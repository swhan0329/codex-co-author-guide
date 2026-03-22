# Example: `vehicle_speed_estimation`

Repository:
- <https://github.com/swhan0329/vehicle_speed_estimation>

This guide shows the practical flow after cloning `vehicle_speed_estimation`.

The goal is to make future commits automatically include:

```text
Co-authored-by: codex <codex@openai.com>
```

## Who this is for

Follow this example if all of the following are true:

- you cloned `vehicle_speed_estimation`
- you use Codex app or Codex CLI to help with edits
- you still plan to do the normal Git steps yourself

## Step-by-step

### 1. Clone the repository

```bash
git clone https://github.com/swhan0329/vehicle_speed_estimation.git
cd vehicle_speed_estimation
```

### 2. Enable the co-author hook

The repository already contains the required files, so run:

```bash
bash scripts/setup-codex-attribution.sh
```

This writes the following local Git settings:

```bash
core.hooksPath=.githooks
commit.template=.gitmessage
ai.coauthor=codex <codex@openai.com>
```

Important:

- run it once per local clone
- run it again in a new clone

### 3. Open the repository with Codex

Either option works:

- Codex app: open the `vehicle_speed_estimation` folder
- Codex CLI: run `codex` inside the repository

Example prompt:

```text
Find a small improvement in this repository, fix it, and run the tests.
```

### 4. Run tests

Either command works in this repository:

```bash
pytest -q
```

or

```bash
python -m unittest discover -s tests
```

### 5. Commit normally

```bash
git add .
git commit -m "Fix small issue in vehicle_speed_estimation"
```

You do not need to type the co-author trailer yourself.

### 6. Verify the commit body

```bash
git show -s --format=%B HEAD
```

Expected result:

```text
Fix small issue in vehicle_speed_estimation

Co-authored-by: codex <codex@openai.com>
```

### 7. Push the branch

```bash
git push origin <branch-name>
```

### 8. Open a PR and merge on GitHub

From here, the workflow is the normal GitHub flow.

## Common confusion

### Does installing Codex app or CLI make this automatic?

No.

- Codex install/login is user-level setup
- the co-author hook is repository-clone-level setup

### Why must I run setup again in a new clone?

Because the script modifies local Git config in `.git/config`.

That means:

- same clone: run once
- new clone: run again

## Short version

For `vehicle_speed_estimation`, the easiest mental model is:

1. clone the repository
2. run `bash scripts/setup-codex-attribution.sh` once
3. work with Codex
4. run tests
5. commit normally
6. push normally

After that, commits in that clone will automatically include:

```text
Co-authored-by: codex <codex@openai.com>
```
