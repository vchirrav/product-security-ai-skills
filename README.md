# OWASP Security Skills for AI Agents

This repository provides **36 ready-to-use AI agent skills** covering the full application security toolchain. Each skill teaches AI coding assistants (Claude Code, Cursor, GitHub Copilot) how to run a specific security tool, parse its output, and provide actionable remediation guidance.

Skills are packaged in the [skills.sh](https://skills.sh) format (top-level folders with `SKILL.md`) and as native **Claude Code skills** (`.claude/skills/`).

## Quick Start

**Install all skills:**

```bash
npx skills add vchirrav/owasp-security-skills
```

**Install a specific skill:**

```bash
npx skills add vchirrav/owasp-security-skills@sast-semgrep
```

## Skills Catalog (36)

| Category | Skill Name | Tool | Language / Target |
|----------|-----------|------|-------------------|
| **Secure Coding** | `secure-coding-audit` | OWASP Rules | All (rule-based audit) |
| | `secure-coding-generate` | OWASP Rules | All (secure code gen) |
| **SAST** | `sast-semgrep` | Semgrep | 30+ languages |
| | `sast-bandit` | Bandit | Python |
| | `sast-eslint-security` | ESLint + security plugin | JavaScript / TypeScript |
| | `sast-spotbugs` | SpotBugs + Find Security Bugs | Java |
| | `sast-gosec` | gosec | Go |
| | `sast-flawfinder` | Flawfinder | C / C++ |
| | `sast-brakeman` | Brakeman | Ruby on Rails |
| | `sast-psalm` | Psalm (taint analysis) | PHP |
| | `sast-cargo-audit` | cargo-audit + cargo-geiger | Rust |
| | `sast-detekt` | detekt | Kotlin |
| **SCA** | `sca-osv-scanner` | OSV-Scanner | All ecosystems |
| | `sca-grype` | Grype | All ecosystems + images |
| | `sca-npm-audit` | npm audit | Node.js / npm |
| | `sca-pip-audit` | pip-audit | Python / PyPI |
| **Secret Scanning** | `secret-scan-gitleaks` | Gitleaks | Git repos / files |
| | `secret-scan-trufflehog` | TruffleHog | Git / filesystem / S3 |
| **Container** | `container-scan-trivy` | Trivy | Docker / OCI images |
| | `container-scan-hadolint` | Hadolint | Dockerfiles |
| | `container-scan-dockle` | Dockle | Docker images (CIS) |
| **IaC** | `iac-scan-checkov` | Checkov | Terraform, CFN, K8s, Helm |
| | `iac-scan-tfsec` | tfsec | Terraform (HCL) |
| | `iac-scan-kube-linter` | KubeLinter | Kubernetes / Helm |
| **DAST** | `dast-zap` | OWASP ZAP | Web apps / APIs |
| | `dast-nuclei` | Nuclei | Web / network / cloud |
| **API Security** | `api-security-schemathesis` | Schemathesis | OpenAPI / GraphQL |
| | `api-security-spectral` | Spectral | OpenAPI / AsyncAPI specs |
| **SBOM** | `sbom-syft` | Syft | Images / filesystems |
| **License** | `license-scan-scancode` | ScanCode Toolkit | Source code |
| **Cloud Security** | `cloud-security-prowler` | Prowler | AWS / Azure / GCP |
| | `cloud-security-scoutsuite` | ScoutSuite | AWS / Azure / GCP / Oracle |
| **Mobile** | `mobile-security-mobsf` | MobSF | Android / iOS |
| **Network** | `network-scan-nmap` | Nmap | Hosts / networks |
| **TLS/SSL** | `tls-scan-testssl` | testssl.sh | TLS endpoints |
| **Malware** | `malware-scan-yara` | YARA | Files / binaries |
| **Supply Chain** | `dependency-confusion-detect` | Confused + GuardDog | npm / PyPI / Maven |

## Skill Formats

### skills.sh Skills (top-level folders)

Each top-level folder contains a `SKILL.md` with YAML frontmatter (`name`, `description`) and step-by-step instructions for the AI agent. Compatible with any agent that supports the [skills.sh](https://skills.sh) format.

### Claude Code Skills (`.claude/skills/`)

Two native Claude Code skills are provided:

- **`/secure-coding-audit`** -- Audits existing code against OWASP rules, outputs a findings table with Pass/Fail per rule.
- **`/secure-coding-generate`** -- Generates new secure code with inline Rule ID citations.

## Dependency: OWASP Secure Coding Rules

The `secure-coding-audit` and `secure-coding-generate` skills require the OWASP rule files from the companion repository:

```bash
git clone https://github.com/vchirrav/owasp-secure-coding-md.git
```

Copy (or symlink) the `rules/` folder into your project root so the skills can find them:

```bash
cp -r owasp-secure-coding-md/rules ./rules
```

All other skills (SAST, SCA, DAST, etc.) are self-contained and do not require the rules repository.

## Repository Structure

```
owasp-security-skills/
├── secure-coding-audit/        # Skill: OWASP secure coding audit
├── secure-coding-generate/     # Skill: OWASP secure code generation
├── sast-semgrep/               # Skill: Semgrep multi-language SAST
├── sast-bandit/                # Skill: Bandit Python SAST
├── ...                         # (36 skill folders total)
├── .claude/skills/             # Native Claude Code skills
│   ├── secure-coding-audit/
│   └── secure-coding-generate/
├── CLAUDE.md
└── README.md
```

## Author

**[Viswanath Chirravuri](https://www.linkedin.com/in/vchirrav/)**

## License

Skills reference the following tools and standards. Each tool has its own license:
* OWASP Secure Coding Practices Quick Reference Guide v2.1
* Semgrep, Bandit, ESLint, SpotBugs, gosec, Flawfinder, Brakeman, Psalm, cargo-audit, detekt
* OSV-Scanner, Grype, npm audit, pip-audit
* Gitleaks, TruffleHog
* Trivy, Hadolint, Dockle
* Checkov, tfsec, KubeLinter
* OWASP ZAP, Nuclei
* Schemathesis, Spectral
* Syft, ScanCode
* Prowler, ScoutSuite
* MobSF, Nmap, testssl.sh, YARA, Confused, GuardDog
