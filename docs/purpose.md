## Project Purpose

**Qualitybase** is a Python library that provides standardized services and tooling for managing code quality, development workflows, and project maintenance in Python projects.

### Core Functionality

The library provides a unified service interface for:

1. **Quality Checks** (`quality` service):
   - **Linting**: Run multiple linters (ruff, mypy, pylint, semgrep)
   - **Security**: Security vulnerability scanning (bandit, safety, pip-audit, semgrep)
   - **Testing**: Test execution with pytest
   - **Complexity Analysis**: Code complexity metrics (radon)
   - **Cleanup**: Detect unused code, imports, and redundancies (vulture, autoflake, pylint)

2. **Development Tooling** (`dev` service):
   - Virtual environment management
   - Dependency installation (production and development)
   - Build and distribution tasks
   - Cleanup utilities (build artifacts, cache, test files)
   - Library update management

3. **Django Services** (`django` service):
   - Django-specific development and maintenance tasks

4. **Publishing** (`publish` service):
   - Package publishing and distribution workflows

### Architecture

The library uses a service-based architecture:

- Each service domain is organized in its own module directory
- Services are accessed through a unified entry point (`service.py`)
- Services can be invoked via `./service.py <service> <command>` or directly via Python modules
- The system ensures virtual environment setup and proper dependency management
- Services are designed to work consistently across different Python projects

### Use Cases

- Standardized quality checks across multiple Python projects
- Consistent development workflows and tooling
- Automated code quality monitoring
- Security vulnerability detection
- Project maintenance and cleanup tasks
- Unified interface for common Python development tasks
