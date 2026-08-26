# throughline-docker

**Docker's Dockerfile best practices** expressed as a
[throughline](https://pypi.org/project/throughline/) **source** — a standalone,
grounded requirements graph that a consuming project composes with
[throughline-compose](https://github.com/rhodium-org/throughline-compose).

This repository holds no code. It is a directory of small YAML items with permanent
UIDs, validated by `tl check`. Consumers import it under a namespace and reference its
rules as `docker:SR-0001`.

## A build / container-concern source

`throughline-docker` is a **build concern** source: it governs how a container image is
built, orthogonal to the language and framework sources you compose alongside it. A CI
pipeline that builds an image with Docker can cite the clauses its Dockerfile satisfies,
the way an application cites ASVS or SLSA clauses.

> **Not the same as `throughline-local-cluster-cicd`.** This source is the *published,
> vendor-neutral* Docker best-practice standard for authoring an image. The separate
> [`throughline-local-cluster-cicd`](https://github.com/rhodium-org/throughline-local-cluster-cicd)
> source is the *house standard* for how one specific estate delivers images to its k3s
> cluster (Flux ImagePolicy, sealed secrets, the shared runner). Compose whichever —
> or both: this one for how the image is built, that one for how it is delivered.

## Status

<!-- tl:count type == 'user_requirement' -->
16
<!-- tl:end --> sections and
<!-- tl:count type == 'system_requirement' -->
33
<!-- tl:end --> practice rules, published to [`docs/spec.md`](docs/spec.md):

- `INT-0001` — the root intent (why the practices exist), `normative: false`.
- Each instruction or topic as a `user_requirement` that `derives_from` the intent.
- Every individual practice as a `system_requirement` that `implements` its section,
  carrying the documentation reference in `attrs.source_ref`.

The counts above are rendered from the live graph by the `tl:count` directive, so they
cannot drift.

## Editions — dated tags

The documentation is a living document. A material revision is cut as a dated tag on
this repo (e.g. `v2026-08`); a consumer pins the ref it wants.

## Composing it

```toml
[[sources]]
namespace = "docker"
url = "https://github.com/rhodium-org/throughline-docker"
ref = "v2026-08"
```

Then reference a rule from your own items:

```yaml
links:
- target: docker:SR-0001      # Docker Dockerfile best practices: create ephemeral containers
  type: satisfies
```

`tl-compose check` resolves the reference; bare `tl check` fails fast and points you at
`tl-compose`.

## Local checks

```sh
pip install throughline
tl check --strict     # the graph must stay sound
tl docs --check       # docs/spec.md must match the graph
```

## Provenance

Docker's Dockerfile best practices are © Docker Inc., licensed Apache-2.0. See
[NOTICE](NOTICE) and https://docs.docker.com/build/building/best-practices/. This
repository is Apache-2.0 for its structure and tooling; the reproduced rule text remains
Docker Inc.'s.
