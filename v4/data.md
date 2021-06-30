# Data Structures

## SourceTree / AST

```json
{
    "parser": "haroslaunch",
    "version": "1.0.0",
    "timestamp": 1234567890,
    "tree": {...}
}
```

## Condition / Logic Formula

- atomic values: `true`, `false`
- variables:
    ```json
    {
      "name": "string",
      "text": "string (original text)",
      "data": null (ScopeCondition: SolverResult, traceability, ...)
    }
    ```
- operators: `["<operator>", operands...]`

Example:

```json
["and", true, ["not", false], {"name": "x", "text": "", "data": null}]
```
