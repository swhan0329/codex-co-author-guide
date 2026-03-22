# Codex Co-author Guide (English)

This guide explains how to use [`sample-codex-coauthor`](https://github.com/sigridjineth/sample-codex-coauthor) in a real repository.

The goal is simple:

```text
Co-authored-by: codex <codex@openai.com>
```

should be appended automatically when you create Git commits.

## What this is

This is not a Codex installer.

- Installing Codex app or CLI: one-time user setup
- Enabling the co-author hook: once per local repository clone

Use this when you already work with Codex and want GitHub commits to show Codex as a co-author.

## Basic flow

After cloning a target repository, run:

```bash
bash scripts/setup-codex-attribution.sh
```

Then commit as usual:

```bash
git add .
git commit -m "Fix small bug"
```

Verify:

```bash
git show -s --format=%B HEAD
```

## Why you must run setup again in a new clone

Because the setup script writes to local Git config in `.git/config`.

That means:

- same clone: run once
- new clone: run again
- different machine: run again

## The original sample repo also includes Codex skills

The original sample repo supports two styles.

### 1. Script-based setup

```bash
bash scripts/setup-codex-attribution.sh
```

### 2. Codex skill-based setup

The sample repo includes repo-local Codex skills such as:

- `$install-codex-coauthor-hook`
- `$add-ai-coauthor`
- `$show-ai-attribution-status`

So in the original sample repository, you can either run shell scripts directly or ask Codex to run the workflow through skills.

## Minimal required files

The minimum practical setup is:

- `.githooks/prepare-commit-msg`
- `.gitmessage`
- `scripts/setup-codex-attribution.sh`

The skills are useful, but optional.

## Real example

See the [vehicle_speed_estimation example](../examples/vehicle_speed_estimation.md).
