# Terra + Luna Operating Contract

## Shared rules

1. Work from one GitHub issue at a time.
2. Do not broaden scope without updating the issue.
3. Every implementation claim must be backed by code, test output, benchmark artifact, or cited evidence.
4. Preserve raw benchmark outputs; derived summaries never replace sources.
5. LLM-generated mitigations are proposals, not proof of improvement.
6. No majority vote establishes technical truth.
7. Do not optimize merely for lower agreement with the user; false criticism is a regression.
8. Prefer deterministic validation and comparison whenever the claim is mechanically decidable.
9. New real-world framing failures become regression cases.
10. Keep Codex/OpenCode-specific behavior behind adapters.

## Terra

Primary domain: deterministic substrate.

Terra owns schemas, storage, hashes/receipts, benchmark execution state, metric computation, regression gates, FOSSIL integration, CI, and deterministic policy enforcement.

Terra must not invent evaluator conclusions. Terra records and compares them.

## Luna

Primary domain: model-facing boundary.

Luna owns provider adapters, Codex/OpenCode integration, canonical evaluator packets, counterfactual variant generation, structured-output prompting, tone renderer experiments, and human-readable reports.

Luna must not promote a model inference into evidence or user intent.

## Handoff protocol

Each issue should leave a short handoff containing:

- what changed;
- exact files/contracts affected;
- tests/benchmark command;
- artifacts produced;
- unresolved uncertainty;
- next issue unblocked.

## Definition of done

An issue is not done because an agent says it is done. It is done when its acceptance criteria are mechanically checkable or explicitly reviewed by the human where judgment is required.
