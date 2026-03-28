# SGX Morning News Reporter

Automated daily stock market news aggregator for SGX (Singapore Exchange) and personal portfolio holdings. Runs as a **remote** Claude Code scheduled task — executes on Anthropic's cloud servers so it works even when your device is off.

## Overview

This project uses a Claude Code **remote scheduled task** to:
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

## Setup: Remote Scheduled Task

This task runs on Anthropic's cloud — your device does **not** need to be on.

### Step 1: Open Claude Code

Open Claude Code in any terminal or IDE.

### Step 2: Create the Remote Scheduled Task

Use the `/schedule` skill or ask Claude directly:

> Create a remote scheduled task called "sgx-morning-news" that runs weekdays at 7:00 AM SGT (Asia/Singapore). Use the prompt from the SKILL.md file in this repo.

Alternatively, paste this command:

```
/schedule create sgx-morning-news --remote --cron "0 7 * * 1-5" --timezone "Asia/Singapore"
```

Then paste the full contents of [`SKILL.md`](./SKILL.md) as the task prompt.

### Step 3: Approve Tool Permissions

On the first run, you'll be asked to approve access to:
- **WebSearch** — for news aggregation
- **Yahoo Finance MCP** — for live stock prices and analyst data

Approve these once; they'll be remembered for future runs.

### Step 4: Verify

Check the task is running:
- Open Claude Code sidebar → "Scheduled" section
- Confirm the task shows as **enabled** and **remote**
- Click "Run now" to test

## Task Prompt

The full task instructions are in [`SKILL.md`](./SKILL.md). This file contains:
- The list of holdings to monitor
- Web search queries to run
- Yahoo Finance data to fetch
- Complete HTML report structure and styling specifications

To modify the task behavior (e.g., add/remove holdings, change report format), edit `SKILL.md` and update the remote scheduled task prompt accordingly.

## Reports

Generated reports are saved as self-contained HTML files with inline styling — no external dependencies. Open in any browser.

**Note:** Since the task runs remotely, reports are delivered in the Claude Code session. You can configure the task to save reports locally or send them via email/notification depending on your setup.

## Manual Trigger

You can manually trigger the task at any time:
- From the Claude Code sidebar → "Scheduled" → "Run now"
- Or ask Claude: *"Run the sgx-morning-news task"*

## Disclaimer

Reports are auto-generated for personal use only. Not financial advice.
