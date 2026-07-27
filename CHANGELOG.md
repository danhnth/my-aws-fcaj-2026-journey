# Changelog

All notable changes to this repository will be documented in this file.

## [2026-07-27]

### Added
* **AGENTS.md:** Added project knowledge base documenting the repository structure, conventions, and anti-patterns for consistent development.
* **Workshop Screenshots:** Added 15 screenshots across 3 workshop steps documenting exposure summaries, threat findings, CDK deployment results, IAM policy assignments, EC2 inbound rules, S3 public access blocking, and security score improvements.

### Changed
* **Worklog Weeks 6-8:** Updated all three bilingual pairs with completed tasks, objectives, and achievements for the final weeks of the internship.
* **Blogs 1-3:** Polished content across all three blog posts (bilingual) and refreshed the blog index to reflect current entries.
* **Event Section:** Restructured Event 1 details with comprehensive rewrites in both languages; removed Event 2 (deprecated); updated the event index accordingly.
* **Workshop Steps 1-3:** Updated Step 1 (Enable Security), Step 2 (Deploy Insecure), and Step 3 (Test Validation) with refined deployment instructions and validation results.
* **Workshop Steps 4-6:** Added Step 4 (Hardening), Step 5 (Revalidation), and Step 6 (Cleanup) content with bilingual hardening procedures, post-remediation validation, and cleanup guidance.
* **Self-evaluation & Feedback:** Refreshed both sections with updated reflections and feedback entries.
* **Navigation Cleanup:** Removed outdated lines from the proposal, workshop index, and homepage.

## [2026-06-26]

### Added
* **Worklog Content:** Added comprehensive Vietnamese worklog entries for Week 2 documenting research progress, deployment milestones, and challenges.
* **Site Index Pages:** Updated both English and Vietnamese index pages to reflect the current repository structure and available content sections.
* **Architecture Description (Vietnamese):** Added a new Vietnamese-language architecture description detailing the security detection pipeline in the workshop.

### Changed
* **README Overhaul:** Reorganized the repository README for clarity and completeness — added dedicated sections for blogs, events, self-assessment, and feedback; included AWS CLI version 2 as a prerequisite.
* **Workshop Restructure:** Refactored the entire workshop guide to center on the AWS Security Operations & Hardening Lab narrative — reordered deployment, security service enablement, insecure configuration, testing, hardening, re-validation, and cleanup into a cohesive flow; added a lessons learned section with future development directions; produced a full Vietnamese translation of the revised content.
* **Workshop Cleanup:** Removed outdated S3 on-premises access lab sections (preparation, interface endpoint creation, DNS simulation, and VPC endpoint policies) to streamline the guide.

### Fixed
* **Class Identifier Correction:** Fixed the class code from an incorrect value to `CN23KHM1` in both English and Vietnamese index files.

## [2026-06-25]

### Added
* **Project Initialization:** Set up the base Hugo framework using the localized workshop template.
* **Repository Architecture:** Configured the local workspace structure to support dual English (`en`) and Vietnamese (`vi`) documentation.
* **Changelog Separation:** Created and modularized project documentation by establishing this dedicated tracking file.

### Fixed
* **Hugo Compatibility Patches:** 
  * Updated legacy shortcode tracking in `layouts/shortcodes/ghcontributors.html` from `getJSON` to modern `resources.GetRemote` syntax to prevent build failures.
  * Resolved `config.toml` deprecation warnings by replacing `languageName` fields with up-to-date `label` keys.