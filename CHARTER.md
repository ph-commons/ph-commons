# PH Commons Charter

**Status:** Adopted for org stand-up 20260805. Scope corrected same day: not government-only.

## Name

**PH Commons** — GitHub organization [`ph-commons`](https://github.com/ph-commons) (display name: Philippine Commons).

## Purpose

Agent-native CLIs that turn **Philippine public data surfaces** into stable, local-first, machine-readable substrates for tools and agents.

Surfaces may be:

- **Government** (e.g. PAGASA, SEC, BSP)
- **Private / market** (e.g. Philippine Stock Exchange / PSE Edge)
- **Other public PH sources** when they meet membership rules

Government data is common in the family; it is **not** a scope boundary. PSE is private and in scope.

## Audience contract

**Primary:** tool-makers and agent builders who need reliable access to Philippine public data so agents can work with bureaucracy, markets, and related PH systems.

**Not for:** consumer dashboards, end-user product UIs, life-safety systems, regulatory filing, or use as a substitute for official/vendor market data feeds where those are required.

Every CLI states the unofficial contract up front and names the real upstream operator.

## Scope rules

- One narrow surface or product per CLI at the start (depth before breadth)
- Operator may be government or private; the test is **public PH data + agent value**, not ownership form
- Server-rendered HTML extraction is acceptable when no stable public API or tokenless JSON exists
- Local SQLite is required when upstream is latest-only, so history, drift, and query are possible
- Every data row or response carries provenance (source + as-of)
- Strong “Unofficial. Not affiliated…” disclaimer naming the operator, plus life-safety / non-official-feed warnings in every README
- Apache-2.0 license

**Non-goals (for now):** monolith CLI, consumer product, paid hosted service, unbounded multi-source aggregator.

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

## Membership / inclusion rules

A CLI belongs under PH Commons if it:

1. Wraps a **Philippine public data surface** (government, private market infrastructure, or other public PH source — not government-only)
2. Is narrow (one primary surface or data product)
3. Follows the full agent contract (JSON/agent/MCP + provenance + local state where needed)
4. Carries required disclaimer language naming the operator, and Apache-2.0
5. Is produced under Printing Press discipline (or manually kept to the same contract)
6. Respects product-only trajectory: clear personal/agent need before significant build

One-off scripts, broad scrapers without durable local value, non-PH sources (unless explicitly sibling-listed), and consumer-facing apps stay outside.

## README template obligations

Every CLI README must include (order flexible):

- Strong unofficial / not-affiliated banner naming the operator, link to official site, life-safety / non-official-feed warning
- Install section (`go install` and verified one-shot curl installer)
- Quick-start examples for humans and `--json` / `--agent`
- Commands table
- Local store value (history, drift) when upstream does not keep history
- Provenance note: figures carry source + as-of
- License line: Apache-2.0
- Link to PH Commons hub / this charter
- MCP server paragraph when present

## Mandatory disclaimer language (adapt per surface)

> **Unofficial.** This is an independent, community-built tool **not affiliated with, endorsed by, or supported by** [Operator]. It uses publicly available data; upstream structure can change and break extraction without notice. For official data, consult [official site] directly — **never rely on this tool for life-safety decisions, regulatory submissions, or decisions that require an official or licensed feed.**

## Governance (early stage)

- Single author / maintainer
- Charter changes by maintainer judgment; record material changes in this file
- Product-only: no sell-hours targets; no hard “fan count” goals

## Transfer policy

Do not move existing personal repos into this org without a simultaneous rewrite of:

- `go.mod` module path → `github.com/ph-commons/<cli>`
- install scripts, README install lines, skills, goreleaser, fleet pins

Partial transfer (repo under org, module path still personal) is discouraged except as a short, documented interim.

## Changelog

- **20260805** — Org stand-up; hub published
- **20260805** — Scope correction: not restricted to government data; PSE (private) explicitly in scope
