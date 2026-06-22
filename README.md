# InferSports

**Sharp Asian odds, built for agents.** Live football & basketball odds with first-class
Asian-handicap support, sharp de-vigged fair probabilities, and live scores — over a
**keyless, hosted MCP server and REST API**. Read-only.

`MCP server` · `Apache-2.0` · `keyless` · `read-only`

InferSports normalizes 6 Asian bookmakers + Pinnacle into one clean schema: Asian handicap
(including quarter lines with win / half-win / push logic), over/under, 1×2, and half-time
markets — plus de-vigged "fair" probabilities from the sharpest book. No API key, no signup
for the Free tier.

> Football and basketball only. Informational and **read-only** — InferSports never places,
> recommends, or sizes a bet.

## Connect (keyless)

Point any MCP client at the hosted endpoint — nothing to install, no key:

**Claude Code**

    claude mcp add --transport http infersports https://api.infersports.dev/mcp

**Claude Desktop / Cursor**

    { "mcpServers": { "infersports": { "url": "https://api.infersports.dev/mcp" } } }

The Free tier is keyless. An optional `isk_…` key raises rate limits and unlocks the sharp
(Pinnacle) book.

## Ask in plain language

- "Who's favored in France vs Argentina, and what's the Asian handicap?"
- "What World Cup matches are on today?"
- "Scan today's slate for value vs the sharp fair line."
- "Is this Polymarket price of 0.54 fair for the home side?"

| Tool | Returns |
|---|---|
| `match_info` / `find_match`            | Score, status, favorite, win probability |
| `list_today_matches` / `list_events`   | Today's / a given day's fixtures (timezone-aware) |
| `get_sharp_line` / `compare_lines`     | Consensus / best Asian-handicap line, per book |
| `get_opening_line`                     | Opening line (初盘) and how it moved |
| `find_value` / `scan_slate`            | Where a price beats the de-vigged fair line (detection only) |
| `compare_prob`                         | Judge an external (Polymarket/Kalshi) price vs the sharp fair |
| `get_result` / `list_results`          | Finished-match results (30-day cache) |

Full tool reference: **https://infersports.dev/llms-full.txt** (keyless, self-describing).

## REST API

Same data over plain REST. Base URL `https://api.infersports.dev`, contract in `openapi.yaml`.

    curl https://api.infersports.dev/v1/events/live

## The Asian edge

- **Asian handicap, first-class** — quarter / half / integer lines, split with win / half-win
  / push logic. No client-side math.
- **Asian books + Pinnacle** — the books that price the Asian market first, Pinnacle as the
  sharp reference, one normalized schema.
- **De-vigged fair value** — the sharp probability behind the price, for value & arbitrage
  detection (detection only, never execution).
- **Half-time markets & opening lines** — full-time and half-time, every line kept; opening
  (初盘) movement exposed.

## Roadmap

Typed Python & TypeScript SDKs and worked examples (arbitrage / +EV / line-movement) land next.

## Links

- Website & docs — https://infersports.dev
- Agent reference — https://infersports.dev/llms-full.txt

## License

Apache-2.0. Read-only data tooling — no scraping or ingestion code. InferSports is
informational and never places or recommends bets.
