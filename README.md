# Insurex Gate — Verification Work in Progress

This repository is the **tests/gate** component of the QMOOSA-1000 staking slashing-insurance family (Batch 163). It is **not** production-certified, FIPS-validated, security-approved, or deployment-ready.

## Current security and implementation status

- GitHub Actions must execute actual Python and Rust checks; a printed score is not verification.
- The inherited `tests/reality_battery.py` contains non-printable / malformed source and currently prevents Python compilation. Do not delete or skip the file to obtain a green badge. Reconstruct meaningful implementation-coupled tests against the protocol/engine APIs.
- The inherited `tests/reality_check_harness.py` asserts constants and prints unverified claims about QuickNode, PQC and escrows. It is not evidence of real integration.
- `src/main.rs` emits unverified operational and FIPS claims; replace those with real checks before making any readiness assertion.
- `insurex-run/src/engine.rs` has an invalid Rust source suffix; remediate independently in that owned engine repository before accepting family-level implementation.

## Local verification

```bash
python -m pip install -r requirements.txt
python -m compileall -q tests
python -m pytest -q tests
cargo check --all-targets
cargo test --all-targets
```

Failing commands are genuine blockers. A passing workflow would establish only the specific checks it executes, **not** security approval or production readiness. No chain deployment, key use, or paid service is required for these checks.
