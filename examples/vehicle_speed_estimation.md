# Example: `vehicle_speed_estimation`

Repository:
- <https://github.com/swhan0329/vehicle_speed_estimation>

This is a real example of applying the `sample-codex-coauthor` pattern to an existing repository.

## What was kept

The practical setup was reduced to the minimum required files:

- `.githooks/prepare-commit-msg`
- `.gitmessage`
- `scripts/setup-codex-attribution.sh`

## What was removed

The original sample repo also contained repo-local Codex skill files under `.agents/skills`.

Those were removed in the real application repository because they were not required for the core Git hook workflow.

## Why this example matters

It shows the difference between:

- the original sample repository, which demonstrates both script-based and skill-based usage
- a production repository, where you may prefer the smallest possible footprint

## Actual tested flow

The following was tested directly:

1. make a small code change in `vehicle_speed_estimation`
2. run tests successfully
3. enable Codex co-author attribution
4. create a commit
5. confirm that the commit body includes:

```text
Co-authored-by: codex <codex@openai.com>
```

6. push the branch to GitHub

## Practical takeaway

For documentation:

- explain the original sample repo with both scripts and skills
- explain the real-world application repo with the minimal setup

That gives readers both the full feature picture and the simplest path to adoption.
