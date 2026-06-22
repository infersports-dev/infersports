<div align="center">
  <img src="assets/logo.svg" width="76" alt="InferSports" />

# InferSports

Live Asian-priced football & basketball odds, scores, and de-vigged sharp fair
lines — as a **keyless, hosted MCP server + REST API** for Claude Code, Cursor,
Claude Desktop, or any agent.

**Read-only · Keyless · MCP + REST · one hosted URL, nothing to install**

[![License](https://img.shields.io/github/license/infersports-dev/infersports)](LICENSE)
[![MCP server](https://img.shields.io/badge/MCP%20server-streamable--HTTP-E0683C)](https://api.infersports.dev/mcp)
[![OpenAPI](https://img.shields.io/badge/OpenAPI-1.0.0-1E2A24)](openapi.yaml)
[![API docs](https://img.shields.io/badge/docs-api.infersports.dev-blue)](https://api.infersports.dev/docs)

</div>

---

Point any MCP client at one hosted URL — no install, no API key — then ask in plain language:

```console
# connect (Claude Code)
$ claude mcp add --transport http infersports https://api.infersports.dev/mcp

# "who's favored in France vs Argentina, and what's the Asian handicap?"
France vs Argentina — France favored (84.0%) · AH -2.25 · kicks off 21:10

# "scan today's slate for value vs the sharp fair line"
Value scan 2026-06-12 — 5 shown (scanned 76)
  evt_… | A v B | sbobet AH -1 home @2.14 | fair 2.08 | +2.9%

# "is this Polymarket price of 0.54 fair for the home side?"
1x2 home: sharp fair 55.6% vs polymarket 54.0% → +1.6pp (ROI +3.0%) · de-vig pinnacle
```

No account, no key, no payment for the Free tier. InferSports normalizes 6 Asian books +
Pinnacle into one clean schema and computes the sharp de-vigged fair price for you.

> Football and basketball only. Informational and **read-only** — InferSports never
> places, recommends, or sizes a bet.

## Why this exists

- **Asian market data, normalized.** Asian handicap (quarter lines with win / half-win /
  push), over/under, and 1×2 — full-time *and* half-time — from 7 curated books, every quote
  convertible across decimal, Hong Kong, Malay, Indonesian, American, and implied probability.
- **Asian books + Pinnacle.** The books that price the Asian market first, with Pinnacle as the
  sharp reference, in one schema — plus the de-vigged fair price behind it.
- **Built for agents.** Keyless, hosted, self-describing — one URL, nothing to install. Ask in
  plain language; get structured answers back.
- **Read-only, detection only.** It reports lines, prices, and detected edges as data. It never
  places, recommends, or sizes a bet — and tells the agent not to either.

## Connect

### Claude Code — one line

```
claude mcp add --transport http infersports https://api.infersports.dev/mcp
```

### Claude Desktop / Cursor

```json
{ "mcpServers": { "infersports": { "url": "https://api.infersports.dev/mcp" } } }
```

The Free tier is keyless. An optional `isk_…` key raises rate limits and unlocks the sharp
(Pinnacle) book.

### REST

Same data over plain REST — base `https://api.infersports.dev`, contract in
[`openapi.yaml`](openapi.yaml):

```
curl https://api.infersports.dev/v1/events/live
```

## Tools

| Tool | Returns |
|---|---|
| `match_info` / `find_match`            | Score, status, favorite, win probability |
| `list_today_matches` / `list_events`   | Today's / a given day's fixtures (timezone-aware) |
| `get_sharp_line` / `compare_lines`     | Consensus / best Asian-handicap line, per book |
| `get_opening_line`                     | Opening line and how it moved |
| `find_value` / `scan_slate`            | Where a price beats the de-vigged fair line (detection only) |
| `compare_prob`                         | Judge an external (Polymarket/Kalshi) price vs the sharp fair |
| `get_result` / `list_results`          | Finished-match results (30-day cache) |

Full tool reference: **https://infersports.dev/llms-full.txt** (keyless, self-describing).
See [`AGENTS.md`](AGENTS.md) for agent-integration rules.

## Roadmap

Typed Python & TypeScript SDKs and worked examples (arbitrage / +EV / line-movement) land next.

## Links

- Website & docs — https://infersports.dev
- Agent reference — https://infersports.dev/llms-full.txt
- Skill (shell-script verbs) — https://github.com/infersports/infersports-skill

## License

[Apache-2.0](LICENSE). Read-only data tooling — no scraping or ingestion code. InferSports is
informational and never places or recommends bets.
