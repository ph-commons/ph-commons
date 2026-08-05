# PH Commons

**Agent-native CLIs for Philippine public data surfaces.**

Government sites, market infrastructure, and other public PH sources — turned into stable, local-first, machine-readable substrates for tool-makers and agents. Not limited to `.gov.ph`. Not consumer apps, not life-safety systems, not regulatory or trading filing tools.

> **Unofficial.** Every CLI in this family is an independent, community-built tool. None are affiliated with, endorsed by, or supported by the operators of the upstream sources (government agencies, exchanges, or private publishers). Data is taken from publicly available pages or feeds; upstream structure can change without notice and break extraction. For official or authoritative data, always consult the source operator directly. **Never rely on these tools for life-safety decisions, regulatory submissions, or trading decisions that require an official feed.**

## Organization

| | |
|--|--|
| GitHub org | [github.com/ph-commons](https://github.com/ph-commons) |
| This hub | [github.com/ph-commons/ph-commons](https://github.com/ph-commons/ph-commons) |
| Charter | [CHARTER.md](./CHARTER.md) |
| License | [Apache-2.0](./LICENSE) |

## Family index

### Reference implementations (full Printing Press contract)

Repos still live under the author's personal account; module paths and install URLs remain `github.com/ngpestelos/...` until an explicit transfer + rewrite.

| Surface | Operator type | CLI | Repo | Notes |
|---------|---------------|-----|------|-------|
| PAGASA weather / cyclones | Government (DOST-PAGASA) | `pagasa-pp-cli` | [ngpestelos/pagasa-pp-cli](https://github.com/ngpestelos/pagasa-pp-cli) | Synopsis, city forecast, storm bulletins, local history |
| PSE Edge equities / disclosures | **Private** (Philippine Stock Exchange) | `pse-edge-pp-cli` | [ngpestelos/pse-edge-pp-cli](https://github.com/ngpestelos/pse-edge-pp-cli) | Quotes, filings, breadth, history, drift |

### Related (not yet under the umbrella)

Skill or prior work exists; adopt only when source matches the charter.

| Surface | Operator type | CLI | Repo |
|---------|---------------|-----|------|
| PH SEC company registry (narrow) | Government (SEC) | `ph-sec-pp-cli` | [ngpestelos/ph-sec-pp-cli](https://github.com/ngpestelos/ph-sec-pp-cli) |
| Metro Manila / Iloilo cinema schedules | Private / commercial listings | `nowshowing-pp-cli` | [ngpestelos/nowshowing-pp-cli](https://github.com/ngpestelos/nowshowing-pp-cli) |
| Vuln desk (CISA KEV + NVD) | Non-PH | `vuln-pp-cli` | [ngpestelos/vuln-pp-cli](https://github.com/ngpestelos/vuln-pp-cli) |

Vuln is a sibling Printing Press CLI, not a PH Commons membership claim.

## What belongs here

A CLI fits PH Commons when it:

1. Wraps a **Philippine public data surface** — government, market infrastructure, or other public PH sources (not government-only; PSE is in scope as private market data)
2. Stays **narrow** — one primary surface or data product
3. Ships the full agent contract (see charter): `--json` / `--agent`, provenance, local state where upstream is latest-only
4. Carries the required unofficial disclaimer (naming the real operator) and **Apache-2.0**
5. Is produced under Printing Press discipline (or kept to the same contract by hand)
6. Has a clear personal/agent demand signal before significant build (product-only)

**Non-goals:** monolith CLI, consumer dashboards, paid hosted service, broad multi-source scrapers without durable local value.

## Technical pattern (Printing Press)

- Go + Cobra CLI
- `--json`, `--agent`, `--select`, `--compact`; auto-JSON when piped
- Companion MCP server (`*-pp-mcp`) — stdio default; optional loopback HTTP
- `doctor` / `which` for health and discovery
- Local SQLite + history / drift where upstream keeps only “latest”
- Typed exit codes for agent self-correction
- Fleet path: goreleaser + one-shot installer + skill files
- Naming: `<slug>-pp-cli`

## README checklist (every CLI)

- Unofficial / not-affiliated banner naming the **actual operator** + link to official site + life-safety / non-official-feed warning
- Install (`go install` and verified one-shot installer)
- Quick start for humans and `--json` / `--agent`
- Commands table
- Local store value (history, drift) when applicable
- Provenance: source + as-of on figures
- License: Apache-2.0
- Link back to this hub / [CHARTER.md](./CHARTER.md)
- MCP paragraph when an MCP binary exists

Reference READMEs: [pagasa-pp-cli](https://github.com/ngpestelos/pagasa-pp-cli), [pse-edge-pp-cli](https://github.com/ngpestelos/pse-edge-pp-cli).

## Roadmap (indicative, own-pace)

1. Keep this hub current as the org front door
2. Affiliate reference CLIs (badges / links) without breaking module paths
3. Transfer under `ph-commons/*` only with a full module-path + install + skill rewrite bundle
4. Demand-gated next seeds (examples, not exclusive): BSP statistics/rates, DOF/Treasury, SEC expansion — plus other PH public surfaces when demand is clear

## Maintainer

Early stage: single maintainer ([@ngpestelos](https://github.com/ngpestelos)). Issues and PRs welcome when they match the charter; drive-by scope expansion will be declined.

## License

Apache License 2.0 — see [LICENSE](./LICENSE).
