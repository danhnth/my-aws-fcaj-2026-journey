# AWS Security Operations & Hardening: Insecure-by-Design to Managed Remediation

This repository serves as the official documentation, deployment guides, and workshop materials for the **AWS Security Operations & Hardening Lab**, developed for the AWS FCAJ 2026 program. 

Built using **Hugo** and the `hugo-theme-learn` theme, this documentation site is fully localized in **English and Vietnamese** and acts as both a project showcase and a step-by-step practical workshop guide.

[![README Tiếng Việt](https://img.shields.io/badge/README-Ti%E1%BA%BFng%20Vi%E1%BB%87t-blue)](https://danhnth.github.io/my-aws-fcaj-2026-journey/)
[![Website](https://img.shields.io/website?url=https%3A%2F%2Fdanhnth.github.io%2Fmy-aws-fcaj-2026-journey%2F&label=Website&color=brightgreen)](https://danhnth.github.io/my-aws-fcaj-2026-journey/)

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

The content within this Hugo site maps directly to the FCAJ final report requirements and is organized as follows:

| # | Directory | Description |
|---|-----------|-------------|
| 1 | **Worklog** (`1-Worklog/`) | Comprehensive weekly tracking (Week 1 to Week 8) detailing research, deployment milestones, and challenges overcome. |
| 2 | **Proposal** (`2-Proposal/`) | Project architecture, security threat modeling, risk evaluation, and estimated baseline budget. |
| 3 | **Blogs Posted** (`3-BlogsPosted/`) | Technical blog posts published to the AWS Study Group community, covering topics such as EKS Pod Identity session policies and other AWS security related subjects. |
| 4 | **Events Participated** (`4-EventParticipated/`) | Documentation of events attended (e.g., GenAI-powered App-DB Modernization workshop) with details on date, location, role, and key takeaways. |
| 5 | **Workshop** (`5-Workshop/`) | The core technical project — a complete, bi-lingual, step-by-step lab guide for replicating the build, testing security alerts, and executing the clean-up process. Covers VPC Endpoints, S3 access patterns, and security hardening. |
| 6 | **Self-Assessment** (`6-Self-evaluation/`) | Personal performance reflections across professional knowledge, communication, teamwork, and problem-solving skills with a structured scoring matrix. |
| 7 | **Sharing and Feedback** (`7-Feedback/`) | Programmatic feedback on the internship experience, working environment, mentor support, and suggestions for improvement. |

---

## Prerequisites

* **Hugo v0.126+** (Extended build is highly recommended).
* AWS CLI version 2.

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