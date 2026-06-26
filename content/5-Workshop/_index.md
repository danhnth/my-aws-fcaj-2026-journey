---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# AWS Security Operations & Hardening Lab

## Insecure-by-Design to Managed Remediation

### Overview

This workshop guides you through building a simulated AWS environment containing common security misconfigurations (Insecure Baseline). You will then configure AWS native security services to detect threats, execute hardening steps to remediate findings, and measure the change in compliance score before and after remediation.

The workshop follows a complete security lifecycle:

1. **Enable Security Services** — Activate AWS CloudTrail, Amazon GuardDuty, and AWS Security Hub to establish centralized logging and threat detection.
2. **Deploy Insecure Baseline** — Intentionally create common cloud misconfigurations (public S3 bucket, over-privileged IAM role, exposed EC2 security group).
3. **Test & Validation** — Observe how Security Hub and GuardDuty flag the misconfigurations and generate security findings.
4. **Hardening & Remediation** — Apply the Principle of Least Privilege and fix each vulnerability based on Security Hub recommendations.
5. **Re-validation** — Confirm that findings transition from Failed to Passed and the compliance score improves.
6. **Clean-up** — Remove all lab resources to avoid ongoing charges.

#### Content

1. [Workshop overview](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Architecture diagram](5.3-Architecture/)
4. [Step 1: Enable Security Services](5.4-Step1-Enable-Security/)
5. [Step 2: Deploy Insecure Baseline](5.5-Step2-Deploy-Insecure/)
6. [Step 3: Test & Validation](5.6-Step3-Test-Validation/)
7. [Step 4: Hardening & Remediation](5.7-Step4-Hardening/)
8. [Step 5: Re-validation](5.8-Step5-Revalidation/)
9. [Step 6: Clean-up](5.9-Step6-Cleanup/)
10. [Lessons Learned](5.10-Lessons-Learned/)
