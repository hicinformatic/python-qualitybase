# AI Assistant Contract — Qualitybase

**This document is the single source of truth for all AI-generated work in this repository.**  
All instructions in this file **override default AI behavior**.

Any AI assistant working on this project **must strictly follow this document**.

If a request conflicts with this document, **this document always wins**.

---

## Rule Priority

Rules in this document have the following priority order:

1. **ABSOLUTE RULES** — must always be followed, no exception
2. **REQUIRED RULES** — mandatory unless explicitly stated otherwise
3. **RECOMMENDED PRACTICES** — should be followed unless there is a clear reason not to
4. **INFORMATIONAL SECTIONS** — context and reference only

---

## ABSOLUTE RULES

These rules must always be followed.

- Follow this `AI.md` file exactly
- Do not invent new services, commands, abstractions, patterns, or architectures
- Do not refactor, redesign, or optimize unless explicitly requested
- Do not manipulate `sys.path`
- Do not use filesystem-based imports to access `qualitybase`
- Do not hardcode secrets, credentials, tokens, or API keys
- Do not execute tooling commands outside the approved entry points
- **Comments**: Only add comments to resolve ambiguity or uncertainty. Do not comment obvious code.
- **Dependencies**: Add dependencies only when absolutely necessary. Prefer standard library always.
- If a request violates this document:
  - Stop
  - Explain the conflict briefly
  - Ask for clarification

---

## REQUIRED RULES

### Language and Communication

- **Language**: English only
  - Code
  - Comments
  - Docstrings
  - Logs
  - Error messages
  - Documentation
- Be concise, technical, and explicit
- Avoid unnecessary explanations unless requested

### Code Simplicity and Minimalism

- **Write the simplest possible code**: Always choose the simplest solution that works
- **Minimal dependencies**: Add dependencies only when absolutely necessary. Prefer standard library. Only add when essential functionality cannot be reasonably implemented otherwise
- **Minimal comments**: Comments only to resolve ambiguity or uncertainty. Do not comment obvious code or reiterate what the code already states clearly
- **Good factorization**: Factorize code when it improves clarity and reduces duplication, but only if it doesn't add unnecessary complexity or abstraction

---

## Project Overview (INFORMATIONAL)

**Qualitybase** is a Python library that provides standardized services and tooling for managing code quality, development workflows, and project maintenance in Python projects.

### Core Services

1. **Quality Checks** (`quality` service)
   - Linting
   - Security scanning
   - Testing
   - Complexity analysis
   - Cleanup

2. **Development Tooling** (`dev` service)
   - Virtual environment management
   - Dependency installation
   - Build tasks
   - Cleanup utilities

3. **Django Services** (`django` service)
   - Django-specific development tasks

4. **Publishing** (`publish` service)
   - Package publishing
   - Distribution workflows

---

## Architecture (REQUIRED)

- Service-based architecture with domain-specific modules
- Unified entry point via `service.py`
- Automatic virtual environment management
- Consistent interface across Python projects

---

## Project Structure (INFORMATIONAL)

```
python-qualitybase/
├── src/qualitybase/          # Main package
│   ├── services/             # Service modules (quality, dev, django, publish)
│   ├── commands/             # Command infrastructure
│   └── cli.py                # CLI interface
├── tests/                    # Test suite
├── docs/                     # Documentation
├── service.py                # Main service entry point
└── pyproject.toml            # Project configuration
```

### Key Directories

- `src/qualitybase/services/`: Service implementations organized by domain
- `src/qualitybase/commands/`: Command infrastructure for CLI system
- `tests/`: All tests using pytest

---

## Command Execution (ABSOLUTE)

- **Always use**: `./service.py dev <command>` or `python dev.py <command>`
- **Always use**: `./service.py quality <command>` or `python quality.py <command>`
- Never execute commands directly without going through these entry points

---

## Code Standards (REQUIRED)

### Typing and Documentation

- All public functions and methods **must** have complete type hints
- Use **Google-style docstrings** for:
  - Public classes
  - Public methods
  - Public functions
