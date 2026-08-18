# PH Commons Charter

**Status:** Live 20260805. Scope: **gov + others** (any Philippine-based CLI that meets the contract), not government-only.

## Name

**PH Commons** — GitHub organization [`ph-commons`](https://github.com/ph-commons) (display name: Philippine Commons).

## Purpose

Home for **agent-native, Philippine-based CLIs**: government data tools and every other PH-scoped CLI in the family (markets, commercial listings, civic surfaces, etc.).

Examples already in the trajectory:

- Government: PAGASA, SEC, future BSP-class tools
- Private market: PSE Edge
- Commercial / other PH: nowshowing (cinema) — **in org** as [`ph-commons/nowshowing-pp-cli`](https://github.com/ph-commons/nowshowing-pp-cli) (20260810)
- Any further Philippine-based CLI that earns a place under the rules below

## Audience contract

**Primary:** tool-makers and agent builders equipping agents for Philippine context (bureaucracy, markets, daily PH surfaces).

**Not for:** treating these CLIs as official feeds, life-safety systems, regulatory filing, or a consumer product line under this brand.

Every CLI states the unofficial contract up front and names the real upstream operator.

## Scope rules

- **Boundary = Philippine-based**, not “government only” and not “public sector data only”
- **gov + others** — private exchange data, commercial listings (e.g. cinema), and other PH surfaces are in scope when they meet membership rules
- One narrow surface or product per CLI (depth before breadth)
- Server-rendered HTML extraction OK when no stable public API / tokenless JSON exists
- Local SQLite when upstream is latest-only
- Provenance on every figure (source + as-of)
- Disclaimer names the operator; Apache-2.0

**Non-goals:** monolith; dumping non-PH tools here; consumer apps; paid hosted service.

## Technical pattern (Printing Press contract)

- Go + Cobra; `--json` / `--agent` / `--select` / `--compact`; auto-JSON when piped
- `*-pp-mcp` companion; `doctor` / `which`
- SQLite history/drift when valuable; typed exit codes
- Fleet: goreleaser + installer + skill files
- Naming: `<slug>-pp-cli`

## Repo layout

| Kind | Location | Notes |
|------|----------|-------|
| Org hub | `ph-commons/ph-commons` | Index + charter |
| Today’s reference CLIs | `ph-commons/pagasa-pp-cli`, `ph-commons/pse-edge-pp-cli` | In-org (PSE 20260818) |
| In org | `nowshowing` 20260810 · `pagasa`/`ph-sec` 20260812 · `pse-edge` 20260818 | Full module rewrite + patch tag |
| Eventually | `ph-sec-pp-cli`, other PH-based CLIs | Move when source + contract ready |
| Preferred home for family | `ph-commons/<slug>-pp-cli` | New and transferred work |

## Membership / inclusion rules

A CLI belongs under PH Commons if it:

1. Is **Philippine-based** (PH government, PH private/market, PH commercial/civic, or clearly PH-scoped)
2. Is narrow (one primary surface or product)
3. Follows the full agent contract
4. Carries disclaimer + Apache-2.0
5. Follows Printing Press discipline (or equivalent by hand)
6. Has clear personal/agent demand before significant build

Non-PH CLIs (e.g. generic vuln desk) stay outside even if they share the generator.

## README template obligations

- Unofficial banner naming operator + official link + warnings
- Install (`go install` + one-shot installer)
- Human and agent quick start; commands table
- Local store value when relevant; provenance; Apache-2.0
- Link to hub / this charter; MCP paragraph when present

## Mandatory disclaimer language (adapt per surface)

> **Unofficial.** This is an independent, community-built tool **not affiliated with, endorsed by, or supported by** [Operator]. Upstream data and structure can change without notice. For official data, consult [official site] directly — **never rely on this tool for life-safety decisions, regulatory submissions, or decisions that require an official or licensed feed.**

## Governance (early stage)

- Single maintainer
- Own-pace; product-only (no sell-hours / fan-count targets)
- Material charter changes recorded in Changelog below

## Transfer policy

No repo move into the org without simultaneous rewrite of module path (`github.com/ph-commons/<cli>`), install scripts, README, skills, goreleaser, and fleet pins.

## Changelog

- **20260805** — Org + hub stand-up
- **20260805** — Not government-only; PSE (private) in scope
- **20260805** — Scope restated **gov + others**: any Philippine-based CLI (including nowshowing and future PH CLIs) may land here eventually
- **20260810** — `nowshowing-pp-cli` transferred to `ph-commons/nowshowing-pp-cli` with full module-path + install + skill rewrite
- **20260818** — `pse-edge-pp-cli` transferred; module rewrite; **v0.1.5**
