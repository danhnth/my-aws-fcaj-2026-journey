# Changelog

All notable changes to this repository will be documented in this file.

## [2026-06-25]

### Added
* **Project Initialization:** Set up the base Hugo framework using the localized workshop template.
* **Repository Architecture:** Configured the local workspace structure to support dual English (`en`) and Vietnamese (`vi`) documentation.
* **Changelog Separation:** Created and modularized project documentation by establishing this dedicated tracking file.

### Fixed
* **Hugo Compatibility Patches:** 
  * Updated legacy shortcode tracking in `layouts/shortcodes/ghcontributors.html` from `getJSON` to modern `resources.GetRemote` syntax to prevent build failures.
  * Resolved `config.toml` deprecation warnings by replacing `languageName` fields with up-to-date `label` keys.