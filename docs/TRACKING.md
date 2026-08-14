# Project Tracking Map

This file is the canonical fallback map for milestone and child-task tracking.

The connected GitHub API currently allows issue creation/update but does not expose native milestone creation or native sub-issue relationship creation. Until those links are created manually in the GitHub UI, milestone parent issues plus task-list links are the source of truth.

## M0 — Reproducible seed benchmark

Parent: #1

- [ ] #2 — Terra: benchmark schemas and immutable run receipts
- [ ] #3 — Luna: framing variants and provider contract
- [ ] #4 — Terra: mechanical comparator and baseline metrics
- [ ] #5 — Luna: port original experiment into seed fixtures

## M1 — Grow to N≈100 distinct benchmark cases

Parent: #6

- [ ] #7 — Luna: 100-case matrix and taxonomy
- [ ] #8 — Luna: counterfactual generator + equivalence checks
- [ ] #9 — Terra: repeated runs, held-out split, variance analysis
- [ ] #10 — Terra: mitigation promotion/regression gates

## M2 — Shared middleware + Codex/OpenCode adapters

Parent: #11

- [ ] #12 — Terra: shared local core service + CLI/MCP
- [ ] #13 — Luna: Codex adapter
- [ ] #14 — Luna: OpenCode plugin adapter
- [ ] #15 — Terra: observer/shadow/warning state machine

## M3 — Framing firewall + FOSSIL engineering flywheel

Parent: #16

- [ ] #17 — Luna: semantic/framing extractor + canonical packet
- [ ] #18 — Terra: deterministic authority policy + quarantine
- [ ] #19 — Terra: canonical retrieval/embedding boundary
- [ ] #20 — Terra+Luna: FOSSIL lineage + regression flywheel

## M4 — Tone/influence safety benchmark

Parent: #21

- [ ] #22 — Luna: controlled tone renderer
- [ ] #23 — Terra: tone-output invariance/drift checks
- [ ] #24 — Luna: human-study protocol

## Suggested native milestones to create later

If/when native milestones are created in GitHub, use exactly:

1. `M0 — Reproducible seed benchmark`
2. `M1 — N≈100 framing benchmark`
3. `M2 — Codex/OpenCode shared middleware`
4. `M3 — Framing firewall + FOSSIL flywheel`
5. `M4 — Tone/influence safety benchmark`

Then assign each parent/child issue to the matching milestone and, if desired, convert the task-list relationships into native GitHub sub-issues without changing issue numbers.

## Execution order

Start with #2 and #3 in parallel. #4 depends on #2. #5 depends on #2 and #3. M1 should not begin at scale until M0 can reproduce a full matched run and mechanical comparison.
