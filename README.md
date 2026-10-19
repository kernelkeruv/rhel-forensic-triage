# RHEL Forensic Triage | Planned project

**Status (October 2026): design / repository scaffold, not an operational forensic triage CLI.**

## Intended defensive use

A future local-first RHEL/Fedora triage utility for collecting host system facts, file hashes and structured evidence bundles without modifying original evidence.

## Repository inventory

This repository currently contains policy, changelog, contribution notes, and GitHub workflow files. **No executable triage implementation, input fixtures or verified bundle generator is present.** An automated CI badge, if displayed, must not be interpreted as proof of forensic accuracy or tool maturity.

## Proposed minimum viable implementation

1. Use standard Linux utilities for a *read-only*, bounded host inventory: OS/kernel metadata, systemd unit status, auditd status, network listeners, and selected file-hash manifests. Avoid indiscriminate copying of private logs.
2. Emit versioned `manifest.json` with timestamps in UTC and an explicit America/Toronto field (when applicable), host/tool versions, collection commands, exit codes, artifact hashes and selection scope.
3. Produce SHA-256 and SHA-512 sums for every derived artifact and verify them on readback. Document where source hashes cannot be obtained.
4. Ship sanitized synthetic fixtures, golden expected outputs, unit tests and a safe disposable-VM smoke test.
5. Explain chain-of-custody limitations, host clock dependence, privileges and any unavoidable system changes before claiming forensic suitability.

## Validation checklist (not yet implemented)

- [ ] Source CLI committed and pinned environment documented
- [ ] Sample dry-run generated on disposable Fedora/RHEL VM
- [ ] No-write-to-source behavior reviewed
- [ ] Negative and failure-path tests with exact expected exit codes
- [ ] Machine-readable JSON schema and reproducible test fixtures
- [ ] Signed/reproducible releases and documented evidence limitations

Do not cite this project as a finished forensic CLI until those items are delivered. The source portfolio currently demonstrates planning and workflow design rather than a tested product.
