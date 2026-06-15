# MarineTraffic (marine-traffic)

MarineTraffic is the leading maritime intelligence and AIS ship-tracking platform — now part of Kpler. The MarineTraffic AIS Data API exposes the same live + historical vessel positions, port calls, berth calls, vessel master data, voyage forecasts, predictive arrivals, port-congestion analytics, sea-lane routing, reverse geocoding, and fleet management endpoints that power the public marinetraffic.com map and the Kpler maritime data services. Data is sourced from 13,000+ terrestrial AIS receivers plus satellite AIS, served as REST/JSON (with CSV / XML / JSONO alternatives), authenticated via a per-key prepaid credit balance, and metered in credits per response row with per-service refresh-interval caching.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/marine-traffic/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/marine-traffic/refs/heads/main/apis.yml)

## Scope

- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- AIS
- Maritime
- Vessel Tracking
- Shipping
- Ports
- Voyage Forecasting
- Geospatial
- Kpler

## Timestamps

- **Created:** 2026-05-25T00:00:00.000Z
- **Modified:** 2026-05-25

## APIs

### MarineTraffic Vessel Positions API

Real-time and historical AIS vessel positions sourced from 13,000+ terrestrial AIS receivers and satellite AIS feeds. Query by single vessel (MMSI / IMO / SHIP_ID), by fleet, by predefined area of interest, by port, or by a custom bounding box. Includes both the modern AIS API (`/exportvessels`, `/exportvessel`, `/exportvessels-custom-area` — MTA030AD-family with cursor pagination) and the legacy PS01–PS08 surface, plus the Vessel Historical Track endpoint (`/exportvesseltrack`) for replaying a vessel's track over a defined window.

- **Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

#### Tags

- AIS
- Maritime
- Vessel Tracking
- Vessel Positions

#### Properties

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-vessel-positions-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marine-traffic-vessel-positions.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marine-traffic-vessel-positions.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/marine-traffic-vessel-position-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/marine-traffic-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Example](examples/marine-traffic-vessel-position-example.json)

### MarineTraffic Events API

Port calls, berth calls, and event timelines — surfaces every arrival, departure, and berth touch detected by the MarineTraffic AIS network. Scope by vessel (`/portcalls`, `/vesselevents`, `/berth-calls` with MMSI/IMO/SHIP_ID) or by port (same endpoints scoped with port_id / UNLOCODE / berth_id / terminal_id). Returns voyage duration, time-in-port, draught, market segment, and full vessel/port keys for downstream joining.

- **Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

#### Tags

- AIS
- Maritime
- Port Calls
- Berth Calls
- Events

#### Properties

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-events-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marine-traffic-events.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marine-traffic-events.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/marine-traffic-port-call-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [Example](examples/marine-traffic-port-call-example.json)

### MarineTraffic Vessels Data API

Vessel master data (`/vesselmasterdata`), vessel photographs (`/exportvesselphoto`), and the ship-database search surface (`/shipsearch` by identifier or by name). Returns the full static AIS record plus MarineTraffic enrichments — owner, manager, builder, classification society, build year, dimensions, deadweight, gross tonnage, and current operational status.

- **Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

#### Tags

- AIS
- Maritime
- Vessel Database
- Search

