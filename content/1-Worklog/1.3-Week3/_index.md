---
title: "Week 3 Worklog"
date: 2026-07-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Plan the "Insecure-by-Design" project architecture and define the misconfiguration scenarios.
* Begin provisioning the initial set of intentionally misconfigured AWS resources.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Wed (01/07) | - Design the "Insecure-by-Design" architecture <br> - Identify misconfiguration scenarios to deploy: <br>&emsp; + Public S3 bucket with sensitive data <br>&emsp; + Over-privileged IAM role with wildcard (*) permissions <br>&emsp; + EC2 instance with public SSH access and no restrictions <br> - Define the project directory structure and module layout | 01/07/2026 | 01/07/2026 | |

### Week 3 Achievements:

* Designed the Insecure-by-Design project architecture covering three core misconfiguration scenarios: a public S3 bucket, an over-privileged IAM role, and a publicly accessible EC2 instance.

* Documented the current security posture and confirmed that AWS Trusted Advisor and Security Hub (once enabled) would flag these as critical findings.

* Prepared the groundwork for Week 4, deploying additional vulnerable resources and expanding monitoring coverage.
