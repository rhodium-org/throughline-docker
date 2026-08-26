# Docker Dockerfile best practices — throughline source

This document is **generated from the graph** by `tl docs`; `tl docs --check` gates it in CI. The prose headings are hand-owned — everything between `tl:*` markers is injected from the YAML items, so the published spec can never drift from the graph.

This source re-expresses **Docker's Dockerfile best practices** as a grounded IDD graph: each instruction or topic is a `user_requirement`, and every individual practice is a `system_requirement` that `implements` its section. The documentation reference lives in `attrs.source_ref`; the throughline UIDs are this source's own and immutable — a consumer cites a rule as `docker:SR-0001`, never by section name.

It carries
<!-- tl:count type == 'user_requirement' -->
16
<!-- tl:end --> sections and
<!-- tl:count type == 'system_requirement' -->
33
<!-- tl:end --> practice rules.

## Purpose

<!-- tl:item INT-0001 -->
**INT-0001 — Container images are built to be reproducible, small and maintainable** — `intent`, status `approved`

> Docker's Dockerfile best practices exist so that container images across a large estate are built the same way: reproducible, small, cacheable and readable, with each container owning a single concern and each Dockerfile instruction used for its intended purpose, so that any engineer can read, rebuild and change an image they did not author and a CI pipeline can build it identically.

**source_ref**: Docker Dockerfile best practices
<!-- tl:end -->

## General Guidelines

<!-- tl:item UR-0001 -->
**UR-0001 — General Guidelines** — `user_requirement`, status `approved`

> Rules governing the overall design of an image and its Dockerfile.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: General Guidelines
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: General Guidelines') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0001 | system_requirement | approved | Create ephemeral containers |
| SR-0002 | system_requirement | approved | Decouple applications into separate containers |
| SR-0003 | system_requirement | approved | Sort multi-line arguments |
<!-- tl:end -->

## Build Context and dockerignore

<!-- tl:item UR-0002 -->
**UR-0002 — Build Context and dockerignore** — `user_requirement`, status `approved`

> Rules governing keeping the build context small and excluding files.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: Build Context and dockerignore
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: Build Context and dockerignore') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0004 | system_requirement | approved | Keep the build context small |
| SR-0005 | system_requirement | approved | Exclude files with a dockerignore file |
<!-- tl:end -->

## Multi-stage Builds

<!-- tl:item UR-0003 -->
**UR-0003 — Multi-stage Builds** — `user_requirement`, status `approved`

> Rules governing using multiple build stages to shrink the final image.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: Multi-stage Builds
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: Multi-stage Builds') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0006 | system_requirement | approved | Use multi-stage builds |
| SR-0007 | system_requirement | approved | Copy only the artefacts you need |
<!-- tl:end -->

## Minimize the Number of Layers

<!-- tl:item UR-0004 -->
**UR-0004 — Minimize the Number of Layers** — `user_requirement`, status `approved`

> Rules governing which instructions create layers and how to keep them few.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: Minimize the Number of Layers
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: Minimize the Number of Layers') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0008 | system_requirement | approved | Know which instructions create layers |
| SR-0009 | system_requirement | approved | Leverage the build cache |
<!-- tl:end -->

## FROM

<!-- tl:item UR-0005 -->
**UR-0005 — FROM** — `user_requirement`, status `approved`

> Rules governing the choice of base image.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: FROM
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: FROM') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0010 | system_requirement | approved | Use official and verified base images |
| SR-0011 | system_requirement | approved | Prefer a minimal base image |
| SR-0012 | system_requirement | approved | Pin the base image version |
<!-- tl:end -->

## LABEL

<!-- tl:item UR-0006 -->
**UR-0006 — LABEL** — `user_requirement`, status `approved`

> Rules governing image metadata.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: LABEL
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: LABEL') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0013 | system_requirement | approved | Add metadata with LABEL |
<!-- tl:end -->

## RUN

<!-- tl:item UR-0007 -->
**UR-0007 — RUN** — `user_requirement`, status `approved`

