# rhel8_cis — Ansible role (rhel8-cis)

**Ansible hardening role** for **RHEL 8** (CIS Benchmark). Suitable for playbooks, Packer/Ansible provisioners, and golden-image pipelines. Search keywords: `ansible`, `ansible-role`, `cis`, `cis-benchmark`, `cis-hardening`, `compliance`, `devsecops`, `hardening`, `infrastructure`, `openscap`, `redhat`, `rhel`, `rhel8`, `security`.

StigForge-exported Ansible role **`rhel8_cis`** · release **`0.3.48`**.
Matrix cell status: **`green`**.

## Install (Ansible Galaxy)

This repository root **is** the Ansible role (Galaxy-style layout). OpenSCAP evidence
lives under `compliance/` and is not loaded when the role runs.

From **Ansible Galaxy** (after import; namespace `stigready`):

```bash
ansible-galaxy role install stigready.rhel8_cis,0.3.48
```

From **GitHub** (public):

```yaml
# requirements.yml
roles:
  - src: https://github.com/stigready/rhel8-cis
    scm: git
    version: v0.3.48   # or an immutable commit SHA
    name: rhel8_cis
```

```bash
ansible-galaxy role install -r requirements.yml -p ./roles
ansible-playbook -i inventory site.yml   # role: rhel8_cis
```

## Verification status (this release)

Scores are OpenSCAP results for this role, recorded by the factory pipeline run cited below.

| Profile | Score | Floor | Gate | Ansible | Evidence tested (UTC) |
|---|---:|---:|---|---|---|

## Exceptions (excluded from the score gate)

These rules are excluded from the OpenSCAP score gate. Most depend on the network or organisation the AMI is deployed into, so the role leaves them to the AMI owner; where the role does enforce a control and only the scanner cannot confirm it, the table says so. Each is tracked in `policy/products/` of [stigforge] and listed in the image's POA&M. The shared cloud policy (`policy/cloud-ami.yml`) strips a further documented set (for example the bootloader password and smartcard rules).

| Rule | Requirement | What this role does | What the AMI owner does |
|---|---|---|---|
| `kernel_module_overlayfs_disabled` | CIS Level 2: Ensure overlayfs kernel module is not available | Does not block the overlay module: no `install overlay /bin/false` in /etc/modprobe.d/overlay.conf. The generated SSG tasks that wrote it are stripped. | Where no container runtime is used, add `install overlay /bin/false` to /etc/modprobe.d/overlay.conf, as the control states. |

Full artifacts per profile: `compliance/releases/0.3.48/<profile>/` (`score.json`, `results.xml`, `arf.xml`, `evidence.json`, `evidence-report.html`, `poam.md`).

## Reports & review

- **[reports/index.html](reports/index.html)** — HTML report index
- **[CHANGELOG.md](CHANGELOG.md)** — release notes and verify summary

## Verify the score (customer)

Re-run OpenSCAP in Docker and compare to this release's evidence:

```bash
make prove RELEASE=0.3.48
```

Or score your own `results.xml`: see **[compliance/README.md](compliance/README.md)**.

## License

- **[LICENSE](LICENSE)** (MIT) — StigForge export packaging
- **[NOTICE](NOTICE)** — ComplianceAsCode / BSD-3-Clause task body attribution

## Catalog

- [https://stigready.com/#stigforge](https://stigready.com/#stigforge)

