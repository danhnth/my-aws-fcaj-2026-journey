# My AWS FCAJ 2026 Journey

This repository serves as the documentation and worklog for the Cybersecurity/OpSec Hardening project, developed as part of the AWS FCAJ 2026 workshop. The site is built using **Hugo** and the `hugo-theme-learn` theme, providing full English and Vietnamese localization for both project proposals and team worklogs.

## Project Overview

This project explores a hybrid AWS architecture, focusing on the migration and deployment models for modern web applications. It includes:

* **Proposal Documentation**: Detailed architecture planning, including core feature mapping (Auth, Booking, Payment) against Monolith and Serverless deployment models.
* **Team Worklogs**: Weekly progress tracking, meeting minutes, and task distribution across Front-end, Back-end, and AWS Admin tracks.
* **Architecture Diagrams**: Technical visualization of hybrid data flows.

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