# Concierge54

Concierge54 is the first traveler-facing application in the AGENTROPOLIS Travel District.

It consumes district Skills. It does not own provider logic, traveler policy, approval authority, or canonical booking records.

## Initial surfaces

- voice concierge
- web chat
- traveler itinerary view
- approval screen
- live event and disruption feed

## Application boundary

Concierge54 may collect intent, show options, explain tradeoffs, and request approval. All travel search, routing, validation, booking, and monitoring operations must run through district contracts.

## Prototype migration

Reusable patterns from the earlier gift-concierge prototype may be migrated selectively:

- tool-based agent calls
- server-sent event feed
- deterministic demo mode
- notification abstraction

Gift catalog logic, hackathon branding, simulated payment completion, and automatic purchase behavior are excluded.
