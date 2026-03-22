# Codex Co-author Guide

Practical documentation for using [`sample-codex-coauthor`](https://github.com/sigridjineth/sample-codex-coauthor) to automatically add:

```text
Co-authored-by: codex <codex@openai.com>
```

to Git commits.

This repo separates the documentation from the application repository so the guide can be shared directly in GitHub, LinkedIn, or blog posts.

## What is covered

- what the original sample repo does
- when you actually need it
- script-based setup
- optional Codex skill-based usage
- a real application example using `vehicle_speed_estimation`
- Korean and English docs

## Docs

- [Korean guide](ko/README.md)
- [English guide](en/README.md)
- [vehicle_speed_estimation example](examples/vehicle_speed_estimation.md)

## Source repositories

- Original sample repo: <https://github.com/sigridjineth/sample-codex-coauthor>
- Example target repo: <https://github.com/swhan0329/vehicle_speed_estimation>

## Key point

This is not a Codex installer.

It is a repository-level Git hook pattern. You install Codex app or CLI once for yourself, but you enable the co-author hook once per local clone.
