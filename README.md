# Codex Product Skills

Reusable product-review and product-rules skills for Codex and other AI coding assistants.

This repository helps teams turn vague product feedback into repeatable methods that AI assistants can reuse across projects.

It is built for cases like:

- reviewing sibling screens without hand-wavy feedback
- validating whether a fix only looks right or actually survives the full user flow
- turning repeated UX decisions into durable product rules

## What You Get

If you use this repository well, the practical result is:

- clearer product reviews instead of vague comments like “this feels messy”
- faster detection of semantic drift between entry, runtime, recovery, and history
- reusable prompts and methods you can carry from one app to another
- better collaboration with AI assistants because the review method is explicit
- a path from “we noticed this again” to “this is now a durable product rule”

In short:

This repository helps you get better product decisions out of your AI assistant with less re-explaining every time.

## What This Repository Contains

Current skills:

- `product-ui-consistency-review-core`
  - generic sibling-screen and repeated-block review
- `product-ui-consistency-review-specialized`
  - domain-aware review for mature product families
- `product-flow-validation`
  - end-to-end validation across entry, runtime, persistence, recovery, history, and replay
- `app-rules-architect`
  - extraction and maintenance of durable product rules

Supporting material:

- `templates/APP_RULES_TEMPLATE.md`
- `docs/SKILL_BOUNDARIES.md`
- `docs/RULES_AND_SKILLS_README.md`
- `CONTRIBUTING.md`

## Why This Repo Exists

Many product teams repeatedly rediscover the same decisions:

- what repeated cards should mean
- when similar pages have drifted apart
- whether a user choice actually survives navigation and recovery
- when a decision should become an app rule instead of another one-off fix

This repo packages those methods into reusable skills and promptable workflows, so teams can apply the same product reasoning in multiple apps.

## Skill Map

Use the skills in this order:

1. `product-ui-consistency-review-core`
   - start here for generic or unfamiliar projects
2. `product-ui-consistency-review-specialized`
   - use when the product already has stable domain terminology or page-family structure
3. `product-flow-validation`
   - use after consistency fixes when you need to verify that the same user choice keeps the same meaning through the full flow
4. `app-rules-architect`
   - use when recurring review outcomes should become durable product rules

Short version:

- Need to compare related screens -> `product-ui-consistency-review-core`
- Need to review using product-specific concepts -> `product-ui-consistency-review-specialized`
- Need to validate the whole user path -> `product-flow-validation`
- Need to turn repeated decisions into rules -> `app-rules-architect`

## Repository Structure

```text
skills/
  app-rules-architect/
  product-flow-validation/
  product-ui-consistency-review-core/
  product-ui-consistency-review-specialized/
templates/
docs/
```

## Installation

## Easiest Setup For New Users

If you do not have much terminal experience, follow these steps in order.

### Step 1. Clone this repository

Open Terminal and run:

```bash
git clone git@github.com:rushairer/codex-product-skills.git
```

If SSH is not configured, use:

```bash
git clone https://github.com/rushairer/codex-product-skills.git
```

Then enter the repository:

```bash
cd codex-product-skills
```

### Step 2. Create your Codex skills directory

```bash
mkdir -p ~/.codex/skills
```

### Step 3. Copy the skills you want to use

If you want the safest beginner setup, copy these two first:

```bash
cp -R skills/product-ui-consistency-review-core ~/.codex/skills/
cp -R skills/product-flow-validation ~/.codex/skills/
```

If `cp -R` does not work well in your environment, use:

```bash
rsync -a skills/product-ui-consistency-review-core/ ~/.codex/skills/product-ui-consistency-review-core/
rsync -a skills/product-flow-validation/ ~/.codex/skills/product-flow-validation/
```

### Step 4. Restart Codex

Close Codex and open it again.

### Step 5. Start with one skill only

For most people, the best first move is:

1. install `product-ui-consistency-review-core`
2. install `product-flow-validation`
3. try one real review task

Do not install everything and use everything at once unless you already know why you need each skill.

### For Codex

Once the repository is cloned, copy one or more skill folders into your Codex skills directory.

Example:

```bash
mkdir -p ~/.codex/skills
cp -R skills/product-ui-consistency-review-core ~/.codex/skills/
cp -R skills/product-flow-validation ~/.codex/skills/
```

Then restart Codex.

Recommended install sets:

### Minimal starter set

```bash
cp -R skills/product-ui-consistency-review-core ~/.codex/skills/
cp -R skills/product-flow-validation ~/.codex/skills/
```

### Full product set

