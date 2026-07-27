---
title: "Blog 2"
date: 2026-07-22
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Amazon GuardDuty Tester - A New Tool to Test Your AWS Security Detection

## What is Amazon GuardDuty Tester?

**Amazon GuardDuty Tester** is an open-source tool from AWS Labs that simulates real attack scenarios in your AWS account. It generates actual GuardDuty findings so you can verify that your threat detection pipeline is working properly.

Instead of waiting for a real security incident to test your detection, you can run this tool and see findings appear in GuardDuty and Security Hub within minutes.

## Why I Used It

In my Security Operations Lab, I had enabled GuardDuty, CloudTrail, and Security Hub - but I had no way to confirm they were actually detecting threats. Vulnerable resources like a public S3 bucket don't trigger alerts just by sitting there. I needed to simulate an attacker interacting with them, and GuardDuty Tester does exactly that.

## How It Works

The tool deploys Lambda functions via AWS CDK that perform simulated malicious activities - port scanning, credential abuse, crypto mining DNS queries, and more. GuardDuty's ML models analyze these activities and generate findings across six categories:

- **Recon** - Port scanning, DNS probing, API enumeration
- **UnauthorizedAccess** - Credential abuse, SSH brute force
- **Impact** - Resource deletion, EC2 termination
- **CryptoCurrency** - Mining pool DNS queries
- **Policy** - IAM policy violations, S3 public access bypass
- **Trojan** - C2 communication, reverse shell attempts

Running `guardduty_tester.py --all` generated over 50 findings in about 15 minutes - a complete validation of my detection setup.

## Key Takeaway

GuardDuty Tester turns a passive monitoring setup into an actively validated detection pipeline. You stop *hoping* your security services work and start *knowing* they do.

**Tags:** `#AWS` `#GuardDuty` `#SecurityTesting` `#CloudSecurity` `#FCAJ` `#AWSStudyGroup`
