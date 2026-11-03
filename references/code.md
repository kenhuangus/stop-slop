# Code and Engineering Anti-Slop Guide

Standards for eliminating AI slop, placeholder stubs, redundant commentary, and superficial code generation from autonomous coding agents and automated refactoring workflows.

## 1. Decision-Focused Comments

Comments must explain *why* an architectural or implementation choice was made, rather than restating *what* the syntax accomplishes.

### Unacceptable Code Slop (Syntax Restatement)
```python
# Check if user is None
if user is None:
    # Return 404 response
    return {"error": "Not found"}, 404

# Loop through all items in the list
for item in items:
    # Add item price to total
    total += item.price
```

### Clean Anti-Slop (Decision and Invariant Rationale)
```python
if user is None:
    # Upstream auth middleware passes synthetic guest tokens when sessions expire;
    # return explicit 404 rather than triggering silent re-authentication.
    return {"error": "Not found"}, 404

for item in items:
    # Prices include regional VAT already calculated during catalog sync
    total += item.price
```

### Comment Standards
* Delete comments that merely rephrase function, variable, or class names.
* Document non-obvious business logic, concurrency constraints, memory invariants, or protocol quirks.
* Preserve existing comments and docstrings during refactoring unless explicitly instructed to revise them.

## 2. Complete, Runnable Implementations

Coding agents must never leave incomplete stubs or synthetic placeholders when implementing features.

### Common Engineering Slop Patterns
* **The Lazy Stub**: Placing `// TODO: Implement remaining 10 handlers` or `pass # Logic goes here` in requested core routines.
* **The Mock Disguised as Real**: Returning hardcoded sample JSON or mocked database objects inside production service classes.
* **Truncated Code Outputs**: Using `... [rest of code unchanged] ...` inside single-file edits when the tooling expects atomic file replacements.
* **Fabricated Tests**: Writing assertions that test tautologies (e.g., `assert True == True` or `assert client is not None`) rather than validating system outputs against known inputs.

### Production Execution Standards
* Write complete, runnable code for all requested endpoints and functions.
* If a full implementation depends on an external service or credentials that are missing, explicitly document the required configuration parameters and fail loudly with an informative error rather than silently mocking responses.
* Every unit or integration test must exercise a real boundary and assert against actual expected state changes.

## 3. Minimal, Direct Architecture

Avoid unnecessary abstraction layers that serve no operational purpose.

* **No Premature Generalization**: Do not create generic base interfaces, abstract factories, or meta-programming decorators for operations that only have a single concrete implementation.
* **Flat Over Nested**: Keep function calls and module structures direct. Avoid five levels of directory nesting for small utility scripts.
* **Standard Library and Direct APIs**: Use verified language built-ins and standard APIs rather than importing single-purpose third-party packages for trivial operations (e.g., left-pad, basic string splitting).

## 4. Defensive Security and Environment Boundaries

* **No Hardcoded Secrets**: Never place API keys, private keys, database passwords, or auth tokens in source code, configuration files, or prompt artifacts.
* **Documented, Sanctioned Paths**: Do not bypass authentication gates, TLS verification, or permission checks in test harnesses or deployment scripts.
* **Deterministic Verification**: Verify code execution with reproducible test commands (`pytest`, `npm test`, `go test`) rather than claiming changes work without execution.

## 5. Review Checklist for Coding Agents

Before committing or delivering code:

1. Are all comments decision-focused rather than descriptive of syntax?
2. Are all requested functions fully implemented without placeholder stubs or synthetic mocks?
3. Have all test assertions verified real business requirements?
4. Are there any unnecessary boilerplate wrappers or redundant abstraction layers?
5. Has the code been executed and verified in the target environment?
