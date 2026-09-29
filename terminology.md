# Terminology

**Answer Accuracy**  
Whether the reported or executed result matches the selected reference result under the evaluation's answer criterion.

**Answer-Trace Consistency**  
Whether the final answer follows from the executed trace and, when present, from the declared operation summary or execution contract.

**Auditable**  
A Trace Integrity dimension requiring the computation, assumptions, and identified failure mode to remain inspectable by a reviewer or validation system.

**CAIT (Correct Answer / Invalid Trace) Rate**  
For systems with at least one correct answer, the fraction of correct answers whose traces fail the applicable integrity checks.

**Execution Contract**  
A structured record of intended computational commitments, including schema elements, operations, assumptions, executable artifacts, verification state, and answer linkage where available.

**Execution Success**  
Whether the generated query or program executes successfully.

**Executable**  
A Trace Integrity dimension requiring a query, program, or structured plan that can be run or deterministically checked.

**Explicit**  
A Trace Integrity dimension requiring the computational commitments needed to answer the request to be recorded.

**Isolation Principle**  
The proposed default discipline of specifying intended computation before value-level data access, while recording justified departures when value inspection is required.

**Normalized Gold Trace**  
The operator-level representation used in the paper's proof-of-concept to record relevant schema elements and query operations from the gold SQL, including joins, filters, grouping, aggregation, ordering, and limits.

**Operator-faithful**  
A Trace Integrity dimension requiring the recorded operations to preserve the computation requested by the user.

**Replayable**  
A Trace Integrity dimension requiring the recorded computation to be re-executable under the same data snapshot and execution environment with the same result.

**Schema-valid**  
A Trace Integrity dimension requiring referenced schema elements to exist and bind to the intended tables, columns, fields, and join keys.

**Structure Gap**  
The mismatch between natural-language intent and the operator-level computation required to satisfy that intent.

**Trace Integrity**  
The property that the recorded computation supporting a structured-data answer is explicit, executable, schema-valid, operator-faithful, replayable, answer-consistent, and auditable.

**Trace Integrity Pass Rate**  
The proportion of evaluated traces that pass the specified integrity procedure. The paper's experimental rate uses a narrower operationalization than the full seven-dimensional definition.
