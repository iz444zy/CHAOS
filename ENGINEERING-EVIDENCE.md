# CHAOS Engineering Evidence

> Dated, publication-safe measurements and representative proof paths from the private CHAOS source repository.

> [!IMPORTANT]
> The implementation referenced here is not included in this public documentation repository. The internal snapshot identifier and private source paths are retained as provenance labels; they are not publicly resolvable links and do not make this repository an independently verifiable source mirror.

Architecture and implementation posture are governed by the [Component Map](COMPONENT-MAP.md). This document records measurements and bounded proof; it does not redefine architecture or convert source/test presence into product completion.

## Audit basis and measurement method

| Audit property | Value |
|---|---|
| Private-source snapshot | Internal commit identifier `83ab168e21082b8febb6d15699e8de31875f8e86` |
| Repository-wide measurement date | 2026-07-30 |
| Later architecture inspection represented in Component Map | Through 2026-08-03 |
| Count basis | Files tracked by Git at the audited snapshot |
| LOC basis | Physical lines, including comments and blank lines |
| Coverage basis | Executable statements reported by the measured pytest/coverage run |
| Claim boundary | Dated repository evidence, not current-working-tree, performance, packaging, or release-readiness proof |

The audit used repository enumeration, commit-history counts, pytest collection, a measured test run, and coverage reporting. The representative commands below document the method used against the private repository; they are not runnable from this documentation-only showcase.

```powershell
git ls-files
git rev-list 83ab168e21082b8febb6d15699e8de31875f8e86 --count
git rev-list 83ab168e21082b8febb6d15699e8de31875f8e86 --merges --count
python -m pytest --collect-only -q
python -m pytest tests/ -v --tb=short `
  --ignore=tests/test_claude_setup.py `
  --cov=src --cov=scripts `
  --cov-report=term-missing --cov-fail-under=20
