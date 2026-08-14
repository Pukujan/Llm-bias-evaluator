# LLM Bias Evaluator

A local-first benchmark and middleware project for measuring and reducing framing-dependent shifts in LLM technical judgment.

## Core objective

Given technically equivalent inputs, irrelevant social framing such as ownership, status, prior praise, desired outcome, or expressed user belief should not silently change substantive claims, evidence requirements, risk severity, confidence, or recommendations.

This project does **not** assume that perfect neutrality is achievable. The engineering target is measurable **framing invariance**, explicit provenance, bounded model authority, and detection of residual instability.

## Architecture direction

```text
Codex adapter      OpenCode adapter
      \               /
       \             /
        shared local core
        - benchmark runner
        - framing/intent firewall
        - structured claim schema
        - counterfactual comparator
        - deterministic policy gates
        - audit/event log
               |
               v
          FOSSIL adapter
     evidence + lineage + runs
```

The core remains agent-agnostic. Codex and OpenCode are thin adapters around the same deterministic benchmark/runtime interfaces.

## Rollout strategy

1. **Observer mode** — reproduce the framing benchmark without changing user-visible outputs.
2. **Shadow mode** — generate sanitized/counterfactual evaluations and compare them mechanically.
3. **Warning mode** — surface framing-instability warnings when predefined thresholds fail.
4. **Enforcement experiments** — only after benchmarks show that mitigation improves invariance without causing contrarian regressions.

## Benchmark growth

The original clean-room/ownership experiment becomes the seed suite. Grow it toward roughly 100 distinct technical cases, each with matched counterfactual variants and repeated runs. Do not treat 100 repetitions of one prompt as N=100 independent cases.

Primary metrics include recommendation flip rate, claim classification flip rate, confidence shift, risk severity shift, evidence-requirement shift, unsupported agreement, unsupported criticism, fatal-fault recall, false-criticism rate, and framing invariance.

## Terra and Luna

- **Terra**: deterministic core, schemas, benchmark runner, persistence, FOSSIL integration, policy gates, reproducibility.
- **Luna**: Codex/OpenCode adapters, counterfactual generation, structured evaluator prompts, tone/influence tests, model/provider integration, analysis reports.

Both agents work through issues and evidence-backed acceptance criteria. Neither may self-approve a mitigation solely because an LLM says it improved the system.

See `docs/BUILD_PLAN.md` and `docs/ARCHITECTURE.md` for the initial implementation plan.
