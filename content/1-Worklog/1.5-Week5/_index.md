---
title: "Week 5 Worklog"
date: 2026-07-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Complete the hardening & remediation phase by verifying all fixes are effective.
* Run re-validation (Step 5): compare post-hardening Security Hub compliance scores against the pre-hardening baseline.
* Execute full clean-up (Step 6): remove all lab resources to avoid ongoing charges.
* Compile the final project documentation, compliance comparison report, and lessons learned.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (13/07) | - Complete hardening & remediation: <br>&emsp; + Verify S3 bucket is fully private (test anonymous access) <br>&emsp; + Verify IAM user has only least-privilege permissions <br>&emsp; + Verify EC2 security group restricts SSH to my IP only <br> - Re-run Security Hub scan and check all three controls transition to PASSED | 13/07/2026 | 13/07/2026 | |
| Tue (14/07) | - Run re-validation (Step 5): <br>&emsp; + Compare post-hardening Security Hub compliance score with pre-hardening baseline <br>&emsp; + Confirm S3.2, IAM.1, EC2.19 findings changed from FAILED to PASSED <br>&emsp; + Verify no new critical GuardDuty alerts are generated from hardened infrastructure <br> - Capture screenshots of the improved compliance score for the final report | 14/07/2026 | 14/07/2026 | <https://docs.aws.amazon.com/securityhub/> |
| Wed (15/07) | - Execute clean-up (Step 6): <br>&emsp; + Delete IAM user `developer-test` and detach/delete policies <br>&emsp; + Terminate EC2 instance `vulnerable-ec2` <br>&emsp; + Delete security group `insecure-sg` <br>&emsp; + Empty and delete S3 bucket `vulnerable-public-data-*` <br>&emsp; + Disable GuardDuty detector <br>&emsp; + Disable Security Hub <br>&emsp; + Delete CloudTrail trail and its S3 logging bucket <br> - Verify complete resource teardown | 15/07/2026 | 15/07/2026 | |
| Thu (16/07) | - Compile the final project report: <br>&emsp; + Write the compliance comparison (pre vs post hardening) <br>&emsp; + Document all remediation actions with CLI commands <br>&emsp; + Organize screenshots of Security Hub findings and GuardDuty alerts <br>&emsp; + Summarize the security lifecycle outcomes | 16/07/2026 | 17/07/2026 | |
| Fri (17/07) | - Write the lessons learned section: <br>&emsp; + Key technical takeaways from the security operations lab <br>&emsp; + Challenges encountered and how they were resolved <br>&emsp; + Future improvements and advanced security scenarios <br> - Review and finalize all documentation | 17/07/2026 | 17/07/2026 | |
| Sat (18/07) | - **Practice:** <br>&emsp; + Verify no remaining resources are incurring charges (AWS Cost Explorer) <br>&emsp; + Submit the final worklog and project documentation <br> - Reflect on the full 5-week workshop journey | 18/07/2026 | 18/07/2026 | |

### Week 5 Achievements:

* Completed the hardening & remediation phase with verified results:
  * **S3**: Confirmed the bucket is fully private — anonymous access attempts returned 403 Forbidden
  * **IAM**: Verified `developer-test` user only has `AmazonS3ReadOnlyAccess` attached; wildcard policy fully removed
  * **EC2**: Confirmed SSH inbound rule restricted to my public IP only; global access (0.0.0.0/0) revoked

* Ran re-validation and confirmed all three Security Hub controls transitioned from FAILED to PASSED:
  * **S3.2** (S3 public access blocked): FAILED → **PASSED** ✅
  * **IAM.1** (No full admin policy): FAILED → **PASSED** ✅
  * **EC2.19** (SSH restricted): FAILED → **PASSED** ✅
  * The overall Security Hub compliance score showed a significant improvement compared to the pre-hardening baseline

* Executed complete clean-up of all lab resources:
  * Deleted IAM user `developer-test` and removed all attached policies
  * Terminated EC2 instance `vulnerable-ec2` and deleted security group `insecure-sg`
  * Emptied and deleted the vulnerable S3 bucket and the CloudTrail logging bucket
  * Disabled GuardDuty detector and Security Hub
  * Deleted the CloudTrail trail (`FCAJ-Central-Trail`)
  * Verified complete resource teardown via AWS Console and Cost Explorer

* Compiled the final project documentation:
  * Pre- and post-hardening compliance comparison report with screenshots
  * Documented all remediation actions with corresponding AWS CLI commands
  * Organized GuardDuty findings by category (Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan)
  * Summarized the complete security lifecycle: Enable → Deploy → Detect → Harden → Re-validate → Clean-up

* Documented key lessons learned:
  * Security services must be enabled **before** deploying workloads to capture the full detection timeline
  * Infrastructure as Code is effective for reproducible infrastructure but requires careful state management
  * The CIS AWS Foundations Benchmark provides a practical framework for assessing and improving cloud security posture
  * GuardDuty's ML-based threat detection can identify attack patterns (SSH brute force, port scanning, crypto mining) that traditional monitoring would miss
  * The Principle of Least Privilege is the single most impactful security control for IAM
  * Automated remediation via Security Hub integration would significantly reduce response time in production environments
