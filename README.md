# rhel8_cis — Ansible role (rhel8-cis)

**Ansible hardening role** for **RHEL 8**, generated from the CIS Red Hat Enterprise Linux 8 Benchmark profiles in ComplianceAsCode SSG 0.1.82. Suitable for playbooks, Packer/Ansible provisioners, and golden-image pipelines. Search keywords: `ansible`, `ansible-role`, `cis`, `cis-benchmark`, `cis-hardening`, `compliance`, `devsecops`, `hardening`, `infrastructure`, `openscap`, `redhat`, `rhel`, `rhel8`, `security`.

StigForge-exported Ansible role **`rhel8_cis`** · release **`0.3.51`**.
Matrix cell status: **`green`**.

## Before you run this role

Each default below changes how a running host behaves. Read them before you apply the role to a host you depend on.

### The role removes the web server packages httpd and nginx

_Requirement: ComplianceAsCode rules `package_httpd_removed` and `package_nginx_removed`, selected by the CIS profile for this product._

**What the role does.** Removes the httpd and nginx packages if they are installed. Their configuration is removed or orphaned with them, depending on the package.

**Who is affected.** A host that serves web traffic, or runs an application that embeds either server as a package dependency. The services stop at the first run and do not come back at reboot.

**How to change it.** Before the first run, set `rhel8cis_package_httpd_removed: false` to keep httpd, or `rhel8cis_package_nginx_removed: false` to keep nginx. The role then leaves that package alone. It does not report on the rule; only an OpenSCAP scan does (see Effect on compliance). If the role has already run, reinstall the package with the system package manager.

**Effect on compliance.** With a variable set to false, the role no longer remediates that CIS rule, and an OpenSCAP scan reports it as failing.

### The role removes the rsync daemon (rsync-daemon)

_Requirement: ComplianceAsCode rule `package_rsync_removed`, selected by the CIS profile for this product._

**What the role does.** Removes the rsync-daemon package (the rsyncd service) if it is installed. The rsync client stays.

**Who is affected.** A host that runs rsyncd to serve files to other hosts.

**How to change it.** Before the first run, set `rhel8cis_package_rsync_removed: false` to keep rsync-daemon. The role then leaves it alone. It does not report on the rule; only an OpenSCAP scan does (see Effect on compliance). If the role has already run, reinstall the package with the system package manager.

**Effect on compliance.** With the variable set to false, the role no longer remediates that CIS rule, and an OpenSCAP scan reports it as failing.

### The role removes the GNOME display manager (gdm)

_Profiles: cis-l2. Requirement: ComplianceAsCode rule `package_gdm_removed`, selected by the CIS Level 2 profile for this product._

**What the role does.** Removes the gdm package if it is installed. Only the cis-l2 profile does this; the default profile (cis-l1) and the workstation profiles leave gdm installed.

**Who is affected.** A host used as a graphical desktop or a remote desktop session host. After the removal there is no graphical login on the console.

**How to change it.** Before the first run with `stigforge_profile: cis-l2`, set `rhel8cis_package_gdm_removed: false` to keep gdm. The role then leaves it alone. It does not report on the rule; only an OpenSCAP scan does (see Effect on compliance). If the role has already run, reinstall the package with the system package manager.

**Effect on compliance.** With the variable set to false, the role no longer remediates that CIS rule, and an OpenSCAP scan reports it as failing.

## Prefer a ready-made image?

StigReady Applied AMIs for AWS are built with a pinned release of this role, scored with OpenSCAP in the
build, and come with a per-version evidence bundle on request. See [https://stigready.com/applied/](https://stigready.com/applied/).

## Install

This repository root **is** the Ansible role (Galaxy-style layout). Release metadata and the
scoring helper live under `compliance/` and are not loaded when the role runs.

From **GitHub** (public):

```yaml
# requirements.yml
roles:
  - src: https://github.com/stigready/rhel8-cis
    scm: git
    version: v0.3.51   # or an immutable commit SHA
    name: rhel8_cis
```

```bash
ansible-galaxy role install -r requirements.yml -p ./roles
ansible-playbook -i inventory site.yml   # role: rhel8_cis
```

## Verification status (this release)

This release carries no per-role OpenSCAP score, and no OpenSCAP results ship with it. A container
cannot evaluate most hardening rules, so the role is not scored here. To score a host you hardened
with it, see *Score it yourself*. `compliance/releases/0.3.51/manifest.json` records this.

## Exceptions (excluded from the score gate)

These rules are excluded from the OpenSCAP score gate. Most depend on the network or organization the AMI is deployed into, so the role leaves them to the AMI owner; where the role does enforce a control and only the scanner cannot confirm it, the table says so. Each is tracked in the StigForge policy for this role and listed in the image's POA&M. The shared cloud policy strips a further documented set (for example the bootloader password and smartcard rules).

| Rule | Requirement | What this role does | What the AMI owner does |
|---|---|---|---|
| `kernel_module_overlayfs_disabled` | CIS Level 2: Ensure overlayfs kernel module is not available | Does not block the overlay module: no `install overlay /bin/false` in /etc/modprobe.d/overlay.conf. The generated SSG tasks that wrote it are stripped. | Where no container runtime is used, add `install overlay /bin/false` to /etc/modprobe.d/overlay.conf, as the control states. |

## Reports & review

- **[reports/index.html](reports/index.html)** — HTML report index
- **[CHANGELOG.md](CHANGELOG.md)** — release notes

## Score it yourself

This repository ships no OpenSCAP results (see *Verification status*). To score a host you
hardened with this role, run `oscap xccdf eval` on it and score the `results.xml` with this role's
exception list: see **[compliance/README.md](compliance/README.md)**.

## Notices

StigForge and StigReady are independent. They are not affiliated with, endorsed by or certified by the Center for Internet Security, Inc. (CIS), the Defense Information Systems Agency (DISA), the U.S. Department of Defense, NIST, Red Hat or the ComplianceAsCode project. "CIS" and "CIS Benchmarks" are trademarks of the Center for Internet Security, Inc. DISA STIGs are DISA publications. Red Hat and Red Hat Enterprise Linux are trademarks or registered trademarks of Red Hat, Inc. or its subsidiaries in the United States and other countries. Linux is the registered trademark of Linus Torvalds in the U.S. and other countries. All trademarks are the property of their respective owners. This role applies ComplianceAsCode (SSG 0.1.82) remediation from SSG's CIS Red Hat Enterprise Linux 8 Benchmark profiles. An OpenSCAP score is a measurement, not a certification.

## License

Copyright (c) 2026 StigReady.

- **[LICENSE](LICENSE)** (MIT) — StigForge export packaging
- **[NOTICE](NOTICE)** — ComplianceAsCode / BSD-3-Clause task body attribution

## Catalog

- [https://stigready.com/#stigforge](https://stigready.com/#stigforge)

