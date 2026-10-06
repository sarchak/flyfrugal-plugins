# Fly Frugal MCP server and plugins

[Fly Frugal](https://flyfrugal.fyi) finds cheap round-trip flights from US airports and publishes day-by-day budget travel itineraries. This repository holds the plugins and registry metadata that connect Claude, ChatGPT, Codex, Cursor and other MCP clients to Fly Frugal's public, read-only MCP server.

**MCP server:** `https://flyfrugal.fyi/mcp` (Streamable HTTP, no sign-in or API key)
**Official MCP Registry:** `fyi.flyfrugal/travel-data`

## Tools

| Tool | What it does |
| --- | --- |
| `list_itineraries` | Browse published itinerary previews. |
| `get_itinerary` | Read one itinerary preview by slug. |
| `list_flight_deals` | Browse current observed round-trip fares, globally or from one airport. |
| `get_todays_deals` | Return only savings verified today. Returns an empty list rather than older results. |

All tools are read-only. Fares are observations and can change or sell out, so check the price again before booking.

## Install

**Claude Code** (plugin):

```
/plugin marketplace add sarchak/flyfrugal-plugins
/plugin install flyfrugal-itineraries@flyfrugal
```

**Claude Code** (server only):

```
claude mcp add --transport http --scope user flyfrugal-travel-data https://flyfrugal.fyi/mcp
```

**Codex:**

```
codex mcp add flyfrugal-travel-data --url https://flyfrugal.fyi/mcp
```

**Cursor and VS Code:** use the one-click buttons on [flyfrugal.fyi/docs](https://flyfrugal.fyi/docs#connect), or add this to your MCP config:

```json
{
  "mcpServers": {
    "flyfrugal-travel-data": { "url": "https://flyfrugal.fyi/mcp" }
  }
}
```

**Claude and ChatGPT apps:** add a custom connector with the URL `https://flyfrugal.fyi/mcp`. No authentication is needed.

## Try it

- "Show me published Fly Frugal trip guide previews."
- "Find recently observed round-trip fares from SFO."
- "Which flight savings were verified today?"

## Layout

- `flyfrugal-itineraries/`: the Claude Code plugin (MCP server and the `browse-travel-data` skill).
- `codex/`: the Codex and ChatGPT plugin package.
- `server.json`: the official MCP Registry entry.

Docs: [flyfrugal.fyi/docs](https://flyfrugal.fyi/docs) · [Privacy](https://flyfrugal.fyi/privacy) · [Contact](https://flyfrugal.fyi/contact)
