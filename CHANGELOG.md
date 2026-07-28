# Changelog

Format based on [Keep a Changelog](https://keepachangelog.com/).

## [0.2.2-private-review] - 2026-07-28

### Added
- Customer verify path: `make prove`, `compliance/verify.json`, `scripts/score-results.py`.

### Changed
- README and this changelog list current OpenSCAP verify scores (≥90% floor).
- All CIS/STIG profiles apply SSG remediation via `stigforge_profile` task includes.
- Matrix cell `rhel8_cis` marked **green** with passing docker verify evidence.

### Fixed
- CIS/STIG roles no longer point at empty `rules.yml` scaffold (remediation runs in verify).

### Verified (OpenSCAP)

- **`cis-l1`** — score **98.84%** (floor 90.0%) · gate **PASS** · evidence `20260728T094020Z`
  - Remaining counted failures: `configure_custom_crypto_policy_cis`
- **`cis-l2`** — score **97.78%** (floor 90.0%) · gate **PASS** · evidence `20260728T094233Z`
  - Remaining counted failures: `configure_custom_crypto_policy_cis, disable_weak_deps`

### Provenance

- Factory pipeline: https://github.com/stigready/stigforge/actions/runs/30348467615
- Factory commit: `49f1c019fbf7ba7f8edc345d79321ed45f9534de`

## [0.2.1-private-review] - 2026-07-28

### Changed
- Galaxy-style layout: Ansible role at repository root; evidence under `compliance/`.
- Private review tag `v0.2.1-private-review` (supersedes nested `roles/<role>/` export).

## [0.2.0-private-review] - 2026-07-26

### Added
- First private StigForge export to `stigready/*` (factory review; nested role path).
