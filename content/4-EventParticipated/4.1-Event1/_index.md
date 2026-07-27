---
title: "Event 1"
date: 2026-07-27
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Summary Report: "Agentic AI Build Week (AABW)"

### Event Objectives

- Provide a hands-on playground to build **Agentic AI** applications on AWS within a limited timeframe
- Introduce AWS's agentic toolset: Amazon Bedrock AgentCore, Strands Agent, SageMaker
- Sharpen scoping skills, teamwork, and turning ideas into an end-to-end MVP
- Share and critique architectures and operating costs across teams during demo day

### Event Information

- **Event Name:** Agentic AI Build Week (AABW)
- **Date & Time:** July 25, 2026
- **Location:** AWS Event Hall – 26th Floor, Bitexco Tower, District 1, Ho Chi Minh City
- **Role:** Attendee

### Key Highlights

#### Team 3KA — S.H.E.P.H.E.R.D

*Smart Human-flow Evaluation, Prediction, Hazard Detection, Response, and Dispatch*

- **Problem:** operations staff must simultaneously monitor multiple entrances, queues, booths, and crowd flows. Manual monitoring is slow, reactive, hard to scale, and prone to missing incidents.
- **Solution:** analyzes live camera feeds to detect and track people, measure crowd density, estimate queue conditions, identify early signs of congestion, forecast overload pressure, and recommend actions to staff.
- **Technology:** YOLO + ByteTrack, Amazon SageMaker, Amazon Bedrock AgentCore + Strands Agent, a React-based monitoring dashboard.
- **Agentic AI layer:** an *Autonomous Monitor* continuously tracks metrics and proactively raises alerts; an *Operator Copilot* lets staff ask questions in natural language and get concise answers grounded in live data.
- **Challenges the team faced:** keeping the video stream stable, reducing inference latency, maintaining tracking across frames, choosing effective camera placements, controlling costs, and keeping the scope feasible within 24 hours.

#### Team Signal Scout — Early Detection of Corporate Strategy Shifts

- **Value delivered:** early detection of restructuring signals, connecting scattered signals into a clear narrative, analyzing metrics and building scenarios, and supporting *Maintain – Adapt – Accelerate* decisions.
- **Design principles:** every conclusion must be backed by verifiable evidence; analysis must be transparent; humans retain final decision-making authority.
- **Target customers:** corporate strategy teams, risk management, competitive intelligence, and B2B account management.
- **Technology and partners:** AWS (Bedrock, AgentCore, Lambda, DynamoDB, API Gateway, Amplify, Cognito, CloudWatch, etc.), LangFuse, TinyFish, Apify.
- **Cost breakdown:** the team presented a cost breakdown across three scenarios — AWS-only costs of roughly USD 17–130/month, and total cost including third-party services of roughly USD 81 – 94 – 359/month — along with a more cost-optimized architecture option.

#### Team Plan V — SA Professional Native App

- **Problem:** Solution Architects are frequently under tight deadlines and must personally handle the four most time-consuming tasks: extracting requirements, drafting an initial architecture, drawing diagrams, and estimating cloud costs.
- **Solution:** a native AI application that analyzes requirements in both natural-language and structured form; proposes high-level architecture options that are hybrid-cloud aware and comply with company standards; generates Draw.io diagrams using official AWS Architecture Icons; estimates AWS costs for the *ap-southeast-1* region; surfaces recommendations, assumptions, and gaps in the requirements; and refines iteratively through a chat sidebar with per-project custom instructions.
- **Impact:** instead of manually reading BRD/PRD documents line by line, starting from a blank page, hand-writing IaC, and estimating costs by gut feel — teams can now simply upload documents and have a natural conversation to get a Requirements Catalogue within minutes, a draft architecture to critique, auto-generated IaC, and an accompanying cost estimate.

### Key Takeaways

#### Product Mindset

- **Start from a real operational pain point:** all three products originated from a genuinely time-consuming manual task, not from the technology itself.
- **Small scope, fully finished:** one complete feature is far more convincing than a large, unfinished idea.
- **Humans retain decision authority:** AI provides evidence and recommendations, but the user is the one who decides.

#### Technical Architecture

- **Agentic AI on AWS:** how to use Amazon Bedrock AgentCore and Strands Agent to build autonomous agents that proactively alert rather than only respond when asked.
- **Combining multiple layers:** real-time computer vision + object tracking + cloud inference + operational dashboard + agent layer.
- **Costing from day one:** a cost breakdown by service and by min/mid/max scenario is a mandatory part of the design, not an afterthought.
- **Explainability:** an agent must be proactive, explainable, and actionable to be usable in real-world operations.

#### Soft Skills

- **Clear role division:** deciding early who codes, who designs, and who pitches avoids overlap and mid-project disputes.
- **Telling the story in 3 minutes:** rehearsing the demo beforehand is decisive when presenting to the judging panel.
- **Preparing in advance is not cheating:** having a clear goal, a starter template, and ready-to-use accounts frees up time to focus entirely on building.

### Applying to Work

- **Experiment with the agentic pattern:** apply the *autonomous monitor + copilot* model to recurring monitoring tasks instead of a passive dashboard.
- **Standardize cost estimation:** build a cost table by min/mid/max scenario for every proposed architecture.
- **Follow the "evidence-backed" principle:** every AI-generated conclusion must be accompanied by a verifiable source.
- **Speed up documentation and diagramming:** use AI tools to generate draft architectures and diagrams, then have humans review and refine them.
- **Build the scoping habit:** break problems down into an MVP achievable within a short timeframe.

### Event Experience

Attending the **Agentic AI Build Week** was a very different experience compared to typical workshops: instead of listening to presentations, I watched teams go through the entire journey from idea to a working product in just 24 hours. Some standout experiences included:

#### Witnessing the real building process

- Teams shared very candidly about the confusing early stage, the moment an idea "clicked," and the pride of seeing the product actually work — an emotional arc that technical slides can never fully capture.
- Many members started with **no AI background** and were **using AWS for the first time**, showing that the real barrier isn't experience but simply daring to start.

#### Learning from real architecture and real costs

- I got to see the detailed architecture diagrams of three very different products, each solving a distinct class of problem: real-time computer vision, synthesizing corporate signals, and automating the Solution Architect's workflow.
- Signal Scout's per-service AWS cost breakdown is a very practical reference for estimating project costs in the future.

#### Networking and discussions

- The Q&A after each presentation helped clarify the trade-offs in each design: latency vs. accuracy, cost vs. scalability, agent autonomy vs. human control.
- I met many people who share the same interest in Agentic AI, opening up opportunities to keep exchanging ideas after the event.

#### Lessons learned

- **Showing up and getting started is already half the journey** — no need to wait until you feel skilled enough.
- **A small product that works is worth more than a big idea left unfinished.**
- **The people you meet matter more than the prize** — the network and experience outlast the competition results.
- Agentic AI is only truly useful when the agent is **proactive, explainable, and actionable**, while humans still retain the final decision.

#### Some event photos
*Add your event photos here*

> Overall, the event not only provided knowledge about Agentic AI and the AWS ecosystem, but also showed me clearly how an idea gets scoped, built, and presented as a complete product under tight time constraints.
