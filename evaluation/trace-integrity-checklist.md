# Trace Integrity Evaluation Checklist

Use this checklist for each structured-data response.

| Dimension | Evaluation question | Typical evidence |
| --- | --- | --- |
| Explicit | Are the material computational commitments recorded? | Contract fields for schema, filters, joins, grouping, metric, ordering, time window |
| Executable | Is there an executable or deterministically checkable artifact? | SQL, program, structured plan, tool invocation record |
| Schema-valid | Do the referenced schema elements exist and bind to the intended fields? | Schema inspection, parser/binder output |
| Operator-faithful | Do the operations implement the requested computation? | Operator comparison, test cases, semantic review |
| Replayable | Can the computation be rerun under the recorded data state and environment? | Snapshot/version ID, engine version, deterministic parameters |
| Answer-consistent | Does the final answer follow from the executed result? | Result reference, answer extraction record |
| Auditable | Can a reviewer inspect the computation and the basis of any failure? | Structured contract, execution artifact, assessment notes |

## Reporting

For each dimension, use one of four statuses: `pass`, `fail`, `indeterminate`, or `not_assessed`. An indeterminate result is appropriate when the available checker cannot establish the required property, including semantic equivalence between alternative programs.

The overall policy for combining dimensions should be stated by the evaluation. In the paper's proof-of-concept, critical failures in the deterministic checks cause the experimental trace to fail. Other deployments may use a different combination rule, provided that the rule is documented and applied consistently.
