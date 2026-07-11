# Travel District Governance

Every Skill is a contract with the Intelligence Grid. Every provider is a replaceable adapter. Every irreversible action requires human clearance.

## Approval boundary

The district may autonomously:

- collect trip requirements
- search providers and open data
- compare offers
- calculate routes and schedules
- draft itineraries
- estimate total trip cost
- prepare a booking request
- monitor already-approved travel

The district may not autonomously:

- purchase a ticket
- reserve paid lodging
- charge a payment method
- cancel or materially change a reservation
- disclose passport, payment, loyalty, medical, or precise-location data

These actions require an explicit approval record produced by CLEARANCE.

## Approval record

Each record must include:

- traveler or authorized approver
- action being approved
- provider
- exact item or itinerary
- total amount and currency
- material restrictions and cancellation terms
- timestamp
- expiration time
- correlation ID

Approval is scoped. Consent to search is not consent to book. Consent to one price is not consent to a higher price.

## Provider neutrality

Supplier APIs, payment processors, voice vendors, and messaging networks are connectors. No connector owns district state, traveler policy, approval logic, or canonical itinerary records.

## Data minimization

Collect only information required for the active travel task. Secrets and traveler records must remain outside the public repository. Logs must redact payment credentials, identity documents, authentication tokens, and unnecessary personal data.

## Failure behavior

When availability, price, identity, payment, or policy state is uncertain, the system must stop before execution and return a structured explanation. It must never invent inventory or silently substitute a booking.

## Auditability

Every search, recommendation, approval, provider request, provider response, booking result, and notification must be traceable through a correlation ID.
