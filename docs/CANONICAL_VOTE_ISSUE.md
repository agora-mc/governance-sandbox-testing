# Canonical Vote Issue — Governance Sandbox

This document describes the canonical voting issues used in the governance sandbox
at `D:\governance-sandbox-testing`. These issues are placeholders for testing the
compiler and launcher governance pipeline (vote tallying, reaction parsing,
poll_blacklist filtering, and quarantine decisions).

## Registered Canonical Issues

| Issue # | Registry ID    | Title                                          |
|---------|----------------|-------------------------------------------------|
| 1       | `test-alpha`   | [SANDBOX] Canonical Vote: Test Alpha Mod       |
| 2       | `test-beta`    | [SANDBOX] Canonical Vote: Test Beta Addon      |

## Mapping

The mapping between issue numbers and registry item IDs is stored in
`registry/governance/vote_issues.json`. The compiler reads this file to
associate GitHub issue `+1`/`-1` reactions with registry items.

Both issue numbers (1, 2) are documented here for convenience; each maps to
its respective sandbox manifest in `registry/mods/`.

## Usage

1. Create GitHub Issues #1 and #2 in this repository with the titles above.
2. Add the `community-review` label to both.
3. The compiler (when run in `read-only` or `monitor` mode) will read reactions
   on these issues and apply them to the corresponding registry items.
4. Test vote-weight scenarios by adding reactions from various accounts.
5. Test `poll_blacklist` by adding a username to `poll_blacklist.json` and
   verifying that user's votes are zero-weighted.

## Disposal

This entire sandbox directory is disposable. Delete the repository or
directory when testing is complete. The real compiler at `D:\Agora\compiler\`
is unaffected.
