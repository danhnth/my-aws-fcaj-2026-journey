---
title : "Step 3: Test & Validation"
date : 2026-06-30
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Step 3: Test & Validation

After deploying the insecure baseline, wait approximately **30-60 minutes** for Security Hub and GuardDuty to complete their initial scan cycles.

**1. Check Security Hub Findings**

1. Navigate to **Security Hub** console → **All findings**.
2. You should see findings flagged in relation to the misconfigurations we created:

   | Finding ID | Description |
   |------------|-------------|
    | **S3.8** | S3 general purpose buckets should block public access |
   | **IAM.1** | IAM policies should not have full administrative privileges |
   | **EC2.19** | Security groups should not allow unrestricted SSH access |

3. Navigate to **Security Hub** → **Posture management** to view the overall **Compliance score**.

   ![Exposure Summary](Screenshots/Exposure-summary.png)<br>
   *Security Hub Exposure Summary showing failed security controls*

   ![Threats Summary](Screenshots/Threats-summary.png)<br>
   *Security Hub Threats Summary*

   ![Security Score](Screenshots/security-score.png)<br>
   *Security Hub CSPM score = Passed / Enabled controls*

{{%expand "AWS CLI Alternative" %}}
```bash
# List all Security Hub findings
aws securityhub get-findings --region ap-southeast-1

# Filter findings for specific controls
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"S3.8","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"IAM.1","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1
aws securityhub get-findings \
    --filters '{"ComplianceSecurityControlId":[{"Value":"EC2.19","Comparison":"EQUALS"}]}' \
    --region ap-southeast-1

# Count failed findings
aws securityhub get-findings \
    --filters '{"ComplianceStatus":[{"Value":"FAILED","Comparison":"EQUALS"}]}' \
    --query 'length(Findings)' \
    --region ap-southeast-1
```
{{%/expand%}}

**2. Check GuardDuty Findings**

Instead of manual simulations (which often fail to trigger reliably), use the **Amazon GuardDuty Tester** in [section 3](#3-deploy-and-run-amazon-guardduty-tester-comprehensive) below. It deploys dedicated test resources and runs real attack simulations that reliably generate GuardDuty findings.

{{%expand "AWS CLI Alternative" %}}
```bash
# List GuardDuty detectors and get the detector ID
aws guardduty list-detectors --region ap-southeast-1

# List all findings (replace <detector-id> with the ID from above)
aws guardduty list-findings --detector-id <detector-id> --region ap-southeast-1

# Get details of specific findings
aws guardduty get-findings --detector-id <detector-id> \
    --finding-ids $(aws guardduty list-findings --detector-id <detector-id> --query FindingIds --output text) \
    --region ap-southeast-1
```
{{%/expand%}}

**3. Deploy and Run Amazon GuardDuty Tester (Comprehensive)**

For a more thorough validation, the repository includes the **Amazon GuardDuty Findings Tester** from AWS Labs at [`amazon-guardduty-tester-master/`](https://github.com/awslabs/amazon-guardduty-tester). This CDK-based tool deploys dedicated test resources (EC2, ECS, EKS, Lambda, S3) and runs real attack simulations to trigger a broad range of GuardDuty findings - far beyond what manual SSH or IAM tests can produce.

> **Note**: Deploy the tester in the same AWS account and region where your insecure baseline is running, or in a separate non-production account to keep findings clearly scoped.

**Prerequisites**
- AWS CLI v2
- npm
- Docker (for CDK asset building)
- Session Manager Plugin ([install guide](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-working-with-install-plugin.html))

**Deploy the tester infrastructure**
```bash
cd amazon-guardduty-tester-master
npm install
cdk bootstrap    # only if this region hasn't been bootstrapped before
cdk deploy
```
Deployment takes approximately 10-15 minutes. It provisions an EC2 instance (the *test driver*), along with supporting resources for S3, ECS, EKS, and Lambda tests.

   ![CDK Bootstrap Result](Screenshots/cdk-bootstrap-result.png)
   *CDK bootstrap output*

   ![CDK Deploy Result](Screenshots/cdk-deploy-result.png)
   *CDK deploy successful output showing all resources created*

**Start an SSM session into the test driver**
```bash
REGION=ap-southeast-1

aws ssm start-session \
  --region $REGION \
  --document-name AWS-StartInteractiveCommand \
  --parameters command="cd /home/ssm-user/py_tester && bash -l" \
  --target $(aws ec2 describe-instances \
    --region $REGION \
    --filters "Name=tag:Name,Values=Driver-GuardDutyTester" \
    --query "Reservations[].Instances[?State.Name=='running'].InstanceId" \
    --output text)
```

**Run the tester to generate findings**

Inside the SSM session, the Python tester dynamically builds and executes bash scripts that simulate attacks. Start with a broad sweep or narrow down by resource or tactic:

```bash
# Run ALL available tests (EC2, S3, IAM, Lambda, EKS, ECS - generates ~50+ finding types)
python3 guardduty_tester.py --all

# Run only EC2 and S3 tests
python3 guardduty_tester.py --ec2 --s3

# Run tests for specific tactics
python3 guardduty_tester.py --tactics recon discovery

# Run a single specific finding test
python3 guardduty_tester.py --finding 'UnauthorizedAccess:EC2/SSHBruteForce'
```

> The tester automatically enables any GuardDuty features required for the selected tests (e.g., EKS Runtime Monitoring, Lambda Protection) and restores the original settings after completion. Enabling these features may start the 30-day GuardDuty free trial.

**Check the generated findings**

Return to the **GuardDuty** console → **Findings** after 5-15 minutes. The `--all` run typically generates findings across categories such as:

| Category | Example Findings |
|----------|-----------------|
| Recon | `Recon:EC2/Portscan`, `Recon:IAMUser/TorIPCaller` |
| Unauthorized Access | `UnauthorizedAccess:EC2/SSHBruteForce`, `UnauthorizedAccess:EC2/RDPBruteForce` |
| Impact | `Impact:EC2/MaliciousDomainRequest.Reputation`, `Impact:EC2/BitcoinDomainRequest.Reputation` |
| CryptoCurrency | `CryptoCurrency:EC2/BitcoinTool.B!DNS` |
| Policy | `Policy:S3/BucketPublicAccessGranted`, `Policy:IAMUser/UnauthorizedAPICall` |
| Trojan | `Trojan:EC2/BlackholeTraffic!DNS`, `Trojan:EC2/DGADomainRequest.C!DNS` |

   ![Generated Findings](Screenshots/generated-findings-result.png)
   *GuardDuty generated findings from the tester*

   ![Generated Findings Detail](Screenshots/generated-findings-result-2.png)
   *GuardDuty findings detail view*

**Clean up the tester resources** when finished:
```bash
cd amazon-guardduty-tester-master
cdk destroy
```

   ![CDK Destroy Result](Screenshots/cdk-destroy-result.png)
   *CDK destroy output cleaning up all tester resources*

This removes all tester-provisioned resources to avoid ongoing costs.
