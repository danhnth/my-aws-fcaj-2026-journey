---
title: "Week 6 Worklog"
date: 2026-07-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Research and understand AWS Security Hub as a unified cloud security posture management service.
* Explore the Amazon GuardDuty Tester — an open-source tool for simulating real attack scenarios.
* Write and publish technical blogs on AWS Security Hub and the Amazon GuardDuty Tester on the AWS Study Group community.
* Share knowledge with fellow FCAJ cohort members and strengthen technical writing skills.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (20/07) | - Research AWS Security Hub in depth <br>&emsp; + Unified security dashboard and findings aggregation <br>&emsp; + CSPM (Cloud Security Posture Management) against CIS benchmarks <br>&emsp; + Attack path graphs, exposure findings, unused access analysis <br>&emsp; + Integration with GuardDuty, Inspector, Macie | 20/07/2026 | 20/07/2026 | <https://docs.aws.amazon.com/securityhub/latest/userguide/> |
| Tue (21/07) | - Research Amazon GuardDuty Tester <br>&emsp; + CDK-based deployment and test infrastructure <br>&emsp; + Six finding categories: Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan <br>&emsp; + How to validate the detection pipeline with simulated attacks | 21/07/2026 | 21/07/2026 | <https://github.com/awslabs/amazon-guardduty-tester> |
| Wed (22/07) | - Write first drafts of technical blogs <br>&emsp; + Blog 1: Introduction to AWS Security Hub (overview, key features, integrations) <br>&emsp; + Blog 2: Amazon GuardDuty Tester — A New Tool to Test Your Security Detection <br>&emsp; + Blog 3: Using Amazon GuardDuty Tester to Automate Security Testing | 22/07/2026 | 23/07/2026 | |
| Thu (23/07) | - Review and refine blog drafts <br>&emsp; + Verify technical accuracy of all feature descriptions <br>&emsp; + Add screenshots and relevant code snippets <br>&emsp; + Proofread for clarity and correct English | 23/07/2026 | 24/07/2026 | |
| Fri (24/07) | - Final review and publish blogs on AWS Study Group <br>&emsp; + Format posts for the community platform <br>&emsp; + Add tags and categories for discoverability <br>&emsp; + Share the published links with the FCAJ cohort for feedback | 24/07/2026 | 24/07/2026 | <https://awsstudygroup.com/> |
| Sat (25/07) | - **Practice:** <br>&emsp; + Document key technical insights gained during the blog writing process <br>&emsp; + Reflect on how Security Hub and GuardDuty Tester complement each other <br> - Review Week 6 progress and prepare for Week 7 | 25/07/2026 | 25/07/2026 | |

### Week 6 Achievements:

* Gained a thorough understanding of **AWS Security Hub** — a unified cloud security solution that collects, correlates, and enriches security signals from multiple AWS services (GuardDuty, Inspector, Macie, IAM Access Analyzer) into a single-pane-of-glass dashboard.

* Learned key Security Hub features:
  * CSPM (Cloud Security Posture Management) with CIS AWS Foundations Benchmark v1.4.0
  * Attack path graphs that visualize how potential attackers could access and compromise resources
  * Exposure findings that correlate data from multiple services to surface the most actionable risks
  * Unused access analysis with least-privilege policy recommendations
  * OCSF (Open Cybersecurity Schema Framework) for standardized findings

* Researched the **Amazon GuardDuty Tester** — an open-source tool from AWS Labs that deploys Lambda functions via CDK to simulate real attack scenarios and generate actual GuardDuty findings across six categories (Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan).

* Wrote and published **three technical blogs** on the AWS Study Group community:
  * [Blog 1: Introduction to AWS Security Hub](../3-BlogsPosted/3.1-Blog1/) — covering the service's key features, integrations, and role in the Security Operations Lab
  * [Blog 2: Amazon GuardDuty Tester — A New Tool to Test Your AWS Security Detection](../3-BlogsPosted/3.2-Blog2/) — introducing the tool and how it validates the detection pipeline
  * [Blog 3: Using Amazon GuardDuty Tester to Automate Security Testing](../3-BlogsPosted/3.3-Blog3/) — a practical guide to deployment, running tests, and the three-phase validation workflow

* Published the blogs on the AWS Study Group community platform and shared them with the FCAJ cohort, receiving positive feedback from peers and mentors.

* Strengthened technical writing skills — learned to explain complex AWS security concepts in an accessible way for the cloud community, and practiced documenting bilingual content for a broader audience.
