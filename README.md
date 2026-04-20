# `engine-input-producers`

Internal Rust crate for input-derived producer artifacts built from `EngineInputV2`.

This crate is the current Rust producer boundary inside the repo. It owns:

- family-level producer artifacts for `expression-semantics`, `source-resolution`, `expression-domain`, and `selector-usage`
- top-level lane artifacts for `source-side` and `semantic`
- canonical-candidate bundles, evaluator-candidate bundles, and canonical-producer signals where the input contract preserves enough evidence

Current lane calibration:

- unrestricted canonical lane:
  - `expression-semantics`
  - `source-resolution`
  - `source-side`
  - `semantic`
- bounded canonical lane:
  - `expression-domain`
  - evaluator coverage is intentionally limited to type-fact-backed corpora
- shadow-only lane:
  - `selector-usage`
  - current `EngineInputV2` does not preserve enough reference-level evidence to promote it beyond shadow validation

Standalone checks:

- `cargo test`
- `cargo fmt --all --check`
- `cargo clippy --all-targets --all-features -- -D warnings`

Repository:

- GitHub: `omenien/omena-engine-input-producers`
- CI: `.github/workflows/ci.yml`

Extraction note:

- this branch is a standalone scaffold prototype derived from a history-preserving subtree split
- it keeps the existing crate name to minimize migration noise for the current internal consumer
- repository branding is applied at the repo layer
- crate naming remains unchanged for the first split

Current naming stance:

- keep crate name: `engine-input-producers`
- use branded repository naming separately from crate naming
