# PH Commons Charter

**Status:** Adopted for org stand-up 20260805. Own-pace.

## Name

**PH Commons** — GitHub organization [`ph-commons`](https://github.com/ph-commons) (display name: Philippine Commons).

## Purpose

Agent-native CLIs that turn Philippine government public data surfaces into stable, local-first, machine-readable substrates for tools and agents.

## Audience contract

**Primary:** tool-makers and agent builders who need reliable access to `.gov.ph` (and closely related public) data so agents can navigate Philippine bureaucracy.

**Not for:** consumer dashboards, end-user product UIs, life-safety systems, or regulatory filing.

Every CLI states the unofficial contract up front.

## Scope rules

- One narrow surface or department per CLI at the start (depth before breadth)
- Server-rendered HTML extraction is acceptable when no stable public API or tokenless JSON exists
- Local SQLite is required when upstream is latest-only, so history, drift, and query are possible
- Every data row or response carries provenance (source + as-of)
- Strong “Unofficial. Not affiliated…” disclaimer plus life-safety / regulatory warning in every README
- Apache-2.0 license

**Non-goals (for now):** monolith CLI, consumer product, paid hosted service, broad multi-department aggregator.

## Technical pattern (Printing Press contract)

- Go + Cobra CLI
- `--json`, `--agent`, `--select`, `--compact` on commands; auto-JSON when piped
- Companion MCP server binary (`*-pp-mcp`): stdio default + optional loopback HTTP
- `doctor` and `which` for health and discovery
- Local durable store (SQLite) + history / drift when valuable
- Typed exit codes for agent self-correction
- Fleet distribution via goreleaser, one-shot installer, and agent skill files
- `AGENTS.md` / `SKILL.md` for agent consumers
- CLI naming: `<slug>-pp-cli`

## Repo layout

| Kind | Location | Notes |
|------|----------|-------|
| Org hub | `ph-commons/ph-commons` | This repo — index, charter, templates |
| Reference CLIs (today) | `ngpestelos/pagasa-pp-cli`, `ngpestelos/pse-edge-pp-cli` | Personal until transfer + module rewrite |
| Future family CLIs | `ph-commons/<slug>-pp-cli` | Preferred home for new work |
| Optional docs | `ph-commons/ph-commons-docs` | Only if hub outgrows a single README |

## Membership / inclusion rules

A CLI belongs under PH Commons if it:

1. Wraps a Philippine government or closely related public data surface
2. Is narrow (one primary surface or data product)
3. Follows the full agent contract (JSON/agent/MCP + provenance + local state where needed)
4. Carries required disclaimer language and Apache-2.0
5. Is produced under Printing Press discipline (or manually kept to the same contract)
6. Respects product-only trajectory: clear personal/agent need before significant build

One-off scripts, broad scrapers without durable local value, and consumer-facing apps stay outside.

## README template obligations

Every CLI README must include (order flexible):

- Strong unofficial / not-affiliated banner, link to official site, explicit life-safety warning
- Install section (`go install` and verified one-shot curl installer)
- Quick-start examples for humans and `--json` / `--agent`
- Commands table
- Local store value (history, drift) when upstream does not keep history
- Provenance note: figures carry source + as-of
- License line: Apache-2.0
- Link to PH Commons hub / this charter
- MCP server paragraph when present

## Mandatory disclaimer language (adapt per surface)

> **Unofficial.** This is an independent, community-built tool **not affiliated with, endorsed by, or supported by** [Official Entity]. It extracts publicly available data; upstream structure can change and break extraction without notice. For official data, consult [official site] directly — **never rely on this tool for life-safety decisions or regulatory submissions.**

## Governance (early stage)

- Single author / maintainer
- Charter changes by maintainer judgment; record material changes in this file
- Product-only: no sell-hours targets; no hard “fan count” goals
- Fans (if any) = agents and tool-makers who spend attention and authority on the CLIs

## Transfer policy

Do not move existing personal repos into this org without a simultaneous rewrite of:

- `go.mod` module path → `github.com/ph-commons/<cli>`
- install scripts, README install lines, skills, goreleaser, fleet pins

Partial transfer (repo under org, module path still personal) is discouraged except as a short, documented interim.
