# stigready/rhel8-cis

StigForge-exported Ansible role **`rhel8_cis`** · release **`0.2.0-private-review`**.
Matrix cell status: **`green`**.

## Verification status (this release)

Evidence was produced by **docker verify + OpenSCAP** on the factory CI run cited below.

| Profile | Score | Floor | Gate | Ansible | Evidence tested (UTC) |
|---|---:|---:|---|---|---|
| `cis-l1` | **93.02%** ✓ | 90.0% | PASS ✓ | rc 2 | 20260726T140033Z |
| `cis-l2` | **92.22%** ✓ | 90.0% | PASS ✓ | rc 2 | 20260726T140157Z |

Full artifacts per profile: `compliance/releases/0.2.0-private-review/<profile>/` (`score.json`, `results.xml`, `report.html`, `evidence.json`, `evidence-report.html`, `poam.md`).

## Reports & review

- **[REVIEW.md](REVIEW.md)** — linked evidence index for product owner review
- **[reports/index.html](reports/index.html)** — HTML report index
- **[CHANGELOG.md](CHANGELOG.md)** — release notes and verify summary

## License

- **[LICENSE](LICENSE)** (MIT) — StigForge export packaging
- **[NOTICE](NOTICE)** — ComplianceAsCode / BSD-3-Clause task body attribution

## Factory

- Monorepo: [stigready/stigforge](https://github.com/stigready/stigforge) @ `0a8f2cc3730d273b1ab8b1cfde1cd8ff7fe9c111`
- CI run: https://github.com/stigready/stigforge/actions/runs/30277229616
- Catalog: [https://stigready.com/#stigforge](https://stigready.com/#stigforge)

