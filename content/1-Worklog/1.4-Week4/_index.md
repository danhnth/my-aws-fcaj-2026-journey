---
title: "Week 4 Worklog"
date: 2026-07-18
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Enable AWS security monitoring services (CloudTrail, GuardDuty, Security Hub) to establish a centralized detection pipeline.
* Deploy the intentionally vulnerable baseline infrastructure.
* Run test & validation - observe how Security Hub and GuardDuty detect and flag the misconfigurations.
* Begin the hardening & remediation phase by fixing the most critical findings.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (06/07) | **Enable AWS security monitoring services** <br>&emsp; + Create CloudTrail trail (`FCAJ-Central-Trail`) with multi-region logging <br>&emsp; + Enable Amazon GuardDuty for threat detection <br>&emsp; + Enable AWS Security Hub with CIS AWS Foundations Benchmark v1.4.0 <br>&emsp; + Verify all three services are active and logging | 06/07/2026 | 06/07/2026 | <https://docs.aws.amazon.com/securityhub/> |
| Tue (07/07) | **Deploy the insecure baseline** <br>&emsp; + Create VPC with public subnet <br>&emsp; + Create public S3 bucket with permissive bucket policy <br>&emsp; + Create over-privileged IAM role with wildcard permissions <br>&emsp; + Launch EC2 instance with open SSH access <br>&emsp; + Verify all resources are deployed and misconfigured as intended | 07/07/2026 | 07/07/2026 | |
| Wed (08/07) | **Run test & validation + GuardDuty Tester** *(consolidated)* <br>&emsp; + Review Security Hub findings — S3.2, IAM.1, EC2.19 (scan from Tue completes overnight) <br>&emsp; + Document the pre-hardening compliance score <br>&emsp; + Simulate SSH brute force and suspicious IAM activity to trigger GuardDuty alerts <br>&emsp; + Deploy Amazon GuardDuty Tester via CDK (deploys in background while reviewing) <br>&emsp; + Execute `guardduty_tester.py --all` to generate 50+ finding types <br>&emsp; + Review all generated findings in GuardDuty console | 08/07/2026 | 08/07/2026 | <https://github.com/awslabs/amazon-guardduty-tester> |
| Thu (09/07) | **Hardening & remediation** <br>&emsp; + Fix S3 — block public access on the vulnerable bucket <br>&emsp; + Fix IAM — detach wildcard policy, attach least-privilege policy, enable MFA <br>&emsp; + Fix EC2 — restrict SSH inbound to specific IP only <br>&emsp; + Document each remediation action with before/after evidence | 09/07/2026 | 09/07/2026 | |
| Fri (10/07) | **Verify fixes + wrap-up** <br>&emsp; + Verify all three fixes are applied correctly <br>&emsp; + Re-run Security Hub scan and confirm findings transition to PASSED <br>&emsp; + Capture post-hardening compliance score and compare with baseline <br>&emsp; + Review Week 4 progress and plan Week 5 tasks | 10/07/2026 | 10/07/2026 | |

### Week 4 Achievements:

* Successfully enabled the three core AWS security monitoring services:
  * **AWS CloudTrail**: Created a multi-region trail (`FCAJ-Central-Trail`) logging all management events to an S3 bucket with log file validation enabled.
  * **Amazon GuardDuty**: Activated the threat detection service and verified it began analyzing CloudTrail, VPC Flow Logs, and DNS logs within minutes.
  * **AWS Security Hub**: Enabled with the CIS AWS Foundations Benchmark v1.4.0 standard and confirmed the initial compliance scan was running.

* Deployed the full insecure baseline:
  * Public S3 bucket with permissive bucket policy allowing anonymous read access
  * Over-privileged IAM role (`WildcardFullAccess`) with `Action: "*"` and `Resource: "*"`
  * EC2 instance in a public subnet with SSH (port 22) open to 0.0.0.0/0
  * Verified all resources were correctly misconfigured via the AWS Console and CLI

* Ran comprehensive test & validation:
  * Reviewed Security Hub findings — confirmed S3.2 (public bucket), IAM.1 (wildcard admin), and EC2.19 (unrestricted SSH) were all flagged as **FAILED**
  * Captured the pre-hardening compliance score as a baseline for comparison
  * Simulated SSH brute force and suspicious IAM activity to trigger GuardDuty alerts
  * Deployed the Amazon GuardDuty Tester via CDK and executed `guardduty_tester.py --all`, generating 50+ finding types across Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, and Trojan categories
  * Reviewed and documented all GuardDuty findings in the console

* Executed the hardening & remediation phase:
  * **S3**: Blocked all public access on the vulnerable bucket and reset ACL to private
  * **IAM**: Detached the `WildcardFullAccess` policy from `developer-test`, attached `AmazonS3ReadOnlyAccess` (least-privilege), and enabled MFA
  * **EC2**: Revoked the global SSH inbound rule (0.0.0.0/0) and restricted access to only my public IP address
  * Documented each remediation action with CLI commands and console screenshots

* Captured the pre-hardening Security Hub compliance score as a baseline for comparison in Week 5.