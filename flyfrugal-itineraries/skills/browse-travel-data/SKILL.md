---
name: browse-travel-data
description: Browse Fly Frugal's public itinerary previews, current observed flight fares, and deals verified today.
---

# Browse Fly Frugal travel data

Use the `flyfrugal-travel-data` MCP server only for public, read-only travel discovery.

- Use `list_itineraries` to browse published previews and `get_itinerary` for one guide.
- Use `list_flight_deals` for current observed fares from one airport or globally.
- Use `get_todays_deals` when the user explicitly asks for today's deals; do not substitute older results when the returned list is empty.
- State that observed fares can change or sell out.
- Do not claim access to paid itinerary content, purchases, customers, alerts, administration, or publishing.