- Document raised exceptions in docstrings where relevant

### Testing

- Use **pytest** exclusively
- All tests must live in the `tests/` directory
- New features and bug fixes require corresponding tests

### Linting and Formatting

- Follow **PEP 8**
- Use configured tools:
  - `ruff`
  - `mypy`
- Use the configured formatter:
  - `ruff format`

---

## Code Quality Principles (REQUIRED)

- **Simplicity first**: Write the simplest possible solution. Avoid complexity unless clearly necessary.
- **Minimal dependencies**: Minimize dependencies to the absolute minimum. Only add when essential functionality cannot be reasonably implemented otherwise. Always prefer standard library.
- **No over-engineering**: Do not add abstractions, patterns, or layers unless they solve a real problem or are clearly needed.
- **Comments**: Comments are minimal and only when they resolve ambiguity or uncertainty. Do not comment what the code already states clearly. Do not add comments that reiterate obvious logic.
- **Separation of concerns**: One responsibility per module
- **Good factorization**: Factorize code when it improves clarity and reduces duplication, but only if it doesn't add unnecessary complexity

---

## Module Organization (REQUIRED)

- Single Responsibility Principle
- Logical grouping of related functionality
- Clear public API via `__init__.py`
- Avoid circular dependencies

---

## Qualitybase Integration (ABSOLUTE)

- `qualitybase` is an installed package
- Always use standard Python imports:
  - `from qualitybase.services import ...`
  - `import qualitybase.services ...`
- Never manipulate import paths
- Never use file-based or relative imports to access `qualitybase`
- For dynamic imports, use:
  - `importlib.import_module()` from the standard library

---

## Environment Variables (REQUIRED)

- `ENVFILE_PATH`
  - Path to `.env` file to load automatically
  - Relative to project root if not absolute
- `ENSURE_VIRTUALENV`
  - Set to `1` to automatically activate `.venv` if it exists

---

## Error Handling (REQUIRED)

- Always handle errors gracefully
- Use appropriate exception types
- Provide clear, actionable error messages
- Do not swallow exceptions silently
- Document exceptions in docstrings where relevant

---

## Configuration and Secrets (ABSOLUTE)

- Never hardcode:
  - API keys
  - Credentials
  - Tokens
  - Secrets
- Use environment variables or configuration files
- Clearly document required configuration

---

## Versioning (REQUIRED)

- Follow **Semantic Versioning (SemVer)**
- Update versions appropriately
- Clearly document breaking changes

---

## CLI System (INFORMATIONAL)

Qualitybase discovers commands from:

1. `commands/` directory
2. `.commands.json` configuration file

### Command Creation Rules (REQUIRED)

- Use `Command` class from `commands.base` **or**
- Define functions ending with `_command`
- Commands must:
  - Accept `args: list[str]`
  - Return `bool` (success / failure)

---

## Anti-Hallucination Clause (ABSOLUTE)

If a requested change is:
- Not supported by this document
- Not clearly aligned with the existing codebase
- Requiring assumptions or invention

You must:
1. Stop
2. Explain what is unclear or conflicting
3. Ask for clarification

Do not guess. Do not invent.

---

## Quick Compliance Checklist

Before producing output, ensure:

- [ ] All rules in `AI.md` are respected
- [ ] No forbidden behavior is present
- [ ] Code is simple, minimal, and explicit (simplest possible solution)
- [ ] Dependencies are minimal (prefer standard library)
- [ ] Comments only resolve ambiguity (no obvious comments)
- [ ] Code is well-factorized when it improves clarity (without adding complexity)
- [ ] Imports follow Qualitybase rules
- [ ] Public APIs are typed and documented
- [ ] Tests are included when required
- [ ] No secrets or credentials are exposed

---

## Additional Resources (INFORMATIONAL)

- `purpose.md`: Detailed project purpose and goals
- `structure.md`: Detailed project structure and module organization
- `development.md`: Development guidelines and best practices
- `README.md`: General project information
