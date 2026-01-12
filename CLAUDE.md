# Claude Code Global Guidelines

## I. The Autonomy Protocol (CRITICAL)

**To operate autonomously without human intervention, you must adhere to the "Spec-Test-Lint" cycle.**

### 1. Specification First
Never start coding without a clear specification. If a task is ambiguous:
1.  **Stop.**
2.  **Ask** the user to clarify requirements or propose a detailed plan yourself.
3.  **Confirm** the plan before writing a single line of implementation code.

### 2. Exhaustive Linting (Strict Mode)
- **Zero Tolerance:** The build must pass with **zero** linting warnings.
- **Strict Configuration:** If setting up a new project, configure the linter (ESLint, Clippy, Pylint, GolangCI-Lint) to its strictest reasonable setting.
- **Type Safety:** In typed languages (TS, Go, Rust, etc.), do not use `any`, `interface{}`, or loose casting unless strictly necessary and documented.

### 3. 100% Test Coverage Requirement
**A feature is not "done" until it is fully tested.**
- **Full Coverage:** Every new logical path must be covered by a test.
- **Red/Green Refactor:** Write the test *before* or *alongside* the implementation.
- **Verification:** You must run the test suite and verify it passes before confirming task completion.

---

## II. Development Guidelines

### 1. Task Completion Definition
A task is ONLY complete when:
1.  Code compiles/runs.
2.  **All** tests pass.
3.  **No** linter warnings exist.
4.  Code is formatted (prettier/fmt).
5.  No incomplete artifacts (`TODO`, `FIXME`, commented-out blocks) remain.

**If you cannot implement something properly, stop and ask the user for clarification.**

### 2. No Half-Implementations
- Handle **all** valid inputs, not just the "happy path."
- Implement proper error handling for every failure case (Network, IO, Parse errors).
- Do not use placeholder stubs unless explicitly meant for scaffolding.

### 3. No Hardcoding
**Never hardcode values that should be computed or configured:**
-   Use configuration files/environment variables for adjustable values.
-   Derive behavior from input data.
-   Parameterize logic that might vary.

### 4. Universal Best Practices
Follow the idiomatic patterns of the language you are using:
-   **Type Safety:** Use strict typing where available (e.g., TypeScript interfaces, Python type hints, Rust structs).
-   **immutability:** Prefer immutable variables/consts where possible.
-   **Functional Style:** Prefer pure functions and transformations (map/filter/reduce) over stateful loops where readable.
-   **DRY:** Extract repeated logic into helper functions.

### 5. Error Handling
- **Catch Specifics:** Never catch generic "Errors" or "Exceptions" if specific ones can be handled.
- **Context:** Wrap errors with context (e.g., "Failed to parse config" vs just "Parse Error").
- **Fail Fast:** Validate inputs at the boundary of the system.

### 6\. Documentation
-   **Public API:** All public classes, functions, and modules must have docstrings/comments.
-   **Examples:** Include usage examples in documentation where complex.
-   **Location:** Place project-level documentation in a `docs/` directory if it exists, otherwise use `README.md`.

### 7\. Automated Boilerplate
**Reduce manual boilerplate:**
-   Use language features (decorators, macros, generators) to reduce repetitive code.
-   Use libraries for validation (e.g., Pydantic, Zod, Serde) rather than writing manual parsers.

Security
--------
-   Validate all external inputs.
-   Never commit secrets (API keys, tokens).
-   Use constant-time comparisons for sensitive data.
-   Sanitize inputs to prevent injection attacks (SQLi, XSS).

---

## III. Language-Specific Standards (Dynamic)

Apply the best tools for the detected language:

| Language | Linter | Test Runner | Formatter | Strictness |
| :--- | :--- | :--- | :--- | :--- |
| **Rust** | `cargo clippy` | `cargo test` | `cargo fmt` | `deny(clippy::all)` |
| **TypeScript** | `eslint` | `vitest` / `jest` | `prettier` | `strict: true` (tsconfig) |
| **Python** | `ruff` / `pylint` | `pytest` | `black` | Type hints required |
| **Go** | `golangci-lint` | `go test` | `gofmt` | Check error returns |

---

## IV. Project Structure & Planning

### When Starting a New Project/Feature:
1.  **Create a Plan:** Write a Markdown file (or scratchpad entry) outlining the architecture.
2.  **Define Interfaces:** Write the types/structs/interfaces first.
3.  **Setup Tooling:** Ensure the linter and test runner are active immediately.

**When entering a new codebase, automatically identify:**
1.  **Build System:** (e.g., `package.json`, `Cargo.toml`, `go.mod`, `requirements.txt`)
2.  **Project Root:** The directory containing the main configuration file.
3.  **Source Location:** usually `src/`, `lib/`, or `app/`.
4.  **Test Location:** usually `tests/`, `__tests__/`, or co-located `*_test` files.
