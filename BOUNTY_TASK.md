# Bounty Objective: M2-01 — Reward engine, loot rolls, duplicates and level
Target: ToguDV/lifespire Issue #10
URL: https://github.com/ToguDV/lifespire/issues/10

## Issue Description
## Context

Rewards must feel like a direct consequence of the chosen node. The values are defined by the SPEC and must live in pure, testable functions.

## Scope

- [ ] Implement the reward table for task, elite, rest, treasure and boss.
- [ ] Apply the effort multiplier: light ×1, medium ×1.5, high ×2.
- [ ] Roll loot for elite, treasure and boss with configurable rarity weights.
- [ ] Convert duplicate loot into gold using a documented balance constant.
- [ ] Apply XP and gold to the profile and record a `RewardEvent`.
- [ ] Derive level as `floor(total XP / 100) + 1`; keep it display-only.
- [ ] Keep all numbers in a small balance/content module rather than scattered UI literals.
- [ ] Make loot rolls deterministic from the provided RNG/seed so tests and replays are stable.

## Acceptance criteria

- [ ] Task XP/gold equal `10 × multiplier`; elite equals `20 × multiplier` plus one loot roll; rest gives 5 XP and 0 gold; treasure gives 15 gold and one loot roll; boss gives `20 × multiplier + 20` XP/gold plus one loot roll.
- [ ] Effort multipliers produce exact integer or documented rounded values.
- [ ] Every roll returns a valid catalog item and rarity.
- [ ] Duplicate items are converted to gold and recorded in the reward event.
- [ ] Level updates only when the XP threshold is crossed.
- [ ] No reward is granted twice for the same node resolution.

## Tests

- [ ] Table-driven tests for every node type and effort combination.
- [ ] Deterministic loot roll tests for common, rare and epic.
- [ ] Duplicate conversion test.
- [ ] Level boundary tests at 0, 99, 100 and 199 XP.

## Dependencies

- Depends on #2, #4, #6.

## References

- https://github.com/ToguDV/lifespire/blob/mvp-0/SPEC.md · §6 Rewards and progression
- https://github.com/ToguDV/lifespire/blob/mvp-0/SPEC.md · §8 Data model

## Instructions for Kuro (Autonomous Solver):
1. Use skills: `systematic-debugging` and `code-review-and-quality`.
2. Inspect the repository structure, locate relevant files, and understand the bug/feature.
3. Apply the minimal, robust fix or implementation.
4. Run any existing test suites or linters in the workspace.
5. Ensure the fix adheres to the project's existing code style.
6. When done, output a summary of files modified and verification results.
