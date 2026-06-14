---
layout: default
title: Versioning
---

# Versioning

OSK follows [Semantic Versioning](https://semver.org/) with one exception during the beta phase.

## Beta phase (`0.x.x`)

During initial development, major refactors may produce breaking API changes that skip multiple minor versions in a single release. For example:

- `0.2` → `0.3` is a standard minor version bump (non-breaking)
- `0.2` → `0.5` represents a **breaking change** — the skipped minor versions indicate significant API shifts

Until a stable `1.0.0` release, minor version increments may contain breaking changes when substantial refactors occur. Consumers should treat any skip in minor versions as potentially non-backward-compatible.

## Post-beta (`>= 1.0.0`)

After reaching `1.0.0`, OSK adheres strictly to Semantic Versioning:

- **MAJOR** — Breaking changes
- **MINOR** — New functionality, backward compatible
- **PATCH** — Bug fixes, backward compatible