```

### Audited repository measurements

| Measure | Audited value |
|---|---:|
| Tracked files | 2,026 |
| Tracked code/configuration files | 1,355 |
| Code/configuration LOC | 235,329 |
| Source Python files | 475 |
| Source Python LOC | 92,204 |
| Test Python files | 459 |
| Test Python LOC | 91,612 |
| Test-to-source Python LOC ratio | 99.4% |
| Collected tests | 6,910 |
| Explicit test modules | 433 |
| Assertion statements | 10,771 |
| Statement coverage | 72.07% |
| Covered executable statements | 35,714 of 49,554 |
| PostgreSQL v2 migration files | 10 |
| Commits reachable from audited private HEAD | 1,759 |
| Merge commits reachable from audited private HEAD | 547 |

These counts describe repository artifacts produced through an agentic development workflow. They are not claims about manually typed lines, individual productivity, runtime performance, or product completion.

### Test-outcome boundary

The retained audit summary records **6,766 passing tests from 6,910 collected**. It does not retain a publication-ready classification of the remaining 144 collected outcomes by failure, skip, expected failure, collection issue, or environment dependency.

Accordingly:

- This document reports the passing count because it exists in the dated audit record.
- It does not characterize all remaining outcomes as failures or as non-failures.
- The passing count is not presented as a clean-suite claim.
- A future updated measurement should publish the complete outcome categories together or omit the partial result breakdown.

The measured run reported 72.07% statement coverage. Coverage and test counts are evidence of verification investment; neither proves that the separate component slices are connected as one released product.

## Repository composition

| Surface | Audited files | Role |
|---|---:|---|
| `src/` | 489 | Product and runtime implementation |
| `tests/` | 462 | Unit, integration, live, container, and contract proof |
| `scripts/` | 126 | Development, audit, generation, migration, and operations tooling |
| `.chaos/` | 187 | Semantic workflow authority, instructions, schemas, and generated runtime material |
| `dev-doc/` | 211 | Architecture, decisions, delivery plans, audits, and reports |
| Docker and Compose surfaces | Not expressed as one directory count | Development and target runtime definitions |

The private repository also contains generated or allowlisted client views for GitHub/Copilot, Codex, and agent-discovery environments. Those surfaces are not treated as separate product engines and are not used here to inflate implementation claims.

## Representative source and test evidence

The paths below are private-repository provenance identifiers. Each test or implementation path supports only the behavior stated; it does not prove unrelated composition.

| Evidence family | Representative private source and verification paths |
|---|---|
| Gateway policy | `src/cw/mcp/server.py`, `src/cw/mcp/gateway_policy.py`, `tests/mcp/test_stage01_gateway_policy.py` |
| Engine control and MES persistence | Engine v2 migrations; `src/cw/engine/services/task_queue.py`, `src/cw/engine/services/provider_chain.py`, `src/cw/mes/runtime.py`, `src/cw/mes/journal.py` |
| Context and Praxis stores | Context and Praxis v2 migrations; `src/cw/context/engine.py`, `payload.py`, `scoring.py`, `budget.py`; `src/cw/praxis/store.py` |
| Hydration and provider evidence | `tests/context/test_stage03_hydration_bundle.py`, `tests/providers/test_stage03_prompt_manifest_provider_payload.py`, `tests/stage03/test_provider_chain_engine_v2_evidence.py` |
| PM and real-agent dispatch | `src/cw/pm/runtime.py`, `tests/stage04/test_stage04_real_agent_dispatch_proof.py` |
| Runtime and provider sessions | `src/cw/runtime/contracts.py`, `src/cw/runtime/lifecycle_supervisor.py`, runtime/provider-session tests |
| MES and KID replay | `src/cw/kid/runtime.py`, `tests/kid/test_mes_projection_replay.py`, `tests/kid/test_mes_reconciliation.py` |
| GitManager | `src/cw/sync/git_manager.py`, `src/cw/sync/git_manager_service.py`, focused sync tests, `tests/stage04/test_git_manager_container_e2e.py` |
| Semantic workflow authority | `.chaos/manifests/`, `.chaos/instructions/`, authority render/validate/drift scripts, and manifest-validation tests |
| Packaging contract | `tests/packaging/test_released_runtime_acceptance.py` as an acceptance contract—not proof of a currently released runtime |

## Test-backed execution traces

| Trace | Evidence path | Observable engineering behavior | Boundary |
|---|---|---|---|
| Context hydration | `tests/context/test_stage03_hydration_bundle.py` | Candidate evidence is retrieved, ranked, trust-filtered, token-budgeted, and retained with hydration-selection provenance. | Does not prove continuous refresh or ongoing session rehydration. |
| Gateway preflight | `tests/mcp/test_stage01_gateway_policy.py` | Registered capabilities pass ordered schema, mode, entitlement, capability, approval, execution-token, and audit-reservation decisions. | Does not prove that every compatibility entrypoint uses the same chain. |
| Task claim and dispatch | `tests/stage04/test_stage04_real_agent_dispatch_proof.py` | Durable Engine task records connect task, provider/session execution, actions, terminal status, and concurrent claim protection. | Does not prove a restart-safe continuously running worker. |
| Projection rebuild | `python scripts/tools/evidence/projection_rebuild.py --check` | Authority documents produce deterministic projection rows, a validation manifest, and replayable hashes. | Validates the targeted projection contract, not the complete runtime catalog. |
| MES and KID replay | `tests/kid/test_mes_projection_replay.py`, `tests/kid/test_mes_reconciliation.py` | A runtime envelope is journaled, cursor-tracked, projected, restarted, and replayed to the same terminal projection. | Does not establish full producer coverage across Engine, sessions, tools, and hydration. |
| Git outcome classification | `tests/stage04/test_git_manager_container_e2e.py` and focused sync tests | Clean histories, scripted resolution, unmerged conflicts, configuration failures, and transient states produce distinct results. | Does not prove autonomous commits, remote publication, or model-assisted repair. |

These are representative bounded traces. The [Showcase](SHOWCASE.md) explains how they are intended to participate in one supervised development workflow without presenting that composition as already complete.

## Audited component inventory

| Component | Files | LOC | Primary responsibility |
|---|---:|---:|---|
| `src/cw/mcp/` | 105 | 20,418 | External gateway, authentication, policy, tools, resources, prompts, and internal clients |
| `src/cw/sync/` | 60 | 13,893 | GitManager, managed clone fleet, merge ingestion, publication groundwork, transport, and reconciliation |
| `src/cw/engine/` | 86 | 13,759 | Operational models, services, migrations, APIs, task authority, provider evidence, and MES persistence |
| `src/cw/pm/` | 27 | 7,514 | Planning, dispatch, task graphs, result collection, and workflow coordination |
| `src/cw/runtime/` | 13 | 6,129 | Runtime contracts, supervision, deployment/read models, and provider sessions |
| `src/cw/context/` | 19 | 4,255 | Retrieval, ranking, budgeting, persistence, hydration, provenance, and projections |
| `src/cw/praxis/` | 15 | 4,109 | Reusable practices, feedback, evaluation, evolution, promotion groundwork, and projections |
| `src/cw/analytics/` | 18 | 3,870 | Benchmarks, instrumentation, tier comparison, quality observations, and scoring |
| `src/cw/kid/` | 11 | 3,451 | Knowledge-integrity jobs, supervision, MES publishing, projections, and reconciliation |
| `src/cw/agents/` | 11 | 2,205 | Agent definitions, process lifecycle, templates, instruction compilation, and orchestration |
| `src/cw/cli/` | 17 | 2,053 | Operator commands, MCP client behavior, status, context, and worktree surfaces |
| `src/cw/mes/` | 12 | 1,827 | Event delivery, journal, consumers, cursors, integrity, dead letters, and replay |
| `src/cw/ingestor/` | 19 | 1,707 | Repository ingestion, classification, chunking, parsing, and source processing |
| `src/cw/providers/` | 15 | 1,555 | Provider contracts, adapters, sessions, registry behavior, and command execution |
| `src/cw/core/` | 11 | 1,498 | Configuration, logging, exceptions, shutdown, circuit protection, and shared primitives |

Smaller implementation families include installer, events, session, terminal, prompt, bundle, generic file support, and a tested but currently disconnected quantization library. Their presence is not used to claim product integration.

## Selected architecture files

| Private source path | LOC | Role |
|---|---:|---|
| `src/cw/mcp/server.py` | 1,046 | Gateway composition, lifecycle, and capability registration |
| `src/cw/mcp/gateway_policy.py` | 325 | Ordered request preflight and policy decisions |
| `src/cw/engine/services/task_queue.py` | 495 | Durable task creation, claim, transition, and result behavior |
| `src/cw/engine/services/provider_chain.py` | 777 | Provider, projection, import, action, and KID evidence |
| `src/cw/context/engine.py` | 373 | Context retrieval and hydration orchestration |
| `src/cw/context/payload.py` | 622 | Hydration bundles, provenance, items, and token budgets |
| `src/cw/runtime/contracts.py` | 565 | Shared runtime event, lifecycle, and causality contracts |
| `src/cw/runtime/lifecycle_supervisor.py` | 418 | Managed service startup, health, and shutdown behavior |
| `src/cw/kid/runtime.py` | 470 | Knowledge-integrity task lifecycle and supervision |
| `src/cw/sync/git_manager.py` | 675 | Managed Git runtime, lifecycle, reconciliation, and outcomes |

These files were selected because they represent important system boundaries. File size alone is not evidence of correctness or architectural quality.

## Test investment

| Test area | Files | LOC |
|---|---:|---:|
| MCP | 89 | 22,936 |
| Engine | 57 | 13,001 |
| Cross-cutting root tests | 59 | 11,457 |
| Sync and Git | 41 | 11,436 |
| PM | 23 | 4,177 |
| CLI | 19 | 3,635 |
| Integration | 17 | 3,051 |
| Stage 04 runtime proof | 12 | 2,809 |
| Runtime | 10 | 2,316 |
| Context | 17 | 2,165 |
| KID and MES | 15 | 1,802 |
| Ingestor | 10 | 1,769 |
| Analytics | 9 | 1,634 |
| Stage 03 store/provider proof | 10 | 1,491 |

The measured coverage run completed in approximately 8 minutes 15 seconds. The repository configuration recorded a 70% report threshold, and the measured 72.07% result exceeded that value. This remains a dated audit observation, not a claim that every current branch or environment passes the same gate.

## Public history methodology

The public repository history is a sanitized, non-code reconstruction of selected development chronology from the private source repository.

- Public history may preserve milestone order, engineering intent, component scope, and verification outcomes.
- Public commit hashes, PR identifiers, metadata, descriptions, and diffs may differ from the private originals.
- Reconstructed history does not independently prove that the private implementation exists or that a described capability was connected.
- Repository-scale commit and merge counts above refer to the audited private snapshot, not the number of public reconstruction events.

The history is intended to show how architecture and implementation evolved—not to simulate a public source history or imply manually authored activity.

## Publication-safe evidence boundary

Public-facing evidence is limited to sanitized architecture descriptions, bounded measurements, representative private paths, and scoped behavior summaries. Publication must exclude:

- Credentials, tokens, secrets, and private service addresses.
- Raw logs, provider payloads, transcripts, or repository bodies.
- Personal filesystem paths or internal account information.
- Private branch names and unreviewed author metadata.
- Raw comments, review threads, and private PR-body text.
- Security-sensitive operational details that are unnecessary to establish the engineering claim.

The standard for this showcase is conservative: measured implementation is reported as measured implementation, bounded proof as bounded proof, connected behavior only when connected proof exists, and release readiness only after packaged lifecycle acceptance.
