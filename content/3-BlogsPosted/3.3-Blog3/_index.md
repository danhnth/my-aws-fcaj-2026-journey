---
title: "Blog 3"
date: 2026-07-22
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Using Amazon GuardDuty Tester to Automate Security Testing

## The Problem

After deploying your AWS infrastructure, how do you know your security monitoring is actually working? Manual checks are slow and easy to miss things. Waiting for a real attack is dangerous. You need a way to **automatically validate** that GuardDuty, Security Hub, and your incident response workflows function correctly.

This is where GuardDuty Tester comes in.

## Deploying the Tool

Deployment is straightforward using the AWS CDK:

```bash
git clone https://github.com/awslabs/amazon-guardduty-tester.git
cd amazon-guardduty-tester/cdk
cdk bootstrap    # one-time setup
cdk deploy       # deploys Lambda functions, IAM roles, test EC2
```

The CDK stack creates the infrastructure needed to simulate attacks - Lambda functions for API-level simulations and optional EC2 instances for network-level scenarios. The whole process takes about 10 minutes.

## Running the Tests

Once deployed, use the Python CLI to run tests:

```bash
# Run all test categories
python3 guardduty_tester.py --all --region us-east-1

# Or run a single category
python3 guardduty_tester.py --test-type Recon --region us-east-1
```

After running, findings appear in GuardDuty within 5-15 minutes. If you have Security Hub enabled, they appear there too alongside your compliance checks.

## How I Used It in My Lab

In my Security Operations Lab, I ran GuardDuty Tester in three phases:

1. **Before hardening** - Established a baseline of 52 findings across all six categories
2. **After applying security fixes** - Re-ran the same tests and saw Critical/High findings drop
3. **As validation** - Confirmed that my fixes (blocking public S3, restricting IAM, locking down SSH) actually changed the detection results

This workflow transformed security validation from a manual one-time effort into an automated, repeatable process.

## Key Takeaway

GuardDuty Tester makes it possible to **automate the validation of your security detection pipeline**. One command runs the full suite, and you get immediate confirmation that your monitoring is working as expected.

**Tags:** `#AWS` `#GuardDuty` `#Automation` `#SecurityTesting` `#CloudSecurity` `#FCAJ` `#AWSStudyGroup`