```bash
cp -R skills/product-ui-consistency-review-core ~/.codex/skills/
cp -R skills/product-ui-consistency-review-specialized ~/.codex/skills/
cp -R skills/product-flow-validation ~/.codex/skills/
cp -R skills/app-rules-architect ~/.codex/skills/
```

### For other AI coding assistants

If your assistant does not support native Codex skills, you can still use this repository as a structured prompting toolkit.

Recommended setup:

1. Clone this repository locally.
2. Pick the one skill that matches your current job.
3. Open that skill's `SKILL.md`.
4. Ask your assistant to read `README.md` first, then the chosen `SKILL.md`.
5. Tell it to follow that skill as the working method for the rest of the task.

This works well with assistants such as:

- OpenClaw
- Claude Code
- Codebuddy
- other repo-aware coding agents

The key requirement is simple:

The assistant must be able to read local files and follow structured instructions.

## Quick Start For New Users

If you are new to this repository, use this path:

1. Start with `product-ui-consistency-review-core`.
2. Add `product-flow-validation` once you start fixing state, recovery, or replay issues.
3. Add `product-ui-consistency-review-specialized` only when your product already has stable family-specific language.
4. Add `app-rules-architect` when the same review outcomes keep repeating and should become rules.

## Non-Technical User Path

If you are not technical and just want to get started:

1. Clone the repository.
2. Copy `product-ui-consistency-review-core` and `product-flow-validation` into `~/.codex/skills/`.
3. Restart Codex.
4. Open your project.
5. Start with this exact prompt:

```text
Use product-ui-consistency-review-core to review these related screens.
If you find fixes that change entry, runtime, recovery, or history meaning, follow with product-flow-validation.
```

That is enough to get value from this repository without learning every skill first.

## Prompt Templates For Other Assistants

If you are using a non-Codex assistant, copy one of these prompts and adjust the file paths.

### Bootstrap prompt

```text
I want you to use this repository as your working method.

First read:
1. README.md
2. the specific SKILL.md I point you to

Then:
- summarize what that skill is for
- tell me what inputs you need from my project
- use that skill as the operating method for the rest of this task
```

### Generic consistency review prompt

```text
Read:
- README.md
- skills/product-ui-consistency-review-core/SKILL.md

Then use that skill to review these related screens for structural, semantic, interaction, and visual drift.
Report findings in the format required by the skill.
```

### Domain-aware review prompt

```text
Read:
- README.md
- skills/product-ui-consistency-review-specialized/SKILL.md

This product already has established page-family language and repeated card roles.
Use the specialized skill, not the generic one.
```

### End-to-end flow validation prompt

```text
Read:
- README.md
- skills/product-flow-validation/SKILL.md

Validate this user path end-to-end:
[replace with your real flow]

Trace the user choice from entry surface through runtime, persistence, recovery, history, and re-entry.
Tell me where the meaning first diverges.
```

### Rules extraction prompt

```text
Read:
- README.md
- skills/app-rules-architect/SKILL.md

Use that skill to turn the repeated decisions in this project into a durable app-rules document.
Separate reusable principles from app-specific rules.
```

## Quick Start

### 1. Review sibling screens

```text
Use product-ui-consistency-review-core to compare the Settings, History, and Favorites screens for structure and interaction consistency.
```

### 2. Validate the real product flow

```text
Use product-flow-validation to validate this path end-to-end: Home recommendation -> session -> finish -> history -> replay.
```

### 3. Promote repeated decisions into rules

```text
Use app-rules-architect to turn our recent import/apply/save decisions into APP_RULES.md.
```

## How To Teach An AI Assistant This Repo Quickly

Use this checklist when onboarding a new assistant to the repository:

1. Tell it what kind of task you are doing:
   - sibling-screen review
   - end-to-end flow validation
   - rules extraction
2. Point it to `README.md`.
3. Point it to exactly one skill first.
4. Ask it to summarize the skill back to you before doing the work.
5. Only after that give it the actual project files or repo paths.

This reduces the chance that the assistant mixes multiple methods too early.

## Design Philosophy

- Keep the generic method reusable.
- Separate screen-family review from end-to-end flow validation.
- Keep domain-specific language out of core skills unless it materially changes the review.
- Prefer durable methods over one-off critique.
- Turn repeated findings into reusable rules.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

Useful companion docs:

- [docs/SKILL_BOUNDARIES.md](docs/SKILL_BOUNDARIES.md)
- [docs/RULES_AND_SKILLS_README.md](docs/RULES_AND_SKILLS_README.md)
- [docs/USAGE_EXAMPLES.md](docs/USAGE_EXAMPLES.md)

## License

MIT
