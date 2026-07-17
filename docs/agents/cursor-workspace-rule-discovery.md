# Cursor workspace rule discovery

Part of the **Cursor agent doc path** — [`00-index.md`](00-index.md) step 7.

## Scope (read this first)

This workflow is **only** for configuring **your Cursor IDE agent environment** in this repository: which `.mdc` rules apply, which optional skills you add, and how you want the agent to behave for **your** team or company.

It is **not** AgentCore product architecture, the platform rule engine, microservices, or admin-console features (`docs/04-rule-engine-orchestration/`, etc.). Nothing here changes runtime product behavior—only what Cursor loads via `ai-toolstack/install.sh` → `.cursor/rules/` and `.cursor/skills/`.

Workspace pack files live under `ai-toolstack/cursor-agent-config/workspace-packs/` alongside the rules/skills install tree.

## Goal

You describe business needs, workflow, and hard limits. The agent walks a **challenge catalog one at a time** and writes a **workspace pack** you activate with `install.sh`.

## How to start

In Cursor chat: "Cursor workspace rule discovery — start" or "تنظیم قوانین workspace کرسر".

Skill: **`cursor-workspace-rule-discovery`**. **One challenge per message.**

## What you provide

1. Workspace profile (who, languages, sovereignty, tooling).
2. Workflow narrative.
3. Hard nos.
4. Per-challenge answers.

Template: [`ai-toolstack/cursor-agent-config/workspace-packs/_template/WORKSPACE-PROFILE.md`](../../ai-toolstack/cursor-agent-config/workspace-packs/_template/WORKSPACE-PROFILE.md).

## What gets generated

`ai-toolstack/cursor-agent-config/workspace-packs/<slug>/` — `WORKSPACE-PROFILE.md`, `choices.yaml`, `workspace-pack.yaml`, `rules/*.mdc`, optional `skills/`, `README.md`. No platform rule-engine YAML.

## Rules vs skills vs MCP Memory

| Need | Mechanism |
| --- | --- |
| Always-on law | `.mdc` in `ai-toolstack/rules/` |
| On-demand procedure | Skill in `ai-toolstack/skills/` |
| Small chat preference | MCP Memory (not a substitute for git rules) |

Reuse `no-cloud-exfiltration.mdc`, `reply-fa-code-docs-en.mdc`, etc. via `inherits_rules` in `workspace-pack.yaml`.

## Activate after review

Merge approved `rules/*.mdc` → `ai-toolstack/rules/` → `./ai-toolstack/install.sh` → Reload Window.

## Challenge catalog

One challenge per turn: why it matters → options → recommendation → your choice.

### A — Context and isolation

| id | Topic |
| --- | --- |
| `A1` | Context limited to this workspace vs other repos |
| `A2` | In-scope paths in monorepo |
| `A3` | dev vs prod terminal assumptions |

### B — Data leaving the machine

| id | Topic |
| --- | --- |
| `B1` | Cloud egress (`no-cloud-exfiltration.mdc`) |
| `B2` | Allowed git/remotes |
| `B3` | External APIs and models |

### C — Working with you

| id | Topic |
| --- | --- |
| `C1` | Continuous vs batch-then-review/docs |
| `C2` | When to invoke review skills |
| `C3` | Ask before destructive git/deploy/IAM |
| `C4` | Commits/PRs only when asked |

### D — Language and docs

| id | Topic |
| --- | --- |
| `D1` | Language for committed files |
| `D2` | Chat language / typography |
| `D3` | When to update docs |

### E — Engineering (code workspaces)

| id | Topic |
| --- | --- |
| `E1` | Testing expectations |
| `E2` | Existing logging/boundary rules |
| `E3` | New dependencies |

### F — Who uses Cursor

| id | Topic |
| --- | --- |
| `F1` | Engineers vs mixed roles |
| `F2` | Features not to suggest casually |

### G — Token / memory

| id | Topic |
| --- | --- |
| `G1` | Git docs vs MCP Memory |
| `G2` | Skills vs new always-on rules |

Record `skipped` in `choices.yaml` when not applicable.

## Rule Card (after each answer)

Challenge id, choice, plain-language rule, draft file paths, risk, dry-run idea.

## Dry-run before approval

2–3 realistic scenarios; list rules/skills that would apply.

## Related

| Doc | Content |
| --- | --- |
| [`00-index.md`](00-index.md) | Reading order |
| [`ai-toolstack/docs/cursor-rules-and-skills.md`](../../ai-toolstack/docs/cursor-rules-and-skills.md) | Rules vs skills |
| [`ai-toolstack/cursor-agent-config/README.md`](../../ai-toolstack/cursor-agent-config/README.md) | Install hub |
