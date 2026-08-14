# Architecture Contract

## Goal

Build a model- and agent-independent system that measures framing sensitivity and prevents irrelevant social framing from silently acquiring epistemic or decision authority.

The target is **framing invariance**, not a claim of perfect neutrality.

## Non-goals

- No majority-vote truth.
- No autonomous self-approval of mitigations.
- No assumption that stricter or more negative output is more correct.
- No assumption that anonymous framing is automatically superior.
- No raw-conversation embedding as the primary technical retrieval query.
- No requirement that FOSSIL/Graphiti/Neo4j become the truth source.

## Core components

### 1. Raw artifact store

Persist the exact user/request artifact immutably for audit and reproducibility.

### 2. Semantic/framing extractor

An LLM may propose a typed representation containing:

- task;
- facts;
- constraints;
- preferences;
- user hypotheses;
- supplied evidence;
- uncertainty;
- ownership/status cues;
- desired-outcome cues;
- confidence/tone cues.

The extractor proposes. It does not decide authority.

### 3. Deterministic authority firewall

Middleware assigns/validates source classes and decides which fields may cross into evaluator context.

Examples:

- `USER_REQUIREMENT` -> preserve;
- `USER_PREFERENCE` -> preserve as preference, not evidence;
- `USER_HYPOTHESIS` -> preserve as hypothesis, not evidence;
- `OWNERSHIP_CUE` -> quarantine unless materially relevant;
- `STATUS_CUE` -> quarantine unless materially relevant;
- `EXTERNAL_EVIDENCE` -> preserve with provenance;
- `MODEL_INFERENCE` -> never silently promote to evidence or human intent.

### 4. Canonical evaluator packet

Evaluation operates on a canonical technical packet rather than the raw social conversation whenever the benchmark condition requires sanitization.

### 5. Retrieval boundary

Technical retrieval embeds/searches canonical semantic content, not the raw conversation by default.

Embeddings and graph projections are replaceable providers, not durable authority.

### 6. Structured evaluator output

Before prose, reviewers emit a machine-readable claim ledger including:

- claim ID;
- classification;
- confidence;
- severity;
- evidence for/against;
- falsification test;
- recommendation;
- required evidence;
- uncertainty.

### 7. Deterministic comparator

Matched counterfactual runs are compared mechanically for claim/recommendation/risk/confidence/evidence-requirement changes.

### 8. Influence renderer

Presentation is downstream of the structured result. Tone may improve readability but must not change epistemic strength.

### 9. Adapters

- Codex: MCP/CLI/API integration around the shared core.
- OpenCode: MCP plus optional deeper plugin hooks.

No adapter owns benchmark truth or policy.

### 10. FOSSIL integration

FOSSIL is used as an evidence/lineage substrate because its architecture already separates durable evidence/events from rebuildable graph/vector/model projections.

Store benchmark cases, variants, runs, claims, evidence links, mitigation versions, and supersession history as provenance-bearing artifacts/events.

Do **not** let the graph decide whether a model is unbiased.

## Operating modes

1. Observer — record only.
2. Shadow — produce hidden sanitized/counterfactual outputs and compare.
3. Warning — warn on predefined instability thresholds.
4. Enforcement experiment — only after benchmark evidence supports the mitigation.

## Promotion rule

A mitigation may be proposed by an LLM, but promotion requires:

- deterministic benchmark results;
- predeclared acceptance thresholds;
- regression checks for false criticism/contrarianism;
- human approval during early milestones.
