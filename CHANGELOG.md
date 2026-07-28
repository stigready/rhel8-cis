# Changelog

Format based on [Keep a Changelog](https://keepachangelog.com/).

## [0.2.2-private-review] - export review

### Added
- Initial StigForge export of matrix role `rhel8_cis`.
- OpenSCAP verify evidence bundles per profile under `compliance/releases/`.

### Verified (CI)

- **`cis-l1`** — score **98.84%** (floor 90.0%) · gate **PASS** · evidence `20260728T094020Z`
  - OpenSCAP failures still counted: `configure_custom_crypto_policy_cis`
- **`cis-l2`** — score **97.78%** (floor 90.0%) · gate **PASS** · evidence `20260728T094233Z`
  - OpenSCAP failures still counted: `configure_custom_crypto_policy_cis, disable_weak_deps`

### Provenance

- Factory pipeline: https://github.com/stigready/stigforge/actions/runs/30348467615
- Factory commit: `49f1c019fbf7ba7f8edc345d79321ed45f9534de`

