# Codex Product Skills

Reusable Codex skills, templates, and docs for:

- extracting durable product rules
- reviewing sibling screens for consistency
- separating generic review methods from domain-specific review language

## Why This Repo Exists

Many product teams repeatedly rediscover the same decisions:

- where users should land after success
- how save and apply should differ
- how to review sibling screens without vague feedback
- when a rule belongs to one app versus many apps

This repo packages those workflows into reusable Codex skills and companion templates.

## Included Skills

### `app-rules-architect`
- Turn repeated UX and product decisions into durable rules
- Create or update files such as:
  - `APP_RULES.md`
  - `APP_RULES_TEMPLATE.md`
  - `FEATURE_RULES.md`
  - `PRODUCT_PRINCIPLES.md`

### `product-ui-consistency-review-core`
- Review sibling screens, repeated blocks, and related flows in a project-agnostic way
- Focus on semantic, structural, interaction, and visual consistency
- Best for unfamiliar or general-purpose projects

### `product-ui-consistency-review-specialized`
- Review mature product families using domain-specific terminology and page patterns
- Best when a product already has stable page-family structure and repeated concepts

## Included Templates

- `templates/APP_RULES_TEMPLATE.md`

## Included Docs

- `docs/SKILL_BOUNDARIES.md`
- `docs/RULES_AND_SKILLS_README.md`

## Which Skill Should I Use?

- Need a generic consistency review → `product-ui-consistency-review-core`
- Need a domain-aware consistency review → `product-ui-consistency-review-specialized`
- Need to turn recurring product decisions into reusable rules → `app-rules-architect`

## Repository Structure

```text
skills/
  app-rules-architect/
  product-ui-consistency-review-core/
  product-ui-consistency-review-specialized/
templates/
docs/
```

## Installation

Copy any skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills/<skill-name>
rsync -a skills/<skill-name>/ ~/.codex/skills/<skill-name>/
```

Then restart Codex.

## Example Prompts

### Use `app-rules-architect`

```text
Use app-rules-architect to turn our recent import/apply/save decisions into APP_RULES.md.
```

```text
Use app-rules-architect to decide which of these rules are reusable across projects and which are app-specific.
```

### Use `product-ui-consistency-review-core`

```text
Use product-ui-consistency-review-core to compare the Settings, History, and Favorites screens for structure and interaction consistency.
```

### Use `product-ui-consistency-review-specialized`

```text
Use product-ui-consistency-review-specialized to review whether this screen has drifted from our established product family pattern.
```

## Design Philosophy

- Keep the generic method reusable
- Keep domain-specific language out of the core skill
- Promote recurring decisions into explicit rules
- Prefer small coherent fixes over vague redesign advice

## License

MIT
