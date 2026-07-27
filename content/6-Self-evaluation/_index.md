---
title: "Self-Assessment"
date: 2026-07-26
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

During my internship at **Amazon Web Services Vietnam Company Limited** — **Workforce Bootcamp: First Cloud AI Journey (FCAJ)** — from **15/06/2026** to **14/08/2026**, I had the opportunity to move from purely academic knowledge of computing into a real cloud engineering workflow, working directly on a live AWS account in the `ap-southeast-1` region.

My main deliverable was the workshop **"AWS Security Operations & Hardening Lab: Insecure-by-Design to Managed Remediation"**. I built an intentionally vulnerable environment (a public S3 bucket, an IAM user carrying a `WildcardFullAccess` policy, and an EC2 instance with SSH open to `0.0.0.0/0`), placed it under continuous monitoring with **CloudTrail**, **GuardDuty**, **AWS Config**, and **Security Hub** running the **CIS AWS Foundations Benchmark v1.4.0**, then remediated it and proved the improvement. All three targeted controls — **S3.2**, **IAM.1**, and **EC2.19** — moved from **FAILED** to **PASSED**. Alongside this, I deployed the **Amazon GuardDuty Tester** through the **AWS CDK** and analysed **50+ generated finding types** across the six GuardDuty categories (Recon, UnauthorizedAccess, Impact, CryptoCurrency, Policy, Trojan).

Beyond the lab, I published technical blog posts on the **AWS Study Group** community covering AWS Security Hub, the Amazon GuardDuty Tester, and Amazon EKS Pod Identity Session Policies; and I attended the two-day AWS **GenAI-powered App–DB Modernization** workshop, which introduced me to Domain-Driven Design, Event-Driven Architecture, and Amazon Q Developer.

Through this process I strengthened my skills in **cloud security operations, IAM least-privilege design, VPC networking, the AWS CLI, infrastructure deployment with CDK, compliance auditing against CIS, and bilingual technical writing**.

In terms of work ethic, I kept a daily worklog for all eight weeks, completed each phase of the project on schedule, verified every change with evidence (CLI output and console screenshots) rather than assumption, and fully cleaned up all billable resources at the end of the lab.

To objectively reflect on my internship period, I would like to evaluate myself based on the following criteria:

| No. | Criteria                            | Description                                                                                      | Good | Fair | Average |
| --- | ----------------------------------- | ------------------------------------------------------------------------------------------------ | ---- | ---- | ------- |
| 1   | **Professional knowledge & skills** | Understanding of the field, applying knowledge in practice, proficiency with tools, work quality | ✅    | ☐    | ☐       |
| 2   | **Ability to learn**                | Ability to absorb new knowledge and learn quickly                                                | ✅    | ☐    | ☐       |
| 3   | **Proactiveness**                   | Taking initiative, seeking out tasks without waiting for instructions                            | ✅    | ☐    | ☐       |
| 4   | **Sense of responsibility**         | Completing tasks on time and ensuring quality                                                    | ✅    | ☐    | ☐       |
| 5   | **Discipline**                      | Adhering to schedules, rules, and work processes                                                 | ☐    | ✅    | ☐       |
| 6   | **Progressive mindset**             | Willingness to receive feedback and improve oneself                                              | ✅    | ☐    | ☐       |
| 7   | **Communication**                   | Presenting ideas and reporting work clearly                                                      | ☐    | ✅    | ☐       |
| 8   | **Teamwork**                        | Working effectively with colleagues and participating in teams                                   | ☐    | ✅    | ☐       |
| 9   | **Professional conduct**            | Respecting colleagues, partners, and the work environment                                        | ✅    | ☐    | ☐       |
| 10  | **Problem-solving skills**          | Identifying problems, proposing solutions, and showing creativity                                | ☐    | ✅    | ☐       |
| 11  | **Contribution to project/team**    | Work effectiveness, innovative ideas, recognition from the team                                  | ☐    | ✅    | ☐       |
| 12  | **Overall**                         | General evaluation of the entire internship period                                               | ✅    | ☐    | ☐       |

### What I Did Well

* **Delivered the full security lifecycle end to end** — Enable → Deploy → Detect → Harden → Re-validate → Clean-up — with measurable results (S3.2, IAM.1, EC2.19 all FAILED → PASSED) rather than stopping at theory.
* **Evidence-driven verification.** For every remediation I re-ran the Security Hub scan, captured the CLI output and console screenshots, and compared the compliance score against the pre-hardening baseline instead of assuming the fix worked.
* **Went beyond the assigned scope.** Deploying the Amazon GuardDuty Tester via CDK and researching EKS Pod Identity Session Policies were self-initiated; neither was required by the original proposal.
* **Documented bilingually.** Every workshop step was written in both English and Vietnamese with parallel Console and CLI instructions, so the lab is reproducible by someone who was not there.
* **Cost discipline.** I tore down every resource at the end of the lab and confirmed via Cost Explorer that nothing was left running.

### Needs Improvement

* **Automation over manual remediation.** All my fixes were applied by hand through the Console and CLI. In a real operations context this does not scale — I should have implemented auto-remediation with **EventBridge + Lambda** driven by Security Hub findings to reduce MTTR.
* **Infrastructure as Code.** I provisioned the lab with imperative CLI commands rather than **CloudFormation** or **Terraform**, which made the environment harder to reproduce reliably and to version-control. I only touched IaC indirectly, through the CDK stack that shipped with the GuardDuty Tester.
* **Breadth of compliance coverage.** I remediated three CIS controls out of a much larger benchmark. A more complete audit — including encryption at rest, logging retention, and root account controls — would have given a truer picture of the account's posture.
* **Time and scope discipline.** I underestimated the 15–30 minute latency of Security Hub and GuardDuty evaluation cycles and had to re-plan parts of Week 4 around it. I need to build verification lag into my schedule instead of discovering it mid-task.
* **Communication and presentation.** My written documentation is stronger than my verbal reporting. I want to become more confident at presenting technical findings live and at explaining security trade-offs to a non-security audience.
* **Deeper problem-solving.** I tended to follow documented remediation paths rather than reasoning independently about *why* a control exists and what an attacker would actually do next. Strengthening threat-modelling thinking is my clearest next step.
