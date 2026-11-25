# Project brief

## Purpose

OpenMettle is a clean-room, open-source self-hosted AI platform designed to give people and organisations a capable, private, multi-user AI experience on hardware they control. It unifies server-authoritative Rust backend services, PostgreSQL 18 persistence, curated local model serving, reviewed tools, scoped knowledge and memory, a planned Flutter web and mobile client, Kubernetes/Helm packaging, and local IDE coding agent workflows.

The ambition is to bring the polish, reliability, and guardrails expected from leading AI products to self-hosted deployments — without surrendering private data, hiding policy enforcement in the browser, or overclaiming unproven hardware or compliance guarantees.

## Audience and editions

OpenMettle grows out of home-lab roots into one shared multi-user platform across three environments:

- **Home & Household (Open Source — In Active Build):** Home-lab builders and families sharing local hardware. Emphasises approachable setup, automatic family onboarding with one-time invitation codes, private per-person chat history, and built-in quiet-hour and study-hour schedules.
- **Education (Planned Offering):** Schools, labs, and universities needing curriculum-aligned study hours, curated model allowlists, OIDC/SSO directory group sync with fail-closed enforcement, strict per-student workspace isolation, and institutional data residency.
- **Small Business & Commercial (Planned Offering):** Teams and small businesses wanting private personal and project workspaces, human-in-the-loop tool approvals, transactional token/cost/storage/GPU quota governance, retention and audit trails, and zero proprietary data sent to public AI clouds by default.

Education and Small Business are planned offerings building on the open-source v1 core. No release dates or formal third-party compliance certifications are claimed.

## Clean-room v1 architecture and delivery order

The accepted [v1 architecture baseline](https://github.com/OpenMettle/openmettle-core/blob/main/ARCHITECTURE-v1.md) (16 November 2026) and [decision records (ADRs 0001–0044)](https://github.com/OpenMettle/openmettle-core/blob/main/DECISIONS.md) define a fresh, clean-room implementation rather than a fork-port of an existing web UI:

1. **Step 1 — Backend & APIs (`openmettle-core`, `openmettle-deploy`):** Separate Rust API (`openmettle-api`), run-worker (`openmettle-worker`), inference proxy (`openmettle-gateway`), and schema migrator (`openmettle-migrate`) processes over PostgreSQL 18, with canonical OpenAPI 3.2 contracts, replayable SSE event streams, and CPU-only core Helm packaging.
2. **Step 2 — Web & mobile client (`openmettle-app`):** Flutter presentation layer consuming the versioned core APIs and replayable event cursors. Permissions, approvals, quotas, and run state remain strictly server-authoritative.
3. **Curated serving & local IDE workflows (`openmettle-serving`, `OpenMettle/sglang`, `openmettle-acp`):** Maintained AMD-first ROCm/RDNA4 SGLang serving with HIP virtual-memory Elastic KV Cache under fenced PostgreSQL capacity grants (`ADR 0042`), alongside the existing local ACP coding agent and its planned v1 backend adapter.

## Security, privacy and governance direction

Privacy and safety are treated as architectural boundaries rather than UI conventions:

- **Private-by-default multi-user isolation (`ADR 0027`, `ADR 0044`):** Every conversation, artifact, and memory record belongs privately to its creator — even inside shared projects and against account administrators — until shared via revocable grants. OpenMettle's own inference proxy strips caller-supplied SGLang cache/routing keys and injects scoped cryptographic `cache_salt`s so upstream KV prefix caches do not cross user or private-conversation boundaries on qualified backends.
- **Four-point family and study schedules (`ADR 0044`):** IANA timezone- and DST-accurate quiet hours, study-hour model allowlists, and model switches evaluated by one PostgreSQL policy function across API admission, worker recheck, database round handoff, and proxy dispatch.
- **Least-privilege database & identity boundaries (`ADR 0003`, `ADR 0022`, `ADR 0030`, `ADR 0044`):** Four disjoint non-DDL, non-`DELETE` PostgreSQL 18 runtime roles (`openmettle_api`, `openmettle_issuance`, `openmettle_worker`, `openmettle_gateway`), OIDC/SSO with local operator identity approval gates, and single-use per-round inference bearers whose plaintext never touches PostgreSQL.
- **Approvals, quotas, retention & value-free telemetry (`ADR 0024`, `ADR 0028`, `ADR 0035`, `ADR 0040`, `ADR 0041`):** SHA-256-bound human-in-the-loop tool approvals (plus policy-gated opt-in YOLO), exact-integer transactional quotas across storage/tokens/cost/device slots, configurable soft-delete grace windows with operator holds, an append-only SHA-256 hash-chained deletion journal and fail-closed restore barrier, and default-deny telemetry that never logs prompts, credentials, or user/scope identifiers (OTLP export off by default).

A self-hosted component alone does not establish the privacy properties of the whole deployment. Optional external providers and tools require explicit configuration and clear disclosure of what leaves the installation.

## Hardware direction

AMD hardware and the ROCm ecosystem are the primary development, optimisation, and validation target — including curated SGLang work on RDNA4 (Elastic KV Cache, FP8 attention caching, MXFP4 quantization, and speculative decoding). The Rust core remains strictly GPU-independent: it deploys on CPU alone, treats managed GPU packages as opt-in Kubernetes DRA profiles, supports user-configured external compatible backends, and leaves clean adapter boundaries for planned qualified NVIDIA and other device profiles. Compatibility and performance claims are documented with reproducible evidence per qualified profile.

## Principles

1. Keep backend contracts, security boundaries, and recovery ahead of presentation polish.
2. Enforce isolation, policy, approvals, and quotas server-side — never as client-only hints.
3. Keep advanced options available without making them prerequisites for ordinary use.
4. Prefer durable, replayable execution over fragile request-bound state.
5. Measure output quality, isolation, and failure recovery alongside throughput and latency.
6. Keep configuration portable and site-specific values outside tracked source trees.
7. Preserve upstream licenses, copyright notices, and provenance across all curated dependencies.

## Delivery milestones

| Milestone | Evidence of completion |
| --- | --- |
| Architecture & repository foundation | Accepted [v1 architecture baseline](https://github.com/OpenMettle/openmettle-core/blob/main/ARCHITECTURE-v1.md), repository boundaries, and public community/brand standards established |
| Step 1 — Core backend & contracts | Rust API, worker, migrator, and inference proxy pass PostgreSQL 18 integration, authorization, quota, retention, and contract conformance checks |
| Core Kubernetes packaging | CPU-only `openmettle-core` Helm chart passes render/schema validation, NetworkPolicy enforcement, and `kind` install/upgrade smoke checks |
| Managed inference & Elastic KV qualification | Curated SGLang profile qualifies live streaming, prefix-cache `cache_salt` isolation, Elastic KV shrink/reclaim, and fenced GPU capacity grants |
| Step 2 — Flutter client & ACP v1 adapter | Flutter web/mobile app and `openmettle-acp` consume versioned v1 APIs, replayable SSE cursors, branches, and approval workflows |
| First v1 preview | Versioned artifacts, backup/restore verification with deletion-journal replay, documented limitations, and recovery guides published |

Milestones are planning targets, not announcements of available features. No release dates are committed.
