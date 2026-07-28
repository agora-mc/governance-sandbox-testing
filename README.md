# Governance Sandbox Testing

**This directory is a disposable sandbox for testing the Agora governance
compiler pipeline.** It is **not** the main Agora registry.

## Purpose

- Test canonical vote issue mapping (`vote_issues.json`)
- Test poll blacklist filtering (`poll_blacklist.json`)
- Test quarantine decision flows (`quarantine_decisions.json`)
- Validate compiler governance modes: `off`, `read-only`, `monitor`
- Experiment with registry manifest schema for mod governance fields

## Structure

```
.github/ISSUE_TEMPLATE/     # Copied from main Agora repo (review-form, mod-submission, config)
registry/
  mods/
    test-alpha.json          # Disposable sandbox mod (direct_hash, MIT)
    test-beta.json           # Disposable sandbox mod (direct_hash, MIT)
  governance/
    vote_issues.json         # Canonical issue to registry ID mapping
    quarantine_decisions.json# Empty quarantine decision log
    poll_blacklist.json      # Empty poll blacklist
docs/
  CANONICAL_VOTE_ISSUE.md    # Documents the two canonical vote issues
build/                       # Build output (gitignored)
.gitignore
README.md                    # This file
```

## Important

- All registry entries use fake names, `https://example.invalid` URLs, and
  `MIT` licenses. They are **not** real mods.
- The `sha256` hashes are fixture values for compiler testing only.
- **No compiler code lives here.** The actual compiler remains at
  `D:\Agora\compiler\`. This sandbox provides flat-file manifests that the
  compiler can consume when pointed at this directory.
- To compile from the main repository: `python compiler/compile.py --registry-root D:/governance-sandbox-testing/registry --governance-mode off --governance-policy sandbox --skip-sign --out D:/governance-sandbox-testing/build/registry.db`
- Delete this directory at any time; nothing depends on it.
