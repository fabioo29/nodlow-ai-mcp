# Changelog

What's new in Nodlow MCP — the toolbox your AI agent uses to build, backtest,
and deploy trading strategies on Nodlow.ai.

## 2026-08-25 — first release

Your agent can now do the full loop end-to-end: explore the block library,
draft a strategy, backtest it, iterate, and deploy a demo bot for
walk-forward validation. Here's what it can do out of the box.

### Explore what's available

- **Get started** — a short recipe + a working example the agent reads first.
- **Browse timeframes** — 1m, 5m, 15m, 30m, 1h, 4h, 1d.
- **Browse instruments** — every ticker with backtest data ready.
- **Browse blocks, indicators, and candle patterns** — RSI, MACD, EMA,
  engulfing, hammer, and everything else in the library.
- **Inspect any block's schema** — inputs, outputs, and parameters.
- **Browse templates** — prebuilt strategies the agent can clone and tweak.

### Build & iterate on strategies

- **Validate** a draft strategy without saving it, and get errors + warnings.
- **Create** a new strategy and get back its hash.
- **Update** an existing strategy — nodes, edges, name, metadata.
- **List your strategies** — everything you own.

### Backtest

- **Run a backtest** on any `(strategy, ticker, timeframe, date range)`.
  Counts toward your weekly usage.
- **Poll for status** — running → completed / failed.
- **Get the trade list** — every trade the backtest opened.
- **Get the equity curve** — ready to chart.
- **List your backtests** — filter and browse.

### Deploy bots

- **Suggest deploy** — for **demo** mode the agent deploys the bot for you
  right away; for **live** and **prop-firm** you always get a signed link
  to open in the browser and confirm (real money never deploys without you).
- **List your bots**, **get a bot's detail**, and **get its trade history**.

### Send feedback

- **Request an indicator** when something you need isn't in the library.
- **Report an issue** when something misbehaves.

### Good to know

- Every response tells you whether it worked. When it doesn't, you get a
  clear reason (bad date range, unknown ticker, usage limit reached, etc.).
- Dates are plain ISO — `2026-01-01` works.
- Backtests are capped at 50,000 candles per run.
- Deploy modes: `demo` (auto), `live` (human confirms), `prop-firm`
  (human confirms).
