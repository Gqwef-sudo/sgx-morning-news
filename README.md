# SGX Morning News Reporter

Automated daily stock market news aggregator for SGX (Singapore Exchange) and personal portfolio holdings.

## Overview

This project uses a Claude Code scheduled task to:
1. Search for the latest morning news relevant to SGX and monitored holdings
2. Fetch live stock prices via Yahoo Finance
3. Generate a beautifully styled, self-contained HTML report

## Monitored Holdings

| Stock | Ticker | Sector |
|-------|--------|--------|
| DBS Group | D05.SI | Banking & Finance |
| Haw Par Corporation | H02.SI | Healthcare & Leisure |
| Singapore Land Group | U06.SI | Real Estate |
| Sheng Siong Group | OV8.SI | Consumer & Retail |
| Mapletree Industrial Trust | ME8U.SI | Industrial REIT |
| CapitaLand Integrated Commercial Trust | C38U.SI | Commercial REIT |
| Nikko AM STI ETF | G3B.SI | Index ETF |

## Report Structure

Each generated report includes:
- **Market Overview** — STI index, key Asian markets, macro summary
- **Portfolio Snapshot** — Live prices, daily changes, color-coded table
- **Top Stories** — Up to 5 most relevant news with source links
- **Sector Analysis** — Banking, REITs, Consumer, Property outlook
- **Key Events & Calendar** — Upcoming earnings, dividends, macro events

## Schedule

- **Frequency:** Weekdays (Monday–Friday)
- **Time:** 7:00 AM SGT
- **Output:** `reports/report-YYYY-MM-DD.html`

## Setup

This project runs as a Claude Code scheduled task. To set it up:

1. Ensure [Claude Code](https://claude.com/claude-code) is installed
2. The scheduled task is registered at `~/.claude/scheduled-tasks/sgx-morning-news/SKILL.md`
3. Required MCP integrations:
   - **WebSearch** — for news aggregation
   - **Yahoo Finance** — for live stock prices and analyst data

## Manual Trigger

You can manually run the task from the Claude Code sidebar under "Scheduled" tasks, or ask Claude:
> "Run the sgx-morning-news task"

## Reports

Generated reports are saved to the `reports/` directory. Each is a self-contained HTML file with inline styling — no external dependencies needed. Open in any browser.

## Disclaimer

Reports are auto-generated for personal use only. Not financial advice.
