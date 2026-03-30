# Seiryu v1.2 Audit Summary

## Scope

Review of `seiryu-v1.1` for hidden issues, missing details, and version-governance gaps.

## Findings fixed in v1.2

1. Integration wording was too optimistic about auto-discovery.
2. Compression deleted originals too aggressively.
3. Git was treated like a hard dependency in multiple skills.
4. Privacy boundaries for auto-saved information were too implicit.
5. "Semantic search" wording was stronger than the implemented heuristic.
6. Theory version metadata lagged behind the current LDRIT baseline.

## v1.2 response

- Added explicit fallback instructions in `INTEGRATION.md` and `CLAUDE.md`
- Made compression reversible with quarantine + manifest
- Downgraded git from required to recommended
- Added explicit sensitive-data exclusions
- Renamed the search claim to heuristic semantic matching
- Updated theory baseline to `LDRIT v0.7-final`

## Remaining non-blocking limitations

- Discovery still depends on the host AI following local instructions correctly
- Compression quality still depends on the summarizer's judgment
- Multi-user support remains intentionally minimal (`default.md`)
