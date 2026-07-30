# Changelog

Format based on [Keep a Changelog](https://keepachangelog.com/).

## [0.2.4] - 2026-07-30

### Changed
- StigForge export refresh for `rhel8_cis` at `0.2.4`.

### Verified (OpenSCAP)

- **`cis-l1`** — score **98.84%** (floor 90.0%) · gate **PASS** · evidence `20260729T223250Z`
  - Remaining counted failures: `configure_custom_crypto_policy_cis`
- **`cis-l2`** — score **97.78%** (floor 90.0%) · gate **PASS** · evidence `20260729T223639Z`
  - Remaining counted failures: `configure_custom_crypto_policy_cis, disable_weak_deps`

### Provenance

- Factory pipeline: https://github.com/stigready/stigforge/actions/runs/30496236357
- Factory commit: `7f7cafc85a392bf2a7eb04f1b979185dbcdf5530`

## [0.2.4-private-review] - 2026-07-29

### Changed
- StigForge export refresh for `rhel8_cis` at `0.2.4-private-review`.

### Verified (OpenSCAP)

- **`cis-l1`** — score **98.84%** (floor 90.0%) · gate **PASS** · evidence `20260729T100240Z`
  - Remaining counted failures: `configure_custom_crypto_policy_cis`
- **`cis-l2`** — score **97.78%** (floor 90.0%) · gate **PASS** · evidence `20260729T100642Z`
  - Remaining counted failures: `configure_custom_crypto_policy_cis, disable_weak_deps`

### Provenance

- Factory pipeline: https://github.com/stigready/stigforge/actions/runs/30440754045
- Factory commit: `c481b47d629f5bc2357a86a933aa6f94f5245fce`

## [0.2.3-private-review] - 2026-07-29

### Changed
- StigForge export refresh for `rhel8_cis` at `0.2.3-private-review`.

### Verified (OpenSCAP)

- **`cis-l1`** — score **93.02%** (floor 90.0%) · gate **PASS** · evidence `20260726T140033Z`
  - Remaining counted failures: `accounts_password_pam_modules_in_authselect_profile, accounts_umask_etc_bashrc, accounts_umask_etc_profile, configure_custom_crypto_policy_cis, no_files_or_dirs_ungroupowned, use_pam_wheel_group_for_su`
- **`cis-l2`** — score **92.22%** (floor 90.0%) · gate **PASS** · evidence `20260726T140157Z`
  - Remaining counted failures: `accounts_password_pam_modules_in_authselect_profile, accounts_umask_etc_bashrc, accounts_umask_etc_profile, configure_custom_crypto_policy_cis, disable_weak_deps, no_files_or_dirs_ungroupowned, use_pam_wheel_group_for_su`

### Provenance

- Factory pipeline: https://github.com/stigready/stigforge/actions/runs/30435216810
- Factory commit: `e8e323a3af3258bee63ebc1a873ba26c0cc12049`

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

- **`cis-l1`** — score **93.02%** (floor 90.0%) · gate **PASS** · evidence `20260726T140033Z`
  - Remaining counted failures: `accounts_password_pam_modules_in_authselect_profile, accounts_umask_etc_bashrc, accounts_umask_etc_profile, configure_custom_crypto_policy_cis, no_files_or_dirs_ungroupowned, use_pam_wheel_group_for_su`
- **`cis-l2`** — score **92.22%** (floor 90.0%) · gate **PASS** · evidence `20260726T140157Z`
  - Remaining counted failures: `accounts_password_pam_modules_in_authselect_profile, accounts_umask_etc_bashrc, accounts_umask_etc_profile, configure_custom_crypto_policy_cis, disable_weak_deps, no_files_or_dirs_ungroupowned, use_pam_wheel_group_for_su`

### Provenance

- Factory pipeline: https://github.com/stigready/stigforge/actions/runs/30353408831
- Factory commit: `5601d6c388051bf9f7636b086d93888a709b8b31`

## [0.2.1-private-review] - 2026-07-28

### Changed
- Galaxy-style layout: Ansible role at repository root; evidence under `compliance/`.
- Private review tag `v0.2.1-private-review` (supersedes nested `roles/<role>/` export).

## [0.2.0-private-review] - 2026-07-26

### Added
- First private StigForge export to `stigready/*` (factory review; nested role path).
