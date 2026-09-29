# Trace Integrity Specification

Trace Integrity applies to structured-data answers that depend on a recorded computation, including SQL queries, table operations, data transformations, and tool-mediated analytical steps. The framework evaluates the computational support for an answer through the operations, schema bindings, execution artifacts, and answer linkage preserved in the trace. Questions about data quality, fairness, or downstream decision suitability require their own evaluation procedures.

## Structure Gap

The **Structure Gap** is the mismatch between natural-language intent and the operator-level computation required to satisfy that intent. Structured-data requests may commit a system to particular records, joins, filters, grouping keys, aggregation functions, temporal windows, ordering rules, limits, or schema bindings. A fluent description of the intended analysis is not sufficient when the executed operations differ from those commitments.

## Trace record

A trace record should retain the information needed to inspect how a structured-data answer was produced. The relevant contents depend on the execution environment, but commonly include:

- the user request or normalized intent;
- schema elements used by the computation;
- filters and exclusions;
- joins and join keys;
- grouping and aggregation;
- ordering, ranking, or limit operations;
- temporal constraints;
- assumptions that affect the computation;
- the executable query or program;
- execution status and result linkage;
- the final answer derived from the execution.

## Seven dimensions

### Explicit

The trace records the computational commitments needed to answer the request. An assessment should be able to identify the measure, grouping key, filters, time window, join path, or other operators that materially determine the result.

### Executable

The trace contains a query, program, or structured plan that can be run or deterministically checked. A free-text rationale alone does not provide an executable artifact.

### Schema-valid

Tables, columns, fields, join keys, and other schema references used by the computation exist in the available schema and refer to the intended elements.

### Operator-faithful

The recorded operations preserve the user's requested computation. Typical checks concern aggregation functions, joins, filters, grouping, ordering, ranking, temporal restrictions, and limits.

### Replayable

The computation can be re-executed under the same recorded data snapshot and execution environment and yields the same result. Reproducibility requires enough environment information to identify the relevant data state and execution context.

### Answer-consistent

The final response follows from the executed trace. This check links the result produced by the computation to the answer presented to the user.

### Auditable

The trace preserves enough structure for a reviewer or validation system to inspect the computation, assumptions, and identified failure mode.

## Execution contract

An **execution contract** is a compact artifact that records intended computational commitments before or alongside execution. It can be checked before execution, retained with execution results, and reviewed after the answer is produced.

The paper's illustrative contract contains an intent, schema commitments, an operator plan, and verification state. The repository schema adds practical record fields for execution and final-answer linkage so that the same artifact can support pre-execution validation and post-execution review.

## CAIT

For `N_correct > 0`,

`CAIT = N_correct_and_invalid / N_correct`.

`N_correct_and_invalid` counts examples whose final answer is correct under the selected answer criterion and whose trace fails the selected integrity checks. `N_correct` is the total number of correct answers. CAIT is undefined when there are no correct answers.

CAIT depends on the integrity procedure used to classify traces. A deterministic structural validator may be unable to establish semantic equivalence for a valid alternative program. Evaluations should therefore document the checks used to determine trace validity and distinguish validator-detected failures from independently adjudicated semantic errors when such adjudication is available.

## Experimental operationalization in the paper

The paper's proof-of-concept uses deterministic operator-level checks against a normalized gold trace. The normalized trace records referenced schema elements and query operations relevant to the request, including joins, filters, grouping, aggregation, ordering, and limits. The validator compares these commitments rather than SQL surface form.

The reported Trace Integrity Pass Rate is narrower than the full seven-dimensional criterion. It scores executability, schema validity, operator fidelity, and answer consistency from the generated SQL and recorded artifacts. Explicitness is represented by the presence of the required structured artifact. Replayability and auditability are properties of the retained evaluation record rather than separately scored metrics in that experiment.

Equivalent SQL rewrites that the deterministic checker cannot establish as equivalent may be flagged. The paper therefore treats CAIT as a diagnostic of computational support under the stated checks rather than a semantic-error prevalence estimate.

## Isolation Principle

The **Isolation Principle** proposes that an LLM data agent specify its intended computation before value-level data access by default. This separates specification from execution and makes later changes to the plan visible in the trace. Some tasks require value inspection, including profiling, deduplication, outlier analysis, and value-dependent thresholds; in those cases, the trace should record why access was needed and how it changed the plan.

The proof-of-concept does not isolate this principle experimentally. A direct test would vary the point at which result values become available to the model while holding the remaining setup fixed.
