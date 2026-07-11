# Travel District Skills

Each Skill is atomic, auditable, and provider-neutral.

## WAYFINDER

**Role:** Convert a natural-language trip request into a validated travel brief.  
**Tier:** core  
**Triggers:** plan a trip; find travel; build an itinerary; help me get to; travel under a budget  
**Chains to:** FLIGHTLINE, STAYGRID, ROUTE54  
**Requires:** traveler input; optional profile and policy connectors  
**Output:** destinations, dates, travelers, budget, preferences, constraints, missing fields, correlation ID  
**Example:** “Plan Sacramento to Lisbon for two adults in October under $4,000.”

## FLIGHTLINE

**Role:** Search, normalize, rank, and explain flight offers without inventing availability.  
**Tier:** core  
**Triggers:** find flights; compare airfare; show nonstop options; search award or cash fares  
**Chains from:** WAYFINDER  
**Chains to:** FAREGUARD, ROUTE54  
**Requires:** one or more flight inventory connectors  
**Output:** normalized offers, provider timestamps, total prices, baggage terms, fare restrictions, offer expirations  
**Example:** “Compare SFO to CDG flights with one checked bag.”

## STAYGRID

**Role:** Search and compare lodging against location, accessibility, policy, and total-cost constraints.  
**Tier:** core  
**Triggers:** find a hotel; compare lodging; stay near; accessible room; refundable stay  
**Chains from:** WAYFINDER  
**Chains to:** FAREGUARD, ROUTE54  
**Requires:** direct-property or marketplace lodging connectors  
**Output:** normalized stays, taxes and fees, cancellation rules, distance and route evidence, availability timestamp  
**Example:** “Find a refundable hotel near the convention center with step-free access.”

## ROUTE54

**Role:** Construct a feasible multimodal itinerary using calculated routes, schedules, and operating hours.  
**Tier:** core  
**Triggers:** build my itinerary; connect these reservations; plan each day; can I make this connection  
**Chains from:** WAYFINDER, FLIGHTLINE, STAYGRID  
**Chains to:** FAREGUARD, ARRIVAL  
**Requires:** routing engine, geocoder, place data, timezone data  
**Output:** ordered itinerary, transfers, buffers, conflicts, map references, confidence flags  
**Example:** “Build three Paris days around these museum reservations.”

## FAREGUARD

**Role:** Validate the real trip cost, restrictions, policy compliance, and material risks before approval.  
**Tier:** core  
**Triggers:** check the total; audit this fare; verify fees; is this refundable; check company policy  
**Chains from:** FLIGHTLINE, STAYGRID, ROUTE54  
**Chains to:** CLEARANCE  
**Requires:** normalized offers and applicable travel policy  
**Output:** total cost, fee breakdown, restrictions, policy exceptions, change risk, approval summary  
**Example:** “Audit this $620 fare after baggage and seat fees.”

## CLEARANCE

**Role:** Produce and verify explicit, scoped human authorization for irreversible travel actions.  
**Tier:** infrastructure  
**Triggers:** book it; pay now; cancel it; change my reservation; share my passport details  
**Chains from:** FAREGUARD  
**Chains to:** booking or payment connector, ARRIVAL  
**Requires:** authenticated approver, exact action payload, expiration, audit store  
**Output:** approved, denied, or expired decision with immutable correlation data  
**Example:** “Approve charging $684.32 for offer ABC before 4:15 PM Pacific.”

## ARRIVAL

**Role:** Convert confirmed transactions into traveler-ready records, calendars, receipts, and briefings.  
**Tier:** core  
**Triggers:** send my confirmation; add this trip to my calendar; build my travel packet  
**Chains from:** CLEARANCE and confirmed provider responses  
**Chains to:** TRIPWIRE  
**Requires:** confirmed reservation data and messaging/document connectors  
**Output:** canonical trip record, calendar events, receipts, confirmation delivery results, traveler brief  
**Example:** “Send the confirmed itinerary to Matrix and create calendar events.”

## TRIPWIRE

**Role:** Monitor approved travel for meaningful disruptions and notify only when action is warranted.  
**Tier:** extended  
**Triggers:** watch this trip; alert me about delays; monitor the fare; track gate changes  
**Chains from:** ARRIVAL  
**Chains to:** WAYFINDER or CLEARANCE when replanning or changes are required  
**Requires:** confirmed trip record and live status sources  
**Output:** disruption event, source timestamp, traveler impact, recommended response, approval requirement  
**Example:** “Notify me when a delay threatens my connection, not for minor schedule noise.”
