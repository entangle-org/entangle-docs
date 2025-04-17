# Release Process

This document describes the workflow for promoting Entangle releases.

---

## Branching Model

- `dev`: Active feature development
- `master`: Release-ready branch for test deployment

---

## Releasing Code

Use the `release.sh` script from the parent directory and specify the release version e.g.

```bash
./release.sh v0.3.0