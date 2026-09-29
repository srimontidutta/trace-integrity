# FAQ

## How does Trace Integrity relate to answer accuracy?

Answer accuracy measures agreement with a reference result. Trace Integrity examines whether the recorded computation provides inspectable support for that answer. Reporting both separates outcome agreement from computational support.

## Where does execution success fit?

Execution success establishes that a query or program runs. Trace Integrity also examines schema bindings, joins, filters, aggregation, grouping, temporal constraints, answer linkage, and the other dimensions defined in the framework.

## How should a structural validation failure be interpreted?

A deterministic structural checker can be unable to establish equivalence between two valid programs. Evaluations should identify the checks used and, when available, distinguish validator-detected failures from independently adjudicated semantic errors.

## Why retain an execution contract when SQL is already stored?

SQL records the executable program. The execution contract records the intended computational commitments in a structured form that can be compared with the program. This pairing helps localize mismatches in planning, schema binding, program generation, execution, or final-answer linkage.

## How should deployments use the seven dimensions?

The seven dimensions define the broader criterion. A deployment can state which dimensions are checked directly, which are supported by its logging or execution environment, and which remain unassessed. The paper's proof-of-concept reports a narrower experimental operationalization.

## What happens when there are no correct answers?

CAIT is undefined because its denominator is zero. Answer accuracy and the available trace-level measures can still be reported.

## Can Trace Integrity be used outside SQL?

The framework applies whenever an agent's answer depends on structured computational commitments that can be retained and inspected. Examples include table transformations, analytics tools, spreadsheet operations, and other programmatic data workflows.

## How is the Isolation Principle evaluated?

The paper proposes the Isolation Principle as a planning discipline. A direct experimental test would vary the timing of value-level access while keeping the remaining setup controlled; the BIRD proof-of-concept evaluates the execution-contract conditions without that intervention.
