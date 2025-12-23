## Project Structure

Qualitybase follows a standard Python package structure with a clear separation between the library code and development tooling.

### General Structure

```
python-qualitybase/
├── src/
│   └── qualitybase/       # Main package directory
│       ├── __init__.py    # Package exports
│       ├── services/      # Service modules (quality, dev, django, publish)
│       │   ├── quality/   # Quality check modules (lint, security, test, etc.)
│       │   ├── dev/       # Development tooling modules
│       │   ├── django/    # Django-specific services
│       │   ├── publish/   # Publishing services
│       │   └── service/   # Service routing and main entry point
│       ├── commands/      # Command infrastructure
│       └── cli.py         # CLI interface
├── tests/                 # Test suite
│   └── ...
├── docs/                  # Documentation
│   └── ...
├── service.py             # Main service entry point script
├── pyproject.toml         # Project configuration
├── README.md              # Project documentation
└── ...
```

### Module Organization Principles

- **Single Responsibility**: Each module should have a clear, single purpose
- **Separation of Concerns**: Keep different concerns in separate modules
- **Service-Based Architecture**: Services are organized by domain (quality, dev, django, publish)
- **Clear Exports**: Use `__init__.py` to define public API
- **Logical Grouping**: Organize related functionality together

### Service Organization

The `services/` directory contains domain-specific service modules:

- **`quality/`**: Quality check modules (lint, security, test, complexity, cleanup)
- **`dev/`**: Development tooling (venv, install, clean, build, etc.)
- **`django/`**: Django-specific services
- **`publish/`**: Publishing and distribution services
- **`service/`**: Service routing and main entry point

### Package Exports

Define the public API in the main package's `__init__.py` file. Only export what users should directly import.

