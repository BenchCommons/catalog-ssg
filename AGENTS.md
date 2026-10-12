# AGENTS.md — catalog-ssg

Follow the org-wide rules in [BenchCommons/.github AGENTS.md](https://github.com/BenchCommons/.github/blob/main/AGENTS.md) and the decisions in [.product](https://github.com/BenchCommons/.product). This file only adds what is specific to this repo.

## Role
Catalog (`catalog-*`): static site generators measured by benchmark-tool (renamed from `ssg-frameworks`, see issue #203).

## Layout
- `<Lang>/<id>/` contains:
  - `<id>.dockerfile`: pinned version;
  - `build.sh`: byte-identical across generators, enforced by `tools/check-build-sh.sh`;
  - `benchmark_config.json`;
  - `generator.json`: validated by `schema/generator.schema.json`;
  - `src/`.
- `generators.json` is derived by `tools/build_index.py`. CI runs it with `--check`, so never edit it by hand.
- `reference/` holds the golden output for conformance.

## Rules
- The catalog contract is owned by benchmark-tool (benchmark-tool#29). Change it there first.
- CI smoke-tests only the changed generators, on amd64 and arm64.
