# Contributing

Thanks for considering a contribution. This is published as a personal/template framework, but improvements that benefit forkers are welcome.

## Ways to contribute

- **Report a gap or inconsistency.** Open an issue if you find a rule that is contradictory, ambiguous, or missing a use case.
- **Suggest a new rule, principle, or operational standard.** PRs welcome with a clear motivation and the rule expressed in operational form (see drafting style below).
- **Share a fork variant.** If you have adapted this for a specific team or organizational context, link to your fork in an issue. Useful as a reference for others doing the same.
- **Improve install methods.** Better instructions for distributing across Claude products, third-party agents, or new platforms are valuable.
- **Surface platform-specific issues.** If a Claude product or third-party agent integration has changed and the install instructions are now wrong, open an issue or PR.

## Drafting style

This document is written **operational first, human-readable second**. Each principle, rule, or bullet should be something an AI agent can self-check against its own behavior. This is not negotiable for additions:

- Prefer concrete behavioral statements ("State conclusions directly; acknowledge limits plainly") over aesthetic descriptors ("Confident without arrogance").
- Each rule must pass: *"Could an agent reading this self-check whether it is following it?"*
- Colloquial framings (like "don't be a jerk") are fine as anchoring metaphors but must be paired with concrete behaviors that make them actionable.
- Personality and readability matter. Don't strip them — but never trade actionability for tone.

## Submission process

1. **Open an issue first** to discuss substantive changes (new rules, structural changes, new sections). Quick fixes (typos, wording clarifications) can go straight to a PR.
2. **PRs should:**
   - State whether the change is **material** (changes what is required of the agent) or **clarification** (does not change requirements). See section 8.2 of the canonical document.
   - Update both `AI_CODE_OF_CONDUCT.md` (canonical) and `AI_CODE_OF_CONDUCT_OPERATIVE.md` (operative) — they must stay synchronized.
   - Update `CHANGELOG.md` with a date-based entry describing what changed and why.
   - Preserve the placeholder convention (`<Your Name>`, `<your federal/national jurisdiction>`, etc.) so the document remains a template.
3. **Material changes** to the canonical or operative will be reviewed against the drafting style above and the existing structure (hard rules vs. principles, authorizable vs. absolute, tier definitions).

## What is out of scope

- **Personal customizations.** This repository is the template; your fork is where personal changes live. Do not submit changes that hardcode specific people, jurisdictions, or organizational policies.
- **Removing operational language for stylistic reasons.** Personality is welcome; trading actionability for tone is not.
- **Loosening hard rule precedence.** Section 4.5 (applicable law) and 4.6 (no physical harm) are absolute and not overridable. PRs that propose making either authorizable will not be accepted.

## Questions

Open an issue for anything unclear about how to contribute, or about the framework itself.
