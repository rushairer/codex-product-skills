---
name: product-ui-consistency-review-specialized
description: Review product screens for structural, semantic, and interaction inconsistencies in domain-specific or already-familiar product families. Use when Codex is working in a product that already has repeated page skeletons, stable in-domain terminology, known recurring card roles, or specialized flow patterns, and the review should use those domain concepts instead of a fully generic consistency framework.
---

# Product UI Consistency Review Specialized

Use this skill when the product family already has its own repeated terms, flow structure, and review vocabulary.

## Positioning

This is the specialized version of `product-ui-consistency-review-core`.

- Use `core` when the project is unfamiliar, generic, or cross-domain.
- Use this skill when the product already has recognized page families, repeated card roles, or domain-specific labels that matter to the review.

## Work In This Order

1. Identify the shared product role of each page.
2. Name the intended common skeleton using the project’s own language.
3. Compare each page against that skeleton.
4. Separate true product drift from acceptable specialization.
5. Recommend the smallest coherent fix.

## What This Skill Assumes

This skill is appropriate only when at least one of these is true:

- the product already has stable repeated terminology
- sibling screens belong to an established page family
- the team already reuses certain block names or flow stages
- previous reviews have identified recurring drift patterns in this product type

If those conditions are not true, prefer `product-ui-consistency-review-core`.

## Review Lens

Check the same four categories as the core skill, but interpret them using domain context:

- semantic consistency
- structural consistency
- interaction consistency
- visual consistency

The difference is that this skill should use the product’s own concepts and not flatten them into generic placeholders if those concepts are important to meaning.

## Decision Rules

- Treat differences as valid only if they preserve the product’s intended meaning.
- Treat them as drift when users must relearn what a repeated block or action means.
- Prefer restoring shared domain abstractions over patching individual screens.
- Prefer one clear primary path over multiple peer-level “important” actions.

## Specialized Review Questions

Ask these internally:

- Does this repeated label still mean the same thing in this product family?
- Did one sibling screen keep an outdated version of the family structure?
- Is this a meaningful domain-specific exception, or just local implementation drift?
- Should the fix happen in a shared component, shared rule, or only this page?

## Output Style

Phrase findings in this shape:

- `问题是否存在`
- `为什么这是问题`
- `这是故意设计还是遗漏`
- `最合理的修法是什么`

Be explicit when the issue is real.

## Relationship To Other Skills

- `product-ui-consistency-review-core`
  - use for project-agnostic page reviews
- `product-ui-consistency-review-specialized`
  - use for domain-specific page families
- `product-flow-validation`
  - use after specialized consistency review when the remaining question is whether the product's domain-specific choice survives runtime, recovery, history, and re-entry
- `app-rules-architect`
  - use when the repeated review outcome should become a durable rule

## Good Triggers

Use this skill when the user says things like:

- “These pages in this product family feel inconsistent.”
- “This app already has a known pattern; is this screen drifting?”
- “Review this using our existing product structure.”
- “Check whether this page still matches the established page family.”