#### Properties

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-vessels-data-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marine-traffic-vessels-data.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marine-traffic-vessels-data.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/marine-traffic-vessel-master-schema.json) — [JSON Schema](https://json-schema.org/specification)

### MarineTraffic Voyage Information API

Machine-learning–powered voyage intelligence: voyage forecast (`/voyageforecast`), predictive destination areas (`/predictive-destination-areas`), and ETA-to-port (`/etatoport`). Combines live AIS positions, port-call history, and predictive routing to deliver destination predictions with probability scores, ranked alternative destination ports, and predictive ETAs that outperform raw AIS-broadcast ETAs.

- **Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

#### Tags

- AIS
- Maritime
- Voyage Forecasting
- Predictive Intelligence
- ETA

#### Properties

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-voyage-info-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marine-traffic-voyage-info.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marine-traffic-voyage-info.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/marine-traffic-voyage-forecast-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [Example](examples/marine-traffic-voyage-forecast-example.json)

### MarineTraffic Ports Information API

Port-centric analytics: expected port arrivals (`/expectedarrivals`), predictive arrivals using MarineTraffic's destination model (`/predictive-arrivals`), and port-congestion intelligence (`/port-congestion`) with anchorage-time, in-port-time, vessels-in-port, and call-count metrics aggregated by market or ship class for a given port and ISO week.

- **Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

#### Tags

- AIS
- Maritime
- Ports
- Port Congestion
- Predictive Arrivals

#### Properties

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-ports-info-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marine-traffic-ports-info.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marine-traffic-ports-info.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/marine-traffic-port-schema.json) — [JSON Schema](https://json-schema.org/specification)

### MarineTraffic Routing Information API

Maritime route generation and distance calculation across global sea lanes via `/exportroutes`. Compute the great-circle or sea-lane-aware route from a vessel's current position (MMSI/IMO/SHIP_ID) — or an arbitrary origin port / LAT-LON pair — to a target port, with optional inland-waterway and alternative-route inclusion.

- **Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

#### Tags

- AIS
- Maritime
- Routing
- Distance

#### Properties

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-routing-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marine-traffic-routing.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marine-traffic-routing.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MarineTraffic Reverse Geocoding API

Maritime-aware reverse geocoding (`/reversegeocode`) — resolves a single coordinate pair to the nearest port, anchorage, terminal, berth, or standard / custom area within a configurable radius. The single geographic primitive in the API; useful for tagging AIS positions with port and berth context.

- **Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

#### Tags

- AIS
- Maritime
- Geocoding
- Geographic

#### Properties

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-reverse-geocoding-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marine-traffic-reverse-geocoding.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marine-traffic-reverse-geocoding.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MarineTraffic Power User API

Power-user administration surface: fleet CRUD (`/setfleet`, `/getfleet`, `/getfleets`, `/clearfleet`), API credit-balance inspection (`/exportcredits` — free), and passage-plan import (`/import-passage-plan`, POST). Used to maintain customer fleet definitions, monitor credit burn, and push voyage plans into the MarineTraffic platform.

- **Human URL:** [https://servicedocs.marinetraffic.com/](https://servicedocs.marinetraffic.com/)

#### Tags

- AIS
- Maritime
- Fleet Management
- Account
- Passage Plans

#### Properties

- [Documentation](https://servicedocs.marinetraffic.com/)
- [OpenAPI](openapi/marine-traffic-power-user-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marine-traffic-power-user.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marine-traffic-power-user.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://www.marinetraffic.com/)
- [Documentation](https://servicedocs.marinetraffic.com/)
- [API Reference](https://servicedocs.marinetraffic.com/)
- [Portal](https://www.kpler.com/product/maritime/data-services)
- [Support](https://support.marinetraffic.com/en/articles/9552659-api-services)
- [Errors](https://support.marinetraffic.com/en/articles/9552800-api-most-common-response-error-codes)
- [Documentation](https://support.marinetraffic.com/en/articles/9552860-what-kind-of-information-is-ais-transmitted)
- [Support](https://support.marinetraffic.com/)
- [Sandbox](https://www.marinetraffic.com/en/ais/home)
- [GitHub Organization](https://github.com/marinetraffic)
- [Tool](https://github.com/marinetraffic/mt-ais-toolbox)
- [LinkedIn](https://www.linkedin.com/company/marinetraffic)
- [Twitter](https://twitter.com/MarineTraffic)
- [OpenAPI](openapi/marine-traffic-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Spectral Rules](rules/marine-traffic-rules.yml)
- [Vocabulary](vocabulary/marine-traffic-vocabulary.yml)
- [JSON-LD](json-ld/marine-traffic-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Plans](plans/marine-traffic-plans-pricing.yml)
- [Rate Limits](rate-limits/marine-traffic-rate-limits.yml)
- [Fin Ops](finops/marine-traffic-finops.yml)
- [Features](undefined)
- [Use Cases](undefined)
- [Integrations](undefined)
- [Solutions](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
