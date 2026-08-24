# Nodlow.ai MCP

**Let Claude, Codex, Cursor — any LLM — build, backtest, and deploy trading
bots for you. Safely.**

You could ask an AI to write a trading bot in Python. It'll happily do it.
Then it'll silently misread a candle, size a position wrong, or crash mid-
trade with real money on the line.

Nodlow.ai flips it: the LLM doesn't write code. It composes strategies from
audited blocks — indicators, entry/exit rules, risk sizing — that run on the
same engine we use in production. **What you backtest is exactly what goes
live.** No translation layer, no "works on my laptop", no weird live
behavior.

This repo is just the setup guide. Two minutes, no credit card.

---

## 1. Get a token (free, ~10 seconds)

1. Sign up at **[nodlow.ai](https://nodlow.ai?src=mcp)** — email only, no
   card.
2. **Settings → Developer → New token** → copy the `nod_…` value.

That's it. Free — no card, no trial timer.

## 2. Plug it into your agent

Endpoint: `https://nodlow.ai/api/mcp`

### Claude Code

```bash
claude mcp add --transport http nodlow https://nodlow.ai/api/mcp \
  --header "Authorization: Bearer nod_YOUR_TOKEN"
```

### Codex

```json
{
  "servers": {
    "nodlow": {
      "type": "http",
      "url": "https://nodlow.ai/api/mcp",
      "auth": { "bearer": "nod_YOUR_TOKEN" }
    }
  }
}
```

Using a different agent (Claude Desktop, Cursor, Windsurf, …)? Ask it to
add the `nodlow` MCP server at `https://nodlow.ai/api/mcp` with header
`Authorization: Bearer nod_YOUR_TOKEN` — it'll write the right config for
your client.

## 3. Ask it to build something

> *"Use nodlow. Build an Opening Range Breakout on NAS100, 5m: mark the
> first 30 minutes after the New York open, go long on a break of the
> range high with a stop at the range low, short on the mirror side, 1R
> take-profit, only one trade per day. Backtest the last 12 months, then
> try 15 and 45-minute range variants and also SP500 and GOLD, and show
> me which held up best. If any backtest beats a 1.4 profit factor,
> deploy it in a demo account."*

Nodlow ships a large block catalog (indicators, patterns, breakout /
consolidation / swing tools, risk sizing) and we keep expanding it. If your
agent can't find something it needs, ask it to call `request_indicator` or
`report_issue` — both land in the staff triage queue with in-app + email
follow-up when resolved.

The agent will call `get_started` first, which hands it the full recipe,
available indicators, timeframes, and error codes. From there it's:

1. Pick instrument + timeframe
2. Compose the strategy from blocks
3. Backtest, read metrics
4. Deploy a **demo bot** for walk-forward validation — auto, no click, no
   real capital
5. Ready to go **live**? The agent hands you a signed link; you click it
   in-app to confirm before real money moves

**Real capital is always human-gated.** Demo bots deploy straight from
chat so you can iterate fast; live and prop-firm deploys always need your
click in-app.

---

Something missing or broken? Tell your agent to report the issue or ping
the support inside [nodlow.ai](https://nodlow.ai?src=mcp).
