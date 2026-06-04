# CLAUDE.md

Operating instructions for Claude Code sessions in this repository.
Last verified: 2026-06-04

## Project Overview

**C&Q .github** — org profile README, default community-health files, and issue/PR templates inherited by every `coyote-and-quill` repo that doesn't override them.
Plain Markdown | no runtime | **public repo** — org profile READMEs only render publicly from a public `.github` repo
Copyright (c) 2026 Glen Lewis. All Rights Reserved.

## Regulatory Scope

Scope: none — org metadata. Auto-merge to `main` permitted on green CI.

## Quick Reference

```bash
gitleaks detect --source . --no-banner    # Secrets scan (same as CI)
```

## Quality Gates

Run before every push: gitleaks clean · templates render correctly (preview the Markdown).
CI runs gitleaks; a PR cannot merge red (enforced by ruleset).

## Workflow Rules

1. **Issue first** — org-level work is tracked in `coyote-and-quill/skills` issues; repo-content changes get an issue there too.
2. **Branch always** — direct pushes to `main` are rejected by ruleset.
3. **PR to merge** — Regulatory Scope: none → green CI auto-merges.
4. **Close explicitly** — `refs #N` only; close with a summary comment as a separate step.
5. **Serial GitHub ops.**
6. **Commit identity** — `glen@coyoteandquill.com` (set per-repo).

## Structure

```
.github/
├── profile/README.md               # Org profile card (public-facing)
├── .github/ISSUE_TEMPLATE/         # feature.md, bug.md — issue-first workflow defaults
├── .github/pull_request_template.md
├── SECURITY.md                     # Private disclosure contact
└── .github/workflows/ci.yml        # gitleaks
```

## Tech Stack

| Category | Technology |
|----------|------------|
| Content | Markdown |
| CI | GitHub Actions (gitleaks) |

## Environment

None.

## MCP & Agent Tooling

None. Skills from coyote-and-quill/skills assumed installed: scoping, closeout.

## Hard Rules — Do NOT

1. **This repo is PUBLIC** — nothing here may reference private repo internals, client names, unreleased product details, or anything not already on the website.
2. Commit any secret — gitleaks runs in CI; push protection is active (public repo). A key has leaked in this org before (org audit 2026-06-04).
3. **If a key ever reaches a commit anyway: ROTATE it immediately; do not just remove it** — git history keeps it forever.
