# PH Commons

**Agent-native CLIs for the Philippines** — government sources and everything else that is Philippine-based.

PAGASA, PSE, cinema schedules, registries, markets, local services: one org for the family. Not limited to `.gov.ph`. Not a monolith — each CLI stays a narrow repo.

> **Unofficial.** Every CLI is an independent, community-built tool. None are affiliated with, endorsed by, or supported by the operators of their upstream sources (government agencies, exchanges, commercial sites, or other publishers). Upstream structure can change without notice. For official or authoritative data, consult the source directly. **Never rely on these tools for life-safety decisions, regulatory submissions, or decisions that require an official or licensed feed.**

## Organization

| | |
|--|--|
| GitHub org | [github.com/ph-commons](https://github.com/ph-commons) |
| This hub | [github.com/ph-commons/ph-commons](https://github.com/ph-commons/ph-commons) |
| Charter | [CHARTER.md](./CHARTER.md) |
| License | [Apache-2.0](./LICENSE) |

## Family index

### In family now (reference implementations)

<<<<<<< Updated upstream
Full Printing Press contract. `nowshowing-pp-cli`, `pagasa-pp-cli`, and `ph-sec-pp-cli` live under this org (PAGASA and PH SEC transferred 2026-08-12; module-path rewrite still pending, so `go install` continues to resolve via the old `ngpestelos/*` path until that follow-up lands). PSE remains personal until its transfer + module rewrite.
=======
Full Printing Press contract. PAGASA, PSE Edge, nowshowing, and PH SEC live under this org.
>>>>>>> Stashed changes

| Surface | Kind | CLI | Repo |
|---------|------|-----|------|
| PAGASA weather / cyclones | Government | `pagasa-pp-cli` | [ph-commons/pagasa-pp-cli](https://github.com/ph-commons/pagasa-pp-cli) |
<<<<<<< Updated upstream
| PH SEC registry (narrow) | Government | `ph-sec-pp-cli` | [ph-commons/ph-sec-pp-cli](https://github.com/ph-commons/ph-sec-pp-cli) |
| PSE Edge equities / disclosures | Private market (PSE) | `pse-edge-pp-cli` | [ngpestelos/pse-edge-pp-cli](https://github.com/ngpestelos/pse-edge-pp-cli) |
=======
| PSE Edge equities / disclosures | Private market (PSE) | `pse-edge-pp-cli` | [ph-commons/pse-edge-pp-cli](https://github.com/ph-commons/pse-edge-pp-cli) |
>>>>>>> Stashed changes
| Metro Manila / Iloilo cinema | Commercial / listings | `nowshowing-pp-cli` | [ph-commons/nowshowing-pp-cli](https://github.com/ph-commons/nowshowing-pp-cli) |

### Heading here eventually

Nothing currently queued. Any other **Philippine-based** CLI that meets the charter (narrow surface, agent contract, disclaimer, Apache-2.0) is a candidate for this org over time.

### Sibling only (not PH Commons membership)

| CLI | Why listed |
|-----|------------|
| [vuln-pp-cli](https://github.com/ngpestelos/vuln-pp-cli) | Same Printing Press pattern; not a Philippine surface |

## What belongs here

**gov + others.** A CLI fits when it is:

1. **Philippine-based** — PH government, PH private/market, PH commercial or civic surface, or otherwise clearly PH-scoped (not “any CLI we wrote”)
2. **Narrow** — one primary surface or product
3. Full agent contract (see charter): `--json` / `--agent`, provenance, local state where upstream is latest-only
4. Unofficial disclaimer naming the real operator + **Apache-2.0**
5. Printing Press discipline (or hand-kept to the same contract)
6. Clear personal/agent demand before significant build (product-only)

**Non-goals:** monolith CLI, consumer product SKU under this brand, paid hosted service, dumping unrelated non-PH tools into the org.

## Technical pattern (Printing Press)

- Go + Cobra CLI
- `--json`, `--agent`, `--select`, `--compact`; auto-JSON when piped
- Companion MCP server (`*-pp-mcp`) — stdio default; optional loopback HTTP
- `doctor` / `which`
- Local SQLite + history / drift where upstream is latest-only
- Typed exit codes; fleet install path; naming `<slug>-pp-cli`

## README checklist (every CLI)

- Unofficial banner naming the operator + official link + life-safety / non-official-feed warning
- Install (`go install` + verified one-shot installer)
- Human and `--json` / `--agent` quick start
- Commands table; local store value when relevant
- Provenance (source + as-of); Apache-2.0; link to this hub
- MCP paragraph when present

## Roadmap (own-pace)

1. Hub stays the front door
2. Affiliate personal repos (badges/links) without breaking module paths
3. Transfer under `ph-commons/*` only with full module-path + install + skill rewrite
4. Fold in remaining PH-based CLIs when ready (**nowshowing** in-org 20260810; **pagasa**, **ph-sec** in-org 20260812, module-path rewrite pending)
5. New seeds when demand is clear (e.g. BSP and other high-value surfaces)

## Maintainer

[@ngpestelos](https://github.com/ngpestelos). Early stage, single maintainer.

## License

Apache License 2.0 — see [LICENSE](./LICENSE).