> Rules governing RUN instructions, package installation and cache management.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: RUN
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: RUN') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0014 | system_requirement | approved | Split long RUN statements across lines |
| SR-0015 | system_requirement | approved | Combine apt-get update and install |
| SR-0016 | system_requirement | approved | Pin installed package versions |
| SR-0017 | system_requirement | approved | Clean up the package cache in the same layer |
| SR-0018 | system_requirement | approved | Set pipefail before piped commands |
<!-- tl:end -->

## CMD

<!-- tl:item UR-0008 -->
**UR-0008 — CMD** — `user_requirement`, status `approved`

> Rules governing the default command of an image.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: CMD
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: CMD') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0019 | system_requirement | approved | Use the exec form of CMD |
| SR-0020 | system_requirement | approved | Use CMD for default arguments |
<!-- tl:end -->

## EXPOSE

<!-- tl:item UR-0009 -->
**UR-0009 — EXPOSE** — `user_requirement`, status `approved`

> Rules governing declaring listening ports.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: EXPOSE
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: EXPOSE') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0021 | system_requirement | approved | Declare listening ports with EXPOSE |
<!-- tl:end -->

## ENV

<!-- tl:item UR-0010 -->
**UR-0010 — ENV** — `user_requirement`, status `approved`

> Rules governing environment variables.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: ENV
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: ENV') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0022 | system_requirement | approved | Use ENV for PATH and required variables |
| SR-0023 | system_requirement | approved | Unset build-only variables in the same layer |
<!-- tl:end -->

## ADD or COPY

<!-- tl:item UR-0011 -->
**UR-0011 — ADD or COPY** — `user_requirement`, status `approved`

> Rules governing copying files into the image.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: ADD or COPY
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: ADD or COPY') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0024 | system_requirement | approved | Prefer COPY over ADD |
| SR-0025 | system_requirement | approved | Use ADD only for tar extraction |
<!-- tl:end -->

## ENTRYPOINT

<!-- tl:item UR-0012 -->
**UR-0012 — ENTRYPOINT** — `user_requirement`, status `approved`

> Rules governing the image's main command and signal handling.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: ENTRYPOINT
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: ENTRYPOINT') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0026 | system_requirement | approved | Set the main command with ENTRYPOINT |
| SR-0027 | system_requirement | approved | Use an exec helper script for PID 1 |
<!-- tl:end -->

## VOLUME

<!-- tl:item UR-0013 -->
**UR-0013 — VOLUME** — `user_requirement`, status `approved`

> Rules governing mutable and user-serviceable data.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: VOLUME
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: VOLUME') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0028 | system_requirement | approved | Expose mutable data with VOLUME |
<!-- tl:end -->

## USER

<!-- tl:item UR-0014 -->
**UR-0014 — USER** — `user_requirement`, status `approved`

> Rules governing running as a non-root user.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: USER
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: USER') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0029 | system_requirement | approved | Run as a non-root user |
| SR-0030 | system_requirement | approved | Avoid installing or using sudo |
| SR-0031 | system_requirement | approved | Avoid switching USER back and forth |
<!-- tl:end -->

## WORKDIR

<!-- tl:item UR-0015 -->
**UR-0015 — WORKDIR** — `user_requirement`, status `approved`

> Rules governing the working directory.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: WORKDIR
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: WORKDIR') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0032 | system_requirement | approved | Use absolute paths for WORKDIR |
<!-- tl:end -->

## ONBUILD

<!-- tl:item UR-0016 -->
**UR-0016 — ONBUILD** — `user_requirement`, status `approved`

> Rules governing triggers for downstream builds.

*Derives from:* INT-0001

**source_ref**: Docker Dockerfile best practices: ONBUILD
<!-- tl:end -->

<!-- tl:table type == 'system_requirement' and attrs.get('source_ref', '').startswith('Docker Dockerfile best practices: ONBUILD') -->
| UID | Type | Status | Title |
|---|---|---|---|
| SR-0033 | system_requirement | approved | Use ONBUILD for downstream builds |
<!-- tl:end -->

