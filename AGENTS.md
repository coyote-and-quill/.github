# AGENTS.md — C&Q .github

Instructions for any agent working in this repo (Claude Code, Codex, Copilot, Cursor).
Last reviewed: 2026-10-29.
Follows the C&Q agentic SDLC kit v1 (coyote-and-quill/skills templates/agentic-sdlc).

## What you are building

**C&Q .github:** the org profile README, the default community-health files, and the issue and PR templates inherited by every `coyote-and-quill` repo that doesn't override them. Plain Markdown, no runtime. **This is a public repo**: an org profile README only renders publicly from a public `.github` repo. Copyright (c) 2026 Glen Lewis. All Rights Reserved. Regulatory scope: none, org metadata.

```
profile/README.md                   # the org profile card (public-facing)
.github/ISSUE_TEMPLATE/             # feature.md, bug.md: the issue-first defaults
.github/pull_request_template.md
SECURITY.md                         # the private disclosure contact
.github/workflows/ci.yml            # gitleaks
```

## Quality gates

Run every gate in this block before every push; all must be green. Gate checkers such as `cq-tools:run-gates` read this block, so it holds every gate and nothing else. Add or remove a gate here, not in a second list.

```bash
gitleaks detect --source . --no-banner --redact
```

Also preview the templates' Markdown before pushing; a broken template shows in every repo that inherits it.

## Required checks on `main`

`ci` (gitleaks), from `.github/workflows/ci.yml`. A PR cannot merge red. Don't weaken, skip or rename a check to get green. There's no `kit-check` job: this repo is public, and GitHub doesn't let a public repo call the private skills repo's workflow. The weekly kit sweep checks it instead.

## Git workflow

1. **Issue first.** Org-level work, this repo's included, is tracked in `coyote-and-quill/skills` issues.
2. **Branch:** `feat/<n>-…`, `fix/<n>-…`, `chore/<n>-…`, `docs/<n>-…`. Direct pushes to `main` are rejected.
3. **Commits and PRs say `refs coyote-and-quill/skills#N`.** Never `closes`, `fixes` or `resolves`. Issues are closed by hand, with a summary comment.
4. **Open the PR and stop.** Glen reviews, approves and merges it with a merge commit. Never merge, enable auto-merge, approve or review a PR, by any route. Green CI no longer auto-merges (29 Oct 2026, when this repo came onto the kit). Glen's own edits come in the same way: he pushes a branch, and the bot opens the PR for him to approve.
5. **GitHub issue and milestone operations run one at a time,** never in parallel.
6. **Agents work as `cq-agent[bot]`, the org's agent app, never as Glen.** The bot can't push `.github/workflows/`; Glen pushes CI changes.

## Guardrails

1. **This repo is PUBLIC** — nothing here may reference private repo internals, client names, unreleased product details, or anything not already on the website.
2. **Never commit a secret** — gitleaks runs in CI; push protection is active (public repo). A key has leaked in this org before (org audit 2026-06-04).
3. **If a key ever reaches a commit anyway: ROTATE it immediately; do not just remove it** — git history keeps it forever.

## Decision rights

- **You decide:** wording that doesn't change what a template asks for, and how work splits into issues.
- **Glen approves first:** the profile's content, what any template asks for, anything public (this whole repo), every merge, and changes to this file.
