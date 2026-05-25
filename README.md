# MarineTraffic (marine-traffic)

MarineTraffic is the leading maritime intelligence and AIS ship-tracking platform — now part of Kpler. The MarineTraffic AIS Data API exposes the same live + historical vessel positions, port calls, berth calls, vessel master data, voyage forecasts, predictive arrivals, port-congestion analytics, sea-lane routing, reverse geocoding, and fleet management endpoints that power the public marinetraffic.com map and the Kpler maritime data services. Data is sourced from 13,000+ terrestrial AIS receivers plus satellite AIS, served as REST/JSON (with CSV / XML / JSONO alternatives), authenticated via a per-key prepaid credit balance, and metered in credits per response row with per-service refresh-interval caching.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/marine-traffic/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - AIS, Maritime, Vessel Tracking, Shipping, Ports, Voyage Forecasting, Geospatial, Kpler

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## At a Glance

| Surface | Endpoints | Highlights |
|---|---|---|
| Vessel Positions | `/exportvessels`, `/exportvessel`, `/exportvessels-custom-area`, `/exportvesseltrack` | Single / fleet / area / port / bbox; modern AIS API + Legacy PS01–PS08 |
| Events | `/portcalls`, `/vesselevents`, `/berth-calls` | Single-vessel and port-scoped port calls and berth calls |
| Vessels Data | `/vesselmasterdata`, `/exportvesselphoto`, `/shipsearch` | Static master record + photo + search by ID or name |
| Voyage Info | `/voyageforecast`, `/predictive-destination-areas`, `/etatoport` | ML-driven destination + ETA prediction |
| Ports Info | `/expectedarrivals`, `/predictive-arrivals`, `/port-congestion` | Per-port arrival forecasts + congestion analytics |
| Routing | `/exportroutes` | Sea-lane-aware route + distance |
| Reverse Geocoding | `/reversegeocode` | Coordinate → port / anchorage / berth / terminal |
| Power User | `/setfleet`, `/getfleet`, `/getfleets`, `/clearfleet`, `/exportcredits`, `/import-passage-plan` | Fleet CRUD + credit balance + passage plan import |

**Base URL:** `https://services.marinetraffic.com/api`
**Authentication:** API key passed as a path segment — `/{service}/{api_key}?…`
**Response protocols:** `json` (default), `jsono`, `xml`, `csv` via the `protocol` query parameter
**Metering:** credits-per-row against a prepaid credit balance, with per-service refresh intervals (cache windows)

## APIs

### MarineTraffic Vessel Positions API
Real-time and historical AIS vessel positions sourced from 13,000+ terrestrial AIS receivers and satellite AIS feeds. Query by single vessel (MMSI / IMO / SHIP_ID), by fleet, by predefined area of interest, by port, or by a custom bounding box. Includes the modern AIS API (`/exportvessels`, `/exportvessel`, `/exportvessels-custom-area` — MTA030AD-family with cursor pagination) and the legacy PS01–PS08 surface, plus Vessel Historical Track (`/exportvesseltrack`).

**Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-vessel-positions-openapi.yml)
- [JSON Schema — Vessel Position](json-schema/marine-traffic-vessel-position-schema.json)
- [JSON-LD](json-ld/marine-traffic-context.jsonld)
- [Example — Vessel Position](examples/marine-traffic-vessel-position-example.json)
- [Naftiko Capability — Vessel Positions (AIS API)](capabilities/vessel-positions-ais.yaml)
- [Naftiko Capability — Vessel Historical Track](capabilities/vessel-positions-historical-track.yaml)

### MarineTraffic Events API
Port calls, berth calls, and event timelines — surfaces every arrival, departure, and berth touch detected by the MarineTraffic AIS network. Scope by vessel (MMSI/IMO/SHIP_ID) or by port (port_id / UNLOCODE / berth_id / terminal_id). Returns voyage duration, time-in-port, draught, market segment, and full vessel/port keys for downstream joining.

**Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

- [OpenAPI](openapi/marine-traffic-events-openapi.yml)
- [JSON Schema — Port Call](json-schema/marine-traffic-port-call-schema.json)
- [Example — Port Call](examples/marine-traffic-port-call-example.json)
- [Naftiko Capability — Single Vessel Events](capabilities/events-single-vessel.yaml)
- [Naftiko Capability — Port Events](capabilities/events-port.yaml)

### MarineTraffic Vessels Data API
Vessel master data (`/vesselmasterdata`), vessel photographs (`/exportvesselphoto`), and the ship-database search surface (`/shipsearch` by identifier or by name). Returns the full static AIS record plus MarineTraffic enrichments — owner, manager, builder, classification society, build year, dimensions, deadweight, gross tonnage, operational status.

**Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

- [OpenAPI](openapi/marine-traffic-vessels-data-openapi.yml)
- [JSON Schema — Vessel Master](json-schema/marine-traffic-vessel-master-schema.json)
- [Naftiko Capability — Vessel Information](capabilities/vessels-data-information.yaml)
- [Naftiko Capability — Search Vessel](capabilities/vessels-data-search.yaml)

### MarineTraffic Voyage Information API
Machine-learning–powered voyage intelligence: voyage forecast (`/voyageforecast`), predictive destination areas (`/predictive-destination-areas`), and ETA-to-port (`/etatoport`). Combines live AIS positions, port-call history, and predictive routing to deliver destination predictions with probability scores, ranked alternative destination ports, and predictive ETAs that outperform raw AIS-broadcast ETAs.

**Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

- [OpenAPI](openapi/marine-traffic-voyage-info-openapi.yml)
- [JSON Schema — Voyage Forecast](json-schema/marine-traffic-voyage-forecast-schema.json)
- [Example — Voyage Forecast](examples/marine-traffic-voyage-forecast-example.json)
- [Naftiko Capability — Voyage Information](capabilities/voyage-information.yaml)

### MarineTraffic Ports Information API
Port-centric analytics: expected port arrivals (`/expectedarrivals`), predictive arrivals (`/predictive-arrivals`), and port-congestion analytics (`/port-congestion`) with anchorage-time, in-port-time, vessels-in-port, and call-count metrics aggregated by market or ship class for a given port and ISO week.

**Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

- [OpenAPI](openapi/marine-traffic-ports-info-openapi.yml)
- [JSON Schema — Port](json-schema/marine-traffic-port-schema.json)
- [Naftiko Capability — Ports Information](capabilities/ports-information.yaml)

### MarineTraffic Routing Information API
Maritime route generation and distance calculation across global sea lanes via `/exportroutes`. Compute the route from a vessel's current position (MMSI/IMO/SHIP_ID) — or an arbitrary origin port / LAT-LON pair — to a target port, with optional inland-waterway and alternative-route inclusion.

**Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

- [OpenAPI](openapi/marine-traffic-routing-openapi.yml)
- [Naftiko Capability — Routing Information](capabilities/routing-information.yaml)

### MarineTraffic Reverse Geocoding API
Maritime-aware reverse geocoding (`/reversegeocode`) — resolves a single coordinate pair to the nearest port, anchorage, terminal, berth, or standard / custom area within a configurable radius.

**Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

- [OpenAPI](openapi/marine-traffic-reverse-geocoding-openapi.yml)
- [Naftiko Capability — Reverse Geocoding](capabilities/reverse-geocoding.yaml)

### MarineTraffic Power User API
Power-user administration surface: fleet CRUD (`/setfleet`, `/getfleet`, `/getfleets`, `/clearfleet`), API credit-balance inspection (`/exportcredits` — free), and passage-plan import (`/import-passage-plan`, POST).

**Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

- [OpenAPI](openapi/marine-traffic-power-user-openapi.yml)
- [Naftiko Capability — Fleet Management](capabilities/power-user-fleets.yaml)
- [Naftiko Capability — Account Balances](capabilities/power-user-balances.yaml)
- [Naftiko Capability — Passage Plans](capabilities/power-user-passage-plans.yaml)

## Common Resources

- [MarineTraffic Portal](https://www.marinetraffic.com/)
- [AIS Data API Reference](https://servicedocs.marinetraffic.com/)
- [Kpler / MarineTraffic Maritime Data Services](https://www.kpler.com/product/maritime/data-services)
- [MarineTraffic Live Map](https://www.marinetraffic.com/en/ais/home)
- [API Most Common Response Error Codes](https://support.marinetraffic.com/en/articles/9552800-api-most-common-response-error-codes)
- [What Kind of Information is AIS Transmitted](https://support.marinetraffic.com/en/articles/9552860-what-kind-of-information-is-ais-transmitted)
- [Support Center](https://support.marinetraffic.com/)
- [MarineTraffic on GitHub](https://github.com/marinetraffic) — [`mt-ais-toolbox`](https://github.com/marinetraffic/mt-ais-toolbox) (AIS density map toolbox)
- [MarineTraffic on LinkedIn](https://www.linkedin.com/company/marinetraffic) · [on Twitter / X](https://twitter.com/MarineTraffic)

## Plans, Rate Limits, and FinOps

- [Plans and Credit Pricing](plans/marine-traffic-plans-pricing.yml)
- [Rate Limits and Refresh Intervals](rate-limits/marine-traffic-rate-limits.yml)
- [FinOps Profile](finops/marine-traffic-finops.yml)

Pricing is credit-based — every API service charges a published number of credits per row (or per call) against a prepaid balance. Pre-purchase credits in advance; per-service refresh intervals serve repeat queries from cache without consuming credits.

## Governance Artifacts

- [Spectral Rules](rules/marine-traffic-rules.yml) — server base, api_key path, title-case summaries, tag taxonomy, JSON content type, protocol enum
- [Domain Vocabulary](vocabulary/marine-traffic-vocabulary.yml) — vessel / port / AIS / move-type / data-source taxonomies
- [JSON-LD Context](json-ld/marine-traffic-context.jsonld) — schema.org + WGS-84 + ITU-R AIS bridge classes

## Use Cases

- Commodity trading and freight intelligence
- Port operations and logistics
- Fleet dashboards and customer-facing vessel tracking
- Compliance and sanctions monitoring (AIS gaps, dark fleet, port-call patterns)
- Marine insurance underwriting (hull / P&I / route)
- Coast guard and government maritime domain awareness
- Carbon / ESG reporting and voyage CO2 estimation

## Maintainers

- **Kin Lane** · [apievangelist.com](https://apievangelist.com) · `info@apievangelist.com` · X: [@apievangelist](https://x.com/apievangelist)
