# Codex Product Skills

Reusable Codex skills for product review, flow validation, and rule architecture.

This repository helps teams turn vague product feedback into repeatable methods that Codex can reuse across projects.

It is built for cases like:

- reviewing sibling screens without hand-wavy feedback
- validating whether a fix only looks right or actually survives the full user flow
- turning repeated UX decisions into durable product rules

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

This repo packages those methods into reusable Codex skills, so teams can apply the same product reasoning in multiple apps.

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

Copy one or more skill folders into your Codex skills directory.

Example:

```bash
mkdir -p ~/.codex/skills
rsync -a skills/product-ui-consistency-review-core/ ~/.codex/skills/product-ui-consistency-review-core/
rsync -a skills/product-flow-validation/ ~/.codex/skills/product-flow-validation/
```

Then restart Codex.

Recommended install sets:

### Minimal starter set

```bash
rsync -a skills/product-ui-consistency-review-core/ ~/.codex/skills/product-ui-consistency-review-core/
rsync -a skills/product-flow-validation/ ~/.codex/skills/product-flow-validation/
```

### Full product set

```bash
rsync -a skills/product-ui-consistency-review-core/ ~/.codex/skills/product-ui-consistency-review-core/
rsync -a skills/product-ui-consistency-review-specialized/ ~/.codex/skills/product-ui-consistency-review-specialized/
rsync -a skills/product-flow-validation/ ~/.codex/skills/product-flow-validation/
rsync -a skills/app-rules-architect/ ~/.codex/skills/app-rules-architect/
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

## New User Guidance

If you are new to this repository:

1. Start with `product-ui-consistency-review-core`.
2. Add `product-flow-validation` once you start fixing state, recovery, or replay issues.
3. Add `product-ui-consistency-review-specialized` only when your product already has stable family-specific language.
4. Add `app-rules-architect` when the same review outcomes keep repeating and should become rules.

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

## License

MIT
