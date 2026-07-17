# 06 - Technical Logic Index

## Purpose

This folder contains the technical implementation logic behind the AgentCore documentation tree. The earlier folders explain product scope, architecture, contracts, and phase design. This folder explains how the platform should actually reason, validate, route, persist, retrieve, and fail safely.

## Files

- `01-core-data-model-technical-logic.md` explains entity invariants, write paths, state transitions, idempotency, audit reconstruction, and task decomposition logic.
- `02-memory-context-technical-logic.md` explains memory classification, consolidation, retrieval scoring, prompt cache invalidation, decay, and token budgeting.
- `03-docs-sync-technical-logic.md` explains code indexing, AST anchors, documentation graph linking, drift detection, Bloom filters, and CI merge gates.
- `04-rules-orchestration-technical-logic.md` explains policy evaluation, deterministic pre-checks, LLM judge constraints, escalation, impact traversal, and task routing.
- `05-interoperability-technical-logic.md` explains Universal Agent JSON validation, broker routing, delivery semantics, adapter mapping, tenancy, and dead-letter handling.
- `06-end-to-end-runtime-logic.md` explains how all phases work together in one runtime flow.
- `07-technical-test-strategy.md` defines technical acceptance tests for the full platform.

## Related Graph Implementation Section

- `../07-code-knowledge-graph/06-technical-implementation-logic.md` defines Neo4j, Tree-sitter, hash diffing, embedding, graph upsert, and graph-guided code generation implementation logic.

## Technical Reading Order

1. Read `06-end-to-end-runtime-logic.md` to understand runtime flow.
2. Read files `01` through `05` for phase-level implementation logic.
3. Read `../07-code-knowledge-graph/06-technical-implementation-logic.md` for the graph-backed code understanding pipeline.
4. Read `07-technical-test-strategy.md` to understand how the design should be verified.

## Design Rule

Every automated output must be traceable to input evidence, every model-based judgment must have a deterministic boundary around it, and every risky operation must be either idempotent, reversible, or explicitly approved by a human owner.

## Configurable Weighting Requirement

Memory retrieval, memory decay, graph retrieval, and forgotten-context handling must use versioned weighting profiles instead of hard-coded constants. The detailed logic is documented in `02-memory-context-technical-logic.md` and `../07-code-knowledge-graph/06-technical-implementation-logic.md`.
