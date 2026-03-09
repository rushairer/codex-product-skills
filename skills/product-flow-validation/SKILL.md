---
name: product-flow-validation
description: Validate end-to-end product meaning across a user flow after UI or interaction changes. Use when Codex needs to verify that entry copy, user choices, runtime state, persistence, recovery, history, and return-entry surfaces still describe the same thing; when checking whether a fix only made screens look consistent or truly made behavior and product semantics line up; or when turning product review findings into a path-based acceptance pass. Often pair with product-ui-consistency-review-core or product-ui-consistency-review-specialized after structural issues have been found.
---

# Product Flow Validation

Validate a product as a user path, not as isolated screens.

Use this skill after major UI consistency work, interaction refactors, persistence changes, or when a product feels "mostly right" but may still contain semantic drift between entry, behavior, and recovery surfaces.

## Core idea

Treat these surfaces as one semantic chain:

1. Entry surface
2. In-flow state
3. Persistence / recovery
4. History / recap
5. Re-entry surface

The question is not only "do these screens look aligned?".

The question is:

`Does the same user choice keep the same meaning all the way through the chain?`

## Pairing with other skills

Use `product-ui-consistency-review-core` first when the main problem is:

- repeated UI blocks drifting apart
- unclear hierarchy across similar pages
- uncertainty about whether a difference is intentional or accidental

Use `product-ui-consistency-review-specialized` first when the product already has stable page families, domain terminology, or repeated in-product flow roles.

Use this skill after those when the main problem becomes:

- a fix looks correct on one screen but may not survive navigation
- user selections may be dropped before the real action happens
- recovery, records, and re-entry may not reflect what the user actually did

Typical sequence:

1. Use `product-ui-consistency-review-core` or `product-ui-consistency-review-specialized` to find structural and semantic drift.
2. Refactor shared structure or state model.
3. Use `product-flow-validation` to walk the real product path and verify the fix actually closes the loop.

## Validation workflow

### 1. Define the path before reviewing

Name the exact user path in one line.

Examples:

- `Home recommendation -> session -> finish -> history -> replay`
- `Mode page custom choice -> session -> background kill -> restore -> home continue`
- `Recommendation library -> session -> pause -> resume -> completion`

Do not review a vague "area". Review a path.

### 2. Mark the canonical user choice

Identify the thing whose meaning must survive the full flow.

Common examples:

- selected preset
- selected mode
- selected duration
- selected session title
- selected sound layers
- current active session

Write it down explicitly before checking files.

### 3. Trace the semantic chain

For the chosen path, inspect each layer in order:

1. Entry copy
2. Navigation payload
3. Real execution surface
4. Persistence model
5. Recovery path
6. History / recap surface
7. Re-entry path

At each layer ask:

- What does the user think they chose here?
- What data actually moves forward?
- Is the same meaning preserved?

### 4. Separate visual correctness from behavioral correctness

A screen can be visually fixed and still be product-wrong.

Flag these cases aggressively:

- the UI says a parameter matters, but runtime ignores it
- a custom choice enters the next screen as a default
- recovery restores time, but not real playback/configuration
- history uses an internal title instead of the user-facing one
- a "continue" entry actually restarts

### 5. Classify the break

Use one of these labels:

- `copy drift`
- `navigation drift`
- `behavior drift`
- `persistence drift`
- `recovery drift`
- `history drift`
- `re-entry drift`

If multiple breaks exist, report the first place the meaning diverges.

### 6. Fix at the narrowest true source

Prefer this order:

1. canonical state/config model
2. navigation payload
3. persistence / recovery model
4. shared display-title or summary resolver
5. individual screen copy

Do not patch five screens if one missing configuration object is the real bug.

## Output format

For each issue, use this structure:

1. `Whether the issue exists`
2. `Why it breaks the user flow`
3. `Where the meaning diverges first`
4. `Most reasonable fix`

Keep findings ordered by severity.

## Generic acceptance checklist

Run this checklist on any product flow:

- Does entry copy match the title/state shown after navigation?
- Does the real execution layer consume the user's choice?
- Is the same choice persisted, not recomputed from defaults?
- Does recovery restore the same meaning, not only a partial state?
- Does history show the same user-facing title/configuration?
- Does replay / continue reuse the same configuration?
- If a control is visible, does it change real behavior?

## Customization points for each project

When adapting this skill to a specific app, define these project-specific mappings:

### A. Entry surfaces

List the real surfaces that start a flow.

Examples:

- home hero
- recommendation library
- mode detail pages
- recap / history replay
- active-session continue

### B. Canonical configuration object

Identify the one object that should carry product meaning through the chain.

Examples:

- `SessionConfiguration`
- `CheckoutIntent`
- `DraftConfiguration`
- `PlaybackContext`

If no such object exists, that is often the first architectural problem to fix.

### C. Persistence surfaces

List where active and completed state live.

Examples:

- local preferences
- database records
- background restore cache
- server session state

### D. User-facing naming rules

Define which title is canonical on user surfaces.

Examples:

- recommendation card title
- resolved display title
- custom preset title

Explicitly separate these from internal identifiers.

## Example project instantiation

For a concrete project, instantiate the method by naming:

- the real entry surfaces
- the canonical configuration object
- the active persistence surface
- the completed persistence surface
- the user-facing naming rule

Example:

- entry surfaces: Home, Flow library, mode pages, continue/replay cards
- canonical object: `SessionConfiguration`
- active persistence: `UserPreferences`
- completed persistence: `SessionRecord`
- user-facing naming: `resolvedDisplayTitle`

Example high-value checks:

- mode-page choices truly entering the runtime surface
- custom layers or presets surviving into runtime, recovery, and history
- active session restore matching both behavior and countdown
- replay / continue cards using real saved configuration instead of defaults

## Relationship To Other Skills

- `product-ui-consistency-review-core`
  - use first for project-agnostic sibling-screen drift
- `product-ui-consistency-review-specialized`
  - use first for domain-specific page-family drift
- `app-rules-architect`
  - use when repeated validation outcomes should become durable product rules

## When to stop

Stop when:

- the chosen path keeps one meaning through all layers
- no visible control is fake
- recovery and recap use the same user-facing title/configuration
- remaining issues are minor copy polish, not semantic breaks
