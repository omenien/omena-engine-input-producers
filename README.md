# `omena-engine-input-producers`

Input-derived producer artifacts for Omena CSS semantic analysis.

This crate owns:

- family-level producer artifacts for `expression-semantics`, `source-resolution`, `expression-domain`, and `selector-usage`
- top-level lane artifacts for `source-side` and `semantic`
- canonical-candidate bundles, evaluator-candidate bundles, flow-analysis summaries, and canonical-producer signals where the input contract preserves enough evidence

Current lane calibration:

- unrestricted canonical lane:
  - `expression-semantics`
  - `source-resolution`
  - `source-side`
  - `semantic`
- bounded canonical lane:
  - `expression-domain`
  - evaluator coverage is intentionally limited to type-fact-backed corpora
  - flow analysis currently exposes explicit type-fact branch joins as the first 1-CFA product slice
- shadow-only lane:
  - `selector-usage`
  - current `EngineInputV2` does not preserve enough reference-level evidence to promote it beyond shadow validation

Primary checks:

- `cargo fmt --all --check`
- `cargo test`
- `cargo clippy --all-targets --all-features -- -D warnings`
- `cargo publish --dry-run`

Monorepo release-facing bundle:

- `pnpm check:rust-release-bundle`
