# CellScript iCKB Equivalence

This repository contains the iCKB equivalence evidence used by CellScript.

It is not a marketing benchmark. It is a set of executable specs, fixtures, original binary references, and reports for checking whether CellScript models the intended iCKB behaviour closely enough to support a production-equivalence claim.

## Repository Map

| Path | Purpose |
| --- | --- |
| `ickb_specs/` | CellScript benchmark specs for the iCKB model surface. |
| `ickb_diff/claim_manifest.json` | The branch-level claim manifest consumed by `cellc verify-ckb-fixtures`. |
| `ickb_diff/matrix.json` | Differential evidence matrix. |
| `ickb_diff/ckb_vm_fixtures/` | CKB VM fixtures for direct pass/fail checks. |
| `ickb_diff/original_binaries/` | Original binary evidence used for comparison. |
| `ickb_positive/` | Accepted model fixtures. |
| `ickb_negative/` | Rejected model fixtures. |
| `docs/` | Carried reports and branch notes explaining the claim boundary. |

## Quick Check

From a CellScript checkout with this repository mounted at `tests/benchmarks`:

```bash
cargo run --locked -p cellscript --bin cellc -- \
  verify-ckb-fixtures tests/benchmarks/ickb_diff/claim_manifest.json --json
```

From this repository alone, keep a neighbouring or otherwise accessible CellScript checkout and pass the manifest path to `cellc` from there.

## What The Evidence Means

The positive fixtures describe behaviours that should be accepted. The negative fixtures describe behaviours that should be rejected. The matrix and manifest connect those scenarios to the concrete iCKB claim surface.

The useful question is not "does this compile?" The useful question is:

```text
Does the CellScript model accept and reject the same cases that the iCKB claim requires?
```

That is why this repository keeps specs, fixtures, binaries, and reports together.

## Start Here

- `docs/CELLSCRIPT_0_17_ICKB_PRODUCTION_EQUIVALENCE_GATE.md`
- `docs/CELLSCRIPT_0_17_ICKB_FINAL_REPORT.md`
- `ickb_specs/README.md`
