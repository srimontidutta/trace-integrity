# Adoption Guide

Trace Integrity can be added to an existing structured-data agent without changing the agent's entire architecture. The main requirement is to retain the computational commitments that connect a request to execution and to the final answer.

## Evaluation harness

For benchmark or offline evaluation, retain an execution contract beside each generated program. Compare the recorded schema and operators with the expected computation, execute the program, link the result to the reported answer, and store the Trace Integrity assessment. Report answer accuracy, execution success, trace pass rate, and CAIT together when each measure is available.

## Pre-execution validation

An execution contract can be checked before a query is run. Useful checks include schema existence, required filters, join keys, grouping, aggregation, temporal constraints, ordering, limits, and whether the declared plan can be translated into an executable artifact. Failed checks can route the request to correction or review before execution.

## Post-execution review

After execution, retain the query or program, execution status, data-state reference, result linkage, and final answer. This supports answer-consistency checks, replay, incident review, and comparison with the pre-execution contract.

## Regression testing

A set of contracts can serve as regression cases when the surrounding system changes. Re-run the same requests after schema migrations, policy changes, system-instruction revisions, model updates, or tool-interface changes and compare both final answers and computational commitments. Stable answers with changed operators are often worth reviewing because answer agreement alone can hide a regression.

## Deployment-specific choices

The seven dimensions define the framework, but deployments will differ in which dimensions can be checked automatically. A database platform may provide strong guarantees for replayability and schema validity, while operator fidelity may require a combination of structural tests, generated test cases, or human review. Record the assessment procedure alongside the result so that pass rates remain interpretable.

## Data handling

Execution contracts and trace logs can contain sensitive schema information, queries, identifiers, or result references. Apply the same access control, retention, redaction, and audit policies used for other operational data artifacts. A useful contract records computational commitments without storing unnecessary sensitive values or private model reasoning.
