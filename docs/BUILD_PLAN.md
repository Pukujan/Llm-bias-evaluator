# Build Plan — Terra + Luna

## Working model

Terra and Luna build one shared core through issue-scoped increments. Every increment must leave behind a reproducible artifact, test, benchmark result, or documented decision.

### Terra responsibilities

- deterministic core and policy engine;
- schemas and validation;
- benchmark case/run persistence;
- comparator and metrics;
- FOSSIL event/provenance integration;
- reproducibility, hashing, retries, receipts;
- CI and regression gates.

### Luna responsibilities

- Codex adapter;
- OpenCode adapter;
- model/provider abstraction;
- counterfactual variant generator;
- evaluator prompts and structured-output contracts;
- tone/influence experiments;
- analysis/report generation.

## Milestone sequence

### M0 — Reproducible seed benchmark

Goal: turn the original framing experiment into a deterministic, rerunnable benchmark harness.

Exit criteria:

- case/variant/run/result schemas exist;
- at least 5 seed technical cases are represented;
- anonymous, ownership, expressed-belief, authority, positive-frame, negative-frame variants are supported;
- repeated runs are stored with model/prompt/version hashes;
- mechanical comparison produces baseline metrics;
- one command reproduces the seed benchmark.

### M1 — N≈100 benchmark

Goal: reach roughly 100 distinct underlying technical cases with matched counterfactual variants.

Exit criteria:

- >=100 distinct cases, not merely 100 repeats;
- case families cover clean/simple systems, planted faults, ambiguous architecture judgments, evidence-heavy questions, and coding/review tasks;
- per-condition repetitions estimate run variance;
- metrics include recommendation flips, claim flips, confidence/risk/evidence shifts, false criticism, unsupported agreement, and fatal-fault recall;
- held-out regression set exists.

### M2 — Shared middleware + Codex/OpenCode adapters

Goal: run the same neutrality/eval core behind both agent surfaces.

Exit criteria:

- shared local API/MCP/CLI contract;
- Codex integration can invoke benchmark/evaluation tools;
- OpenCode integration uses the same core and may use deeper hooks only as an adapter optimization;
- observer and shadow modes work end-to-end;
- raw artifacts and canonical evaluator packets are distinguishable and auditable.

### M3 — Framing firewall + FOSSIL flywheel

Goal: turn benchmark failures into durable, traceable engineering inputs.

Exit criteria:

- semantic/framing extraction is provenance-bearing;
- deterministic authority policy quarantines irrelevant social cues;
- canonical semantic query is used for technical retrieval benchmarks;
- FOSSIL stores benchmark lineage, claims, evidence, mitigation versions, and regressions;
- mitigation candidates are tested in shadow mode before promotion;
- no LLM may self-approve a mitigation.

### M4 — Influence/tone safety research

Goal: separate human→AI framing sensitivity from AI→human presentation influence.

Exit criteria:

- identical structured conclusions can be rendered in controlled tone conditions;
- tone conditions do not alter structured epistemic content;
- human-study protocol is specified separately from automated benchmark claims;
- no claim of “complete neutrality” or “manipulation solved” without evidence.

## Engineering flywheel

```text
benchmark
  -> find instability
  -> cluster failure
  -> formulate mitigation
  -> shadow implementation
  -> rerun full + held-out benchmark
  -> reject or promote by predeclared thresholds
  -> convert newly observed failure into immutable regression case
  -> repeat
```

## First implementation stack

Prefer boring/local components:

- Python 3.12+
- Pydantic/JSON Schema
- SQLite
- immutable JSON artifacts + hashes
- provider-neutral model gateway interface
- pytest
- optional FOSSIL integration behind an adapter
- MCP + CLI + HTTP boundary for external agents

Avoid microservices, autonomous agent councils, shared mutable agent memory, and free-form LLM adjudication in V0.
