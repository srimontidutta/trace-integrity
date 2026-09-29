# Execution-Contract Schema

`execution-contract.schema.json` provides a reusable JSON representation of the execution contract described in the paper. The schema records intent, schema commitments, operator plan, assumptions, execution information, answer linkage, and Trace Integrity assessment.

Implementations can extend the record with environment-specific identifiers, data-snapshot metadata, permissions, or tool-call references while retaining the same conceptual structure. Stable field names make contracts easier to exchange across evaluation and production tooling.
