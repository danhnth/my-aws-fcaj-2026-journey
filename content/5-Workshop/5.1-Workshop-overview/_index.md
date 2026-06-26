---
title : "Workshop Overview"
date : 2024-01-01 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

#### Workshop Overview

This workshop approaches AWS Cloud through the lens of a **Cloud Security Engineer**. The core objective is to deploy a controlled, intentionally vulnerable cloud environment ("Insecure-by-Design"), monitor it using AWS native security services, and systematically harden it to meet enterprise security benchmarks (such as the CIS AWS Foundations Benchmark).

**Key Phases:**

1. **The Vulnerable Baseline** — Deploy common cloud misconfigurations: public S3 buckets, over-privileged wildcard IAM roles, and exposed EC2 instances with unrestricted SSH access.
2. **Continuous Monitoring & Detection** — Orchestrate a centralized logging and threat detection pipeline using AWS CloudTrail, Amazon GuardDuty, and AWS Security Hub.
3. **Securing & Remediation** — Execute step-by-step hardening to apply the Principle of Least Privilege and remediate each finding.
4. **Audit & Validation** — Compare compliance scores before and after hardening using Security Hub's CIS AWS Foundations Benchmark assessment.

**Learning Outcomes:**

By completing this workshop, you will gain practical experience in:
- Identifying real-world AWS security misconfigurations
- Configuring AWS native security services for centralized monitoring
- Interpreting Security Hub findings and compliance scores
- Applying least-privilege IAM policies and network security controls
- Validating security posture improvements through quantitative metrics