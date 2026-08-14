# Framing Benchmark Specification

## Unit of analysis

One benchmark case is one underlying technical evaluation problem with a fixed evidence payload and a family of semantically matched framing variants.

`N` counts distinct underlying cases. Repeated stochastic runs are recorded separately and do not increase `N`.

## Required variant family

Each case should support, where semantically valid:

1. `control_anonymous`
2. `ownership_user`
3. `user_belief_positive`
4. `user_belief_negative`
5. `authority_positive`
6. `authority_negative`
7. `social_proof_positive`
8. `social_proof_negative`
9. `prose_polished`
10. `prose_terse_or_degraded`

The technical evidence, requested decision, and material constraints must remain fixed across a matched set unless the case explicitly tests a different variable.

## Structured result contract

Every run must emit a structured result before any human-facing prose:

- case_id
- variant_id
- repetition_id
- provider/model/version
- system/prompt hashes
- evidence bundle hash
- claims[]
- per-claim classification
- per-claim confidence
- severity
- evidence_for/evidence_against
- falsifier
- requested_additional_evidence
- final recommendation/status
- run metadata and errors

## Baseline metrics

- recommendation_flip_rate
- claim_classification_flip_rate
- mean_absolute_confidence_shift
- risk_severity_shift_rate
- evidence_requirement_shift_rate
- unsupported_agreement_rate
- unsupported_criticism_rate
- fatal_fault_recall
- false_criticism_rate
- citation/evidence consistency
- within-condition run variance
- cross-condition effect size

Never collapse all metrics into one “unbiased percentage” in V0.

## Experimental discipline

- Predeclare the variable changed by each variant.
- Randomize variant order where order could matter.
- Preserve exact evidence hashes across matched variants.
- Keep raw outputs immutable.
- Separate model/run variance from framing sensitivity.
- Do not use majority vote to establish truth.
- Use planted-fault/mechanical cases where ground truth can be established.
- Include clean controls so adversarial prompting cannot look good by inventing flaws.

## N≈100 composition target

Suggested initial distribution:

- 20 planted-fault software/architecture cases
- 20 clean/simple technical controls
- 20 architecture trade-off cases with explicit evidence
- 15 evidence/citation verification cases
- 15 coding/review cases
- 10 ambiguity/human-preference boundary cases

The distribution is a starting hypothesis and should be revised by benchmark coverage analysis.

## Promotion gates for mitigations

A mitigation is eligible to move from shadow to warning/enforcement experiments only if it:

1. reduces predefined framing-sensitivity metrics on the development suite;
2. also improves or preserves performance on held-out cases;
3. does not materially increase false criticism or contrarian behavior;
4. preserves fatal-fault recall;
5. does not erase legitimate human constraints/preferences;
6. remains reproducible under repeated runs;
7. has an auditable versioned policy/prompt/config diff.
