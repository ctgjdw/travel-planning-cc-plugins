# Travel Planning — Claude Code Plugin

A Claude Code plugin that adds a structured, collaborative travel planning skill. Give Claude a destination and duration, and it walks you through a single upfront questionnaire then generates a complete set of trip-planning documents you can iterate on across sessions.

## What it does

The **planning-trips** skill turns a vague trip idea ("plan a trip from Singapore to Osaka for 10D9N") into a durable project on disk:

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Project memory — preferences, bookings, tooling notes for future sessions |
| `00_overview.md` | At-a-glance summary, flights, budget, packing, etiquette |
| `01_itinerary.md` | Hour-by-hour day-by-day schedule |
| `02_accommodation.md` | Hotel shortlist with criteria and comparison |
| `03_reservations.md` | Booking tracker with priority timeline |
| `04_transport.md` | Intercity and local transit decisions and costs |
| `05_bucketlist.md` | Categorized place lists per city (food, shopping, sights, etc.) |

### Key principles

- **Ask once, capture everything** — a single structured questionnaire gathers all planning inputs upfront.
- **No fabrication** — every operational fact (hours, prices, dates) must come from a verified source or be explicitly labeled as unverified.
- **Session-durable** — all context is persisted to files so future Claude Code sessions can pick up where you left off.
- **Tool-aware** — integrates with Google Maps, Booking.com, Reddit, and Wanderlog MCPs when available; falls back to web search gracefully.

## Installation

```bash
claude plugin marketplace add https://www.github.com/ctgjdw/travel-planning-cc-plugins
```

After adding the marketplace, go to `/plugin` and install from the marketplace.

## Usage

Start a Claude Code session and describe your trip:

```
Plan a trip from Singapore to Tokyo for 12D11N
```

Claude will confirm the project structure, run through the questionnaire, then generate all seven planning documents in your current directory.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI

### Optional (recommended)

The following MCP servers enhance the planning experience but are not required — the skill falls back to web search when they are unavailable.

| MCP Server | Purpose | Source |
|------------|---------|--------|
| **Google Maps (Grounding Lite)** | Verify places, addresses, operating hours and coordinates | [Google Maps Platform](https://developers.google.com/maps/ai/grounding-lite) |
| **Booking.com** | Hotel research, pricing and ratings | Built-in Claude integration |
| **Reddit (OpenTabs)** | Crowd-sourced travel tips and recommendations | [opentabs-dev/opentabs](https://github.com/opentabs-dev/opentabs) |
| **Wanderlog** | Sync itinerary to Wanderlog | [shaikhspeare/wanderlog-mcp](https://github.com/shaikhspeare/wanderlog-mcp) |
| **Gmail / Google Drive** | Retrieve confirmed bookings from email | Built-in Claude integration |

## License

MIT
