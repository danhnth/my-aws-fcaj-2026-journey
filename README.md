# AWS Security Operations & Hardening: Insecure-by-Design to Managed Remediation

This repository serves as the official documentation, deployment guides, and workshop materials for the **AWS Security Operations & Hardening Lab**, developed for the AWS FCAJ 2026 program. 

Built using **Hugo** and the `hugo-theme-learn` theme, this documentation site is fully localized in **English and Vietnamese** and acts as both a project showcase and a step-by-step practical workshop guide.

---

## Project Overview

Instead of just spinning up functioning resources, this project approaches AWS Cloud through the lens of a **Cloud Security Engineer**. The core objective is to deploy a controlled, intentionally vulnerable cloud environment ("Insecure-by-Design"), monitor it using AWS native security services, and systematically harden it to meet enterprise security benchmarks (such as the CIS AWS Foundations Benchmark).

### Key Features Covered:
* **The Vulnerable Baseline**: Deploying common cloud misconfigurations (Public S3 Buckets, Over-privileged Wildcard IAM roles, un-MFA'ed users, and exposed EC2 instances).
* **Continuous Monitoring & Detection**: Orchestrating a centralized logging and threat detection pipeline utilizing **AWS CloudTrail**, **Amazon GuardDuty**, and **AWS Security Hub**.
* **Securing & Remediation**: Step-by-step technical execution to harden the infrastructure, applying the *Principle of Least Privilege* and demonstrating automated or manual remediation.
* **Audit & Validation**: Validating compliance posture before and after hardening using Security Hub compliance scores.

---

## Repository & Website Structure

The content within this Hugo site maps directly to the FCAJ final report requirements:
* **Proposal (`/content/proposal/`)**: Project architecture, security threat modeling, risk evaluation, and estimated baseline budget.
* **Workshop Lab Guide (`/content/workshop/`)**: The core technical project. A complete, bi-lingual, step-by-step guide for someone else to replicate the build, test security alerts, and execute the clean-up process.
* **Worklogs (`/content/worklog/`)**: Comprehensive weekly tracking (Week 1 to Week 12) detailing research, deployment milestones, and challenges overcome.
* **Self-Evaluation & Feedback (`/content/evaluation/`)**: Personal performance reflections and programmatic feedback.

---

## Prerequisites

* **Hugo v0.126+** (Extended build is highly recommended).

## Getting Started

### Local Development

To preview the site locally, run the following command from the project root:

```bash
hugo server -D

```

Open `http://localhost:1313` in your browser. The server will live-reload automatically when you make changes to your Markdown files.

### Building for Production

To generate the static site in the `public/` directory:

```bash
hugo

```

---

## Changelog

For a complete history of development updates, technical fixes, and content additions, please refer to the **[CHANGELOG.md](CHANGELOG.md)** file.