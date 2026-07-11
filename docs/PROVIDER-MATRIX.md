# Provider Matrix

Providers are classified by function, openness, and whether they control transactional inventory.

| Domain | Open-source foundation | Commercial connector candidates | District rule |
|---|---|---|---|
| Destination data | OpenStreetMap, Wikidata, Wikivoyage | Google Places, Foursquare | Open data is canonical where practical |
| Geocoding | Pelias, Photon, Nominatim | Mapbox, Google | Adapters return normalized places |
| Maps | MapLibre, OpenMapTiles | Mapbox, Google Maps | Rendering provider must be replaceable |
| Multimodal routing | OpenTripPlanner, MOTIS | Rome2Rio | Route claims require calculated travel time |
| Road routing | Valhalla, OSRM, GraphHopper | Google Routes, HERE | Never estimate connections with LLM intuition alone |
| Flight reference data | OurAirports, OpenFlights, OpenSky | FlightAware, Cirium | Reference data is not ticket inventory |
| Flight offers and ticketing | none complete | LetsFG, Duffel, Amadeus, Sabre, Travelport, airline NDC | Normalize offers; isolate ticket issuance |
| Lodging operations | QloApps, HotelDruid | Booking.com, Expedia, Hotelbeds, direct hotel APIs | Direct property inventory and marketplace inventory remain distinct |
| Itinerary optimization | OR-Tools, Timefold | proprietary optimizers | Operating hours and travel time must be validated |
| Weather | Open-Meteo, Meteostat, NOAA/NWS | Tomorrow.io, WeatherAPI | Alert source and timestamp must be retained |
| Messaging | Matrix, ntfy, Apprise, Novu | Telegram, WhatsApp, SMS vendors | Channel failure cannot invalidate booking state |
| Identity | Keycloak, Authentik | Auth0, Clerk | Traveler identity stays district-controlled |
| Documents | Paperless-ngx, Nextcloud | cloud document vendors | Sensitive documents remain private |
| Payment orchestration | Hyperswitch, Kill Bill | Stripe, Adyen, Braintree | Payment rail is replaceable; CLEARANCE is mandatory |
| Voice | LiveKit, Pipecat, faster-whisper, Piper | ElevenLabs, telephony vendors | Voice is an interface, not an authority |

## Initial evaluation order

1. OpenStreetMap + MapLibre + Pelias
2. OpenTripPlanner versus MOTIS
3. Valhalla versus OSRM
4. OR-Tools itinerary validation
5. Open-Meteo disruption inputs
6. LetsFG versus Duffel versus Amadeus for transactional flight access
7. QloApps for direct-property experiments
8. Hyperswitch for payment-provider abstraction
