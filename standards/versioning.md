# Versioning

## Semantic Versioning

All orobobos packages follow [Semantic Versioning 2.0.0](https://semver.org/):

- **MAJOR** — Incompatible API changes
- **MINOR** — Backwards-compatible new functionality
- **PATCH** — Backwards-compatible bug fixes

Tags use `v` prefix: `v1.2.3`

## Pre-1.0

Bricks may start at `v0.1.0`. While < 1.0, minor bumps may include breaking changes. Document these clearly in the changelog.

## Changelog Format

Every repo maintains a `CHANGELOG.md` following [Keep a Changelog](https://keepachangelog.com/en/1.1.0/):

```markdown
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2025-01-15

### Added
- Initial release with core Store interface
- PostgresStore implementation

### Changed
- ...

### Removed
- ...
```

Allowed section headers: `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`.

## Deprecation Policy

**No deprecated shims.** When something is removed, it's removed cleanly:

- Announce removal in the changelog under `Removed`
- Bump the major version
- No `__getattr__` hacks, no re-exports of old names, no compatibility layers

If consumers need migration time, communicate via changelog and release notes before the breaking release.

## Version Location

The version is defined in two places (kept in sync):

1. `pyproject.toml` — `project.version`
2. `src/<package>/__init__.py` — `__version__`

The release workflow validates these match before publishing.

## Release Process

1. Update `CHANGELOG.md` — move Unreleased items to a new version section
2. Update version in `pyproject.toml` and `__init__.py`
3. Commit: `release: v1.2.3`
4. Tag: `git tag v1.2.3`
5. Push: `git push && git push --tags`
6. CI handles the rest (build, publish)
