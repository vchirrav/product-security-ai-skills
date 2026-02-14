# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Skills-only repository containing **36 AI agent skills** for application security tooling. Each skill is a standalone Markdown file (`SKILL.md`) that teaches AI coding assistants how to run a specific security tool, parse its output, and provide remediation guidance. No build, test, or lint commands -- pure Markdown.

## Architecture

### skills.sh Skills (top-level folders)

36 top-level folders, each containing a `SKILL.md` with YAML frontmatter:

```yaml
---
name: skill-name
description: What the skill does
---
```

Followed by: when to use, prerequisites, step-by-step instructions, and output format.

Categories: Secure Coding (2), SAST (10), SCA (4), Secret Scanning (2), Container Security (3), IaC Scanning (3), DAST (2), API Security (2), SBOM (1), License (1), Cloud Security (2), Mobile (1), Network (1), TLS (1), Malware (1), Supply Chain (1).

### Claude Code Skills (`.claude/skills/`)

- **`/secure-coding-audit`** -- Audits code against OWASP rules, outputs findings table.
- **`/secure-coding-generate`** -- Generates secure code with inline Rule ID citations.

These two skills require a local `rules/` folder from the companion repo: [owasp-secure-coding-md](https://github.com/vchirrav/owasp-secure-coding-md).

## Conventions for Editing Skills

- Each `SKILL.md` must have YAML frontmatter with `name` and `description`
- Include a "When to use" section explaining the trigger conditions
- Include a "Prerequisites" section listing tool installation requirements
- Provide step-by-step instructions the AI agent should follow
- Define the output format (typically a findings/results table)
- Keep skills self-contained -- each skill should work independently

## Install

```bash
# All skills
npx skills add vchirrav/owasp-security-skills

# Specific skill
npx skills add vchirrav/owasp-security-skills@sast-bandit
```
