# Changelog

All notable changes to this repository will be documented in this file.

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