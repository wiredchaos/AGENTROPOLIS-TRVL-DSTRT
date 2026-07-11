# AGENTROPOLIS TRVL DSTRT

> Travel intelligence is a public utility. Booking rails are replaceable connectors.

The **AGENTROPOLIS Travel District** is the domain institution for travel search, routing, itinerary construction, approvals, disruption monitoring, traveler messaging, and booking orchestration.

It is not a single travel app. It publishes governed Skills to the AGENTROPOLIS Intelligence Grid. Applications such as **Concierge54** consume those Skills.

## Status

**District:** TRVL DSTRT  
**Layer:** District / Institution  
**Status:** Under construction  
**License:** Apache 2.0  
**Primary application:** Concierge54

## Non-negotiable rule

> No irreversible booking, payment, cancellation, or traveler-data disclosure occurs without explicit, recorded user approval.

## Core Skill chain

```text
WAYFINDER
  -> FLIGHTLINE / STAYGRID
  -> ROUTE54
  -> FAREGUARD
  -> CLEARANCE
  -> booking connector
  -> ARRIVAL
  -> TRIPWIRE
```

| Skill | Role |
|---|---|
| WAYFINDER | Capture traveler intent, dates, budget, preferences, and constraints |
| FLIGHTLINE | Normalize and compare flight inventory across providers |
| STAYGRID | Search and compare lodging inventory |
| ROUTE54 | Build a feasible multimodal itinerary |
| FAREGUARD | Validate price, fees, restrictions, and policy compliance |
| CLEARANCE | Enforce explicit human approval before irreversible actions |
| ARRIVAL | Deliver confirmations, receipts, calendars, and traveler briefs |
| TRIPWIRE | Monitor delays, cancellations, schedule changes, and material price shifts |

## Architecture

```text
Layer 1 — Intelligence Grid
runtime · memory · registry · dispatch · audit

Layer 2 — TRVL DSTRT
travel policy · provider adapters · routing · approvals · monitoring

Layer 3 — Applications
Concierge54 · operator consoles · traveler portals · partner experiences
```

## Open-source foundation

- OpenStreetMap, Wikidata, and Wikivoyage for geographic and destination intelligence
- MapLibre for map rendering
- Pelias or Photon for geocoding
- OpenTripPlanner or MOTIS for multimodal routing
- Valhalla or OSRM for road routing
- OR-Tools or Timefold for itinerary constraints
- Open-Meteo for weather intelligence
- Matrix, ntfy, and Apprise for notifications
- Keycloak for identity
- Paperless-ngx for receipts and travel documents
- Hyperswitch for payment-provider abstraction

Live airline ticketing, global hotel inventory, and regulated card processing remain connector concerns. The district must never become dependent on one supplier.

## Repository map

```text
apps/concierge54/       traveler-facing application
skills/                 governed travel Skills
connectors/             replaceable supplier and open-data adapters
services/               routing, itinerary, approval, notification, payment
registry/               district and Skill manifests
docs/                   architecture, governance, and provider decisions
```

## Current phase

1. Establish district contracts and registry.
2. Implement open-data route and destination intelligence.
3. Add provider adapters behind normalized interfaces.
4. Connect Concierge54 as the first application.
5. Require CLEARANCE before every irreversible transaction.

## License

Apache License 2.0. See [LICENSE](LICENSE).
