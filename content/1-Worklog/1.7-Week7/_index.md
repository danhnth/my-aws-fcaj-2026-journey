---
title: "Week 7 Worklog"
date: 2026-08-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Attend the Agentic AI Build Week (AABW) — a hackathon on building Agentic AI applications on AWS.
* Learn about Amazon Bedrock AgentCore, Strands Agent, and the agentic AI ecosystem on AWS.
* Understand three real-world agentic AI architectures from team presentations (S.H.E.P.H.E.R.D, Signal Scout, SA Professional Native App).
* Gain insights into product mindset, cost estimation, and scoping for AI applications under tight time constraints.
* Write the AABW event summary report for the FCAJ internship portfolio.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (27/07) | - Research Agentic AI fundamentals on AWS: <br>&emsp; + Amazon Bedrock AgentCore and Strands Agent <br>&emsp; + Agentic patterns: autonomous monitoring, copilot interfaces <br>&emsp; + Review the AABW event agenda and team list | 27/07/2026 | 27/07/2026 | <https://aws.amazon.com/bedrock/agent/> |
| Tue (28/07) | - Attend AABW demo day at Bitexco Tower: <br>&emsp; + Watch team presentations (S.H.E.P.H.E.R.D, Signal Scout, SA Professional Native App) <br>&emsp; + Learn about architecture decisions, trade-offs, and operating costs <br>&emsp; + Network with participants and AWS speakers | 28/07/2026 | 28/07/2026 | <4.1-Event1/> |
| Wed (29/07) | - Analyze the three product architectures in depth: <br>&emsp; + S.H.E.P.H.E.R.D - real-time computer vision + agentic AI for crowd monitoring <br>&emsp; + Signal Scout - early detection of corporate strategy-shift signals <br>&emsp; + SA Professional Native App - AI assistant for Solution Architects <br> - Document key architectural patterns and technology choices | 29/07/2026 | 29/07/2026 | |
| Thu (30/07) | - Consolidate AABW learnings: <br>&emsp; + Write detailed notes on agentic AI patterns (Autonomous Monitor, Operator Copilot) <br>&emsp; + Summarize costing models and design principles shared by teams <br>&emsp; + Document takeaways on product mindset and team collaboration | 30/07/2026 | 30/07/2026 | |
| Fri (31/07) | - Apply AABW insights to Security Operations Lab: <br>&emsp; + Explore how agentic patterns could enhance security monitoring <br>&emsp; + Consider autonomous incident detection and response workflows <br>&emsp; + Evaluate AI-assisted documentation and diagramming for the workshop | 31/07/2026 | 31/07/2026 | <../5-Workshop/> |
| Sat (01/08) | - **Practice:** <br>&emsp; + Write the AABW event summary for the FCAJ internship portfolio <br>&emsp; + Reflect on how agentic AI differs from traditional automation approaches <br> - Review Week 7 progress and plan final documentation for Week 8 | 01/08/2026 | 01/08/2026 | |

### Week 7 Achievements:

* Successfully attended the **Agentic AI Build Week (AABW)** at AWS Event Hall, Bitexco Tower, experiencing how teams build end-to-end Agentic AI applications on AWS within 24 hours.

* Acquired practical knowledge about **Amazon Bedrock AgentCore and Strands Agent** — the core AWS services for building autonomous agents that proactively monitor, analyze, and alert rather than only respond when asked.

* Studied three distinct product architectures in detail:

  * **S.H.E.P.H.E.R.D** — a real-time crowd monitoring system combining YOLO + ByteTrack (computer vision), Amazon SageMaker (cloud inference), and two agentic AI layers: an *Autonomous Monitor* that continuously tracks metrics and proactively raises alerts, and an *Operator Copilot* that lets staff ask questions in natural language grounded in live data.

  * **Signal Scout** — an early detection system for corporate strategy-shift signals, using Amazon Bedrock, Lambda, DynamoDB, API Gateway, and multi-source intelligence aggregation. The team presented a detailed per-service cost breakdown across three scenarios (USD 17-130/month for AWS-only), demonstrating that cost estimation must be part of the design from day one.

  * **SA Professional Native App** — an AI assistant that automates the four most time-consuming tasks for Solution Architects: extracting requirements from BRD/PRD documents, drafting high-level architecture proposals, generating Draw.io diagrams with official AWS Architecture Icons, and estimating AWS costs for the *ap-southeast-1* region.

* Gained insights into **product mindset**: start from a real operational pain point rather than the technology itself, keep scope small and finish completely, and always keep humans in the decision loop with evidence-backed AI recommendations.

* Learned about **effective team collaboration**: clear role division early, rehearsing demos to tell a story in 3 minutes, and preparing starter templates in advance to maximize building time.

* Understood the importance of **cost estimation from day one** — every team presented a per-service cost breakdown by min/mid/max scenario as a mandatory part of their architecture, not an afterthought.

* Wrote the AABW event summary report for the FCAJ internship portfolio, documenting all three product architectures, key takeaways, and how the experience connects to the broader security operations work.
