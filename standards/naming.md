# Naming Conventions

## Repository Names

| Scope | Convention | Example |
|-------|-----------|---------|
| Brick repos | `oro-<name>` | `oro-db`, `oro-beliefs`, `oro-infra` |
| Composed project repos | No prefix | `valence`, `bob` |

Bricks are small, focused, reusable components. Composed projects combine bricks into deployable systems.

## Python Packages

- Package name = underscore version of repo name
- `oro-db` → `oro_db`
- `oro-beliefs` → `oro_beliefs`

## Internal Modules

- Use `package.module` structure
- `oro_db.connection`, `oro_beliefs.store`
- Keep modules focused — one clear responsibility each

## Interfaces and Implementations

| Kind | Convention | Example |
|------|-----------|---------|
| Interfaces / ABCs | Clean nouns | `Store`, `Client`, `Transport` |
| Implementations | Descriptive prefix | `PostgresStore`, `HttpClient`, `NatsTransport` |

Interfaces live in the brick's top-level or `interface.py`. Implementations live in their own modules.

## Import Style

```python
# Public API — import from package root
from oro_db import Store, PostgresStore

# Internal — import from module
from oro_db.connection import ConnectionPool
```

## File Naming

- Python files: `snake_case.py`
- No abbreviations in filenames unless universally understood (`db` is fine, `blf` is not)
- Test files: `test_<module>.py`
- Config files: standard names (`pyproject.toml`, `Makefile`, etc.)
