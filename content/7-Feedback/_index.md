---
title: "Sharing and Feedback"
date: 2026-07-26
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

> Here I share my personal opinions about my experience in the **First Cloud AI Journey (FCAJ)** program, so the FCAJ team can build on what worked and improve what did not.

### Overall Evaluation

**1. Working Environment**
FCAJ runs largely as a self-paced, remote program built around the **AWS Study Group** platform and the cohort community, with a structured learning path at `cloudjourney.awsstudygroup.com`. I found this format genuinely suited to cloud work - I had my own AWS account, my own region (`ap-southeast-1`), and the freedom to break things and fix them without endangering anyone else's environment. The cohort channel was active and questions rarely went unanswered for long. The main trade-off of a remote-first format is that momentum depends heavily on self-discipline: on the weeks where I set my own daily schedule I made steady progress, and on the weeks where I did not, progress became uneven.

**2. Support from Mentor / Team Admin**
The mentoring style was the part of the program I valued most. During orientation in Week 1 the expectations, reporting format, and learning path were laid out clearly, so I never had to guess what "done" looked like. Later, when I shared my blog on EKS Pod Identity Session Policies with the cohort in Week 6, and when my final report was reviewed in Week 8, the feedback I received was specific and actionable rather than a simple approval. I especially appreciated that mentors let me work through problems myself - when my Security Hub findings did not update after remediation, I was pointed towards the evaluation cycle rather than handed the answer, and understanding that 15-30 minute latency myself was far more useful than being told to just wait.

**3. Relevance of Work to Academic Major**
As a Computer Science student, the fit was strong. University gave me the foundations - networking, operating systems, access control theory - and FCAJ turned them into something operational: VPC subnets and route tables instead of abstract topology, IAM policies and least privilege instead of textbook access-control models, and CIS AWS Foundations Benchmark controls instead of general "security best practice". Areas like cloud threat detection, compliance auditing, and managed security services were entirely new to me and are not covered anywhere in my curriculum.

**4. Learning & Skill Development Opportunities**
The learning curve across eight weeks was steep in a good way. I went from creating my first AWS account in Week 1 to running a complete security operations lifecycle - enabling CloudTrail, GuardDuty, AWS Config, and Security Hub; deploying an insecure baseline; detecting the misconfigurations; remediating them; and proving that S3.2, IAM.1, and EC2.19 all moved from FAILED to PASSED. Deploying the **Amazon GuardDuty Tester** via CDK and analysing 50+ finding types across six categories was the single most instructive exercise, because it let me validate detection rather than assume it. The program also pushed skills beyond pure engineering: writing bilingual technical documentation, publishing blogs for a public audience, and attending the two-day **GenAI-powered App-DB Modernization** workshop, which introduced Domain-Driven Design, Event-Driven Architecture, and Amazon Q Developer.

**5. Community & Team Spirit**
The FCAJ cohort culture is open and knowledge-sharing by default. Publishing to AWS Study Group turned what would otherwise have been private notes into something peers could critique, and the feedback I received on my posts genuinely improved them. Attending the workshop at Bitexco Tower alongside other participants - and hearing directly from AWS speakers - made the program feel connected to the wider AWS ecosystem in Vietnam rather than like an isolated online course.

**6. Program Structure & Policies**
The eight-week structure was well-balanced: roughly five weeks of hands-on lab work, one week dedicated to technical writing, one week for an external AWS workshop, and a final week for documentation and handover. Requiring a proposal up front and a worklog every week kept me honest about progress. AWS Free Tier plus clearly documented clean-up steps meant I could work on real infrastructure without cost anxiety, and I finished with no lingering billable resources.

---

### Additional Questions

**What did I find most satisfying?**
Watching all three CIS controls flip from **FAILED** to **PASSED** in Security Hub after my remediation, and being able to prove the change with before-and-after evidence rather than claiming it. Closely behind that: seeing 50+ GuardDuty findings appear from the GuardDuty Tester and realising I could now read attack telemetry that had been meaningless to me eight weeks earlier.

**What should the program improve for future participants?**
- **Cover automated remediation explicitly.** The lab ends at manual hardening. A guided module on **EventBridge + Lambda** auto-remediation driven by Security Hub findings would be the natural next step and reflects how this is actually done in production.
- **Introduce Infrastructure as Code earlier.** Most of the lab is imperative CLI. Providing a CloudFormation or Terraform track alongside it would make environments reproducible and teach a skill every cloud role expects.
- **Warn about evaluation latency up front.** The 15-30 minute Security Hub and GuardDuty scan cycle is not obvious to a beginner and cost me planning time. A single note in the prerequisites would prevent that.
- **More structured checkpoints.** Optional weekly live sync sessions would help remote participants who struggle to self-pace, without removing the flexibility that makes the format work.

**Would I recommend FCAJ to a friend?**
Yes, without hesitation - with one condition. It suits someone willing to drive their own schedule and go beyond the minimum. The program gives you a real AWS account, a real security problem, and real freedom; how much you get out of it is proportional to how much you choose to push past the assigned scope.

---

### Suggestions & Expectations

- **Suggestion:** Add an optional advanced track after the core lab - auto-remediation with EventBridge and Lambda, multi-account Security Hub aggregation, and full-benchmark CIS auditing rather than a three-control subset.
- **Suggestion:** Encourage participants to pair up for peer review of each other's workshops. Reproducing someone else's lab is the fastest way to discover gaps in documentation.
- **Expectation for the future:** I would like to continue with the AWS Study Group community after the internship, keep publishing on cloud security, and work towards the **AWS Certified Security - Specialty** certification building on what I covered here.
- **Other comments:** Thank you to the FCAJ team and mentors for a well-structured program and for consistently choosing to guide rather than to hand over answers. Learning to debug my own environment - instead of being rescued from it - is the habit I am taking away most from these eight weeks.
