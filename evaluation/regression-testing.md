# Regression Testing with Trace Integrity

Trace records can be reused as regression tests when a data-agent pipeline changes. The same structured requests can be rerun after updates to schemas, system instructions, retrieval context, execution policies, model versions, or tool interfaces.

A regression suite can compare:

- answer agreement;
- execution success;
- schema bindings;
- filters and exclusions;
- join paths and keys;
- grouping and aggregation;
- temporal constraints;
- ordering and limits;
- answer-trace linkage;
- the resulting Trace Integrity assessments.

The comparison is most useful when expected computational commitments are retained separately from a single observed answer. This allows a pipeline change to be detected even when the final value happens to remain unchanged.

When an alternative program is semantically valid but structurally different, the test should record that equivalence explicitly or mark the structural comparison as indeterminate rather than treating structural difference alone as evidence of semantic error.
