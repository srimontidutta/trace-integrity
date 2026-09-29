# CAIT Evaluation

## Definition

For an evaluation with at least one correct answer:

`CAIT = N_correct_and_invalid / N_correct`

The denominator is the number of correct answers under the selected answer criterion. The numerator is the subset of those answers whose traces fail the selected integrity procedure. CAIT is undefined when no answers are correct.

## What to report

A CAIT result is interpretable only with the surrounding evaluation details. Report:

- the answer-correctness criterion;
- the number of evaluated examples;
- `N_correct` and `N_correct_and_invalid`;
- the trace-integrity procedure used to classify traces;
- the dimensions included in that procedure;
- how indeterminate or unverified equivalence cases are handled;
- uncertainty intervals when the number of correct answers is small.

## Interpretation

CAIT identifies answer-level successes whose recorded computational support fails the stated integrity checks. A deterministic structural validator may reject an alternative program whose semantic equivalence it cannot establish. When semantic adjudication is not performed, the CAIT rate should be described as a rate of failed integrity checks rather than a rate of semantically wrong programs.

CAIT complements answer accuracy, execution success, and trace pass rate. Comparisons between systems should avoid ranking small CAIT samples when their uncertainty intervals overlap substantially.
