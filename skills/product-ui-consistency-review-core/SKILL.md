---
name: product-ui-consistency-review-core
description: Review product screens for structural, semantic, interaction, and visual consistency in a project-agnostic way. Use when Codex needs to compare sibling pages, identify a shared page skeleton, detect whether a difference is intentional or drift, recommend the smallest coherent fix, review repeated blocks or flows across multiple screens, or perform reusable UI consistency reviews across different apps without relying on domain-specific labels or product-specific terminology.
---

# Product UI Consistency Review Core

Review repeated screens as a family, not as isolated pages.

## Work In This Order

1. Confirm whether the screens are the same page family.
2. Define the shared skeleton in one short list.
3. Compare each page against that skeleton.
4. Separate valid differences from product drift.
5. Recommend the smallest coherent fix.

## What To Check

- **Semantic consistency**
  - Do equal-looking blocks mean the same thing?
  - Do similar labels represent the same user job?
  - Are success, progress, and completion states clearly distinguished?

- **Structural consistency**
  - Do sibling pages use the same information order?
  - Is one page missing a required layer?
  - Did one page keep an older layout after others evolved?

- **Interaction consistency**
  - Do similar actions live in similar places?
  - Does one page execute immediately while siblings ask for confirmation?
  - Are save, apply, continue, and review actions clearly separated?

- **Visual consistency**
  - Are repeated sections using the same role and rhythm?
  - Is a difference caused by content needs, or by bypassing a shared pattern?

## Decision Rules

- Treat a difference as valid only if product meaning is preserved.
- Treat it as drift when users must relearn what a repeated block means.
- Prefer restoring the shared skeleton over patching each page separately.
- Prefer one clear primary path over multiple peer-level primary actions.

## Four-Step Reasoning

Use this exact reasoning when possible:

1. Confirm whether the problem really exists.
2. Classify it as semantic, structural, interaction, or visual.
3. Decide whether it is intentional special-casing or implementation drift.
4. Give one most-reasonable fix.

## Comparison Method

Always compare in this order:

1. Are these screens the same family?
2. If yes, what common skeleton should they share?
3. Which screen deviates from that skeleton?
4. Is the deviation about hierarchy, responsibility, action placement, or meaning?

## Shared Skeleton

Express the intended common skeleton briefly.

Example form:

- title/header
- primary content
- secondary details
- primary action
- destructive or low-priority actions

Do not overfit the skeleton to one page’s current implementation.

## Common Drift Patterns

Watch for these cross-project mistakes:

- same-looking cards doing different jobs
- one sibling page missing an empty state
- one sibling page missing a confirmation step
- save and apply actions mixed together
- primary and secondary actions inverted on one page
- one page keeping an outdated structure
- a repeated component being hand-rolled differently
- one screen forcing extra steps to verify success

## Severity Levels

Use these labels:

- `轻微漂移`
  - Meaning is still mostly correct.
  - Usually styling, spacing, or small placement issues.

- `结构冲突`
  - A sibling screen uses a different flow or misses a required layer.

- `语义错误`
  - A label, state, or action claims one thing but means another.

- `共享抽象失效`
  - Drift keeps recurring because no shared interface constrains the page family.

## How To Phrase Findings

Report each finding in this shape:

- `问题是否存在`
- `为什么这是问题`
- `这是故意设计还是遗漏`
- `最合理的修法是什么`

Be direct when the user is correct.

## Fix Strategy

Prefer these fixes in order:

1. restore meaning
2. restore skeleton
3. restore action placement
4. restore visuals

Fix the shared abstraction before patching multiple sibling pages manually.

## When To Escalate

Escalate from local fixes to shared abstractions when:

- three or more sibling pages repeat the same drift
- one page keeps diverging after multiple edits
- future changes should land across a family
- the inconsistency is about product meaning, not just spacing

## Relationship To Other Skills

- `product-flow-validation`
  - use after consistency fixes when the remaining question is whether entry, runtime, persistence, recovery, and replay still keep the same meaning across a user path

## Good Triggers

This skill is especially useful when the user asks:

- “Are these two or three screens inconsistent?”
- “Is this difference intentional or accidental drift?”
- “What common skeleton should these pages share?”
- “How should I fix this without redesigning everything?”
- “Can you review these related screens for consistency?”
