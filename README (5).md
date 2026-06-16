# Airscape

**A living map of the air.**

Airscape turns hourly air-quality data into a moving picture of the atmosphere over any place on Earth. Pollution appears as colour and motion: cool teal for cleaner air, shifting through amber to deep red as levels rise. Haze drifts across the map with the real wind, hotspots glow along major roads, and a timeline lets you replay the past month or look four days ahead.

**Live site:** https://rohit-rcrohit7.github.io/airscape/

## Features

### Anywhere on Earth
- Search any **city, street address or postcode**, with a suggestions dropdown; precise addresses zoom to street level.
- Tap **⌖** to centre on your own position, with a live-tracked marker that follows you as you move.
- Every relocation fetches fresh data for that area: air quality, wind, roads.

### Live, rolling data
- Hourly values for the most recent **31 days plus a 4-day forecast** — never a frozen snapshot.
- While the page is open, the present edge refreshes every **15 minutes**.
- Drag the timeline hour by hour, press ▶ for a timelapse, or jump back with **NOW**. Forecast hours are labelled in amber.

### Pollutants and indexes
- **PM2.5, PM10, NO₂, O₃, SO₂ and CO** everywhere.
- **Grass pollen** across Europe, including the UK, in season.
- **UK:** the header shows the official **DAQI** (Daily Air Quality Index, 1–10, low → very high) computed with Defra/COMEAP concentration bands. Tap the badge to switch to the European **EAQI** and back.
- **Europe:** the EAQI appears automatically.

### Visual layers (each toggleable)
- **▦ heatmap** — a smooth colour surface of estimated concentration across the whole viewport.
- **∴ haze** — drifting particles whose direction and speed follow the real recorded or forecast wind for the hour being viewed, and whose colour, size and turbulence follow pollution levels.
- **— roads** — major roads from OpenStreetMap, drawn with weight so the emission hierarchy (motorway → primary) is visible.
- **♪ noise** (England only) — Defra's official strategic road-noise map (Round 4, modelled 2022) streamed live from the Defra Data Services Platform. While it's on:
  - **tap anywhere** to read the decibel value at that exact spot (Lden, annual average);
  - the traffic emission weighting upgrades from road class to **noise-derived** — the app reads the service's own legend to map colours back to dB, samples the viewport as a raster, and converts noise intensity into emission weights that track real traffic.

### Reading the map
- **Hover** anywhere for a quick floating readout of the estimated value at that point, named and banded (e.g. "NO₂ 28.4 µg/m³ · moderate").
- **Click anywhere** to pin that spot and open a full info panel: the reverse-geocoded place name, the value and band for the active pollutant plus a compact grid of every other pollutant at that point, the local DAQI/EAQI, and a trend graph spanning the last 48 hours flowing into the forecast. The pollutant chips switch the map; the underlined labels signpost straight into the relevant section of the in-app guide.
- A **wind compass** shows the real wind (direction and speed) driving the haze for the hour on the timeline.
- A built-in **guide** explains every control, the colour bands, and the health effects of each pollutant alongside WHO 2021 guideline levels.

## How it works

Airscape is a single self-contained HTML file — no build step, no backend, no API keys. Leaflet renders the basemap; two canvas layers on top render the heatmap surface and the particle field. Concentrations are sampled at several points around the chosen location, blended into a continuous field by inverse-distance interpolation, and shaped near roads by an emission weighting (road class by default; Defra noise-derived in England when the noise layer is on). The diurnal traffic cycle modulates road contributions through the day.

## Data sources

| Data | Source |
|---|---|
| Air quality & 4-day forecast | CAMS (Copernicus Atmosphere Monitoring Service) via the Open-Meteo Air Quality API, hourly |
| Wind (recorded & forecast) | Open-Meteo |
| Basemap & road geometry | OpenStreetMap contributors; dark basemap style by CARTO; roads via Overpass API |
| Geocoding & address search | Nominatim (OpenStreetMap) |
| Road noise (England) | Defra strategic noise mapping Round 4 (WMS), © Department for Environment, Food & Rural Affairs 2023, Open Government Licence |
| EAQI | CAMS via Open-Meteo |
| DAQI | Computed in-app from Defra/COMEAP concentration bands |

## limitations

- Air-quality values are **model estimates** (CAMS), not physical sensor readings, and can differ from street-level monitors, especially beside busy roads. I will be working to add stationary monitors data.
- The DAQI shown is computed from **current hourly values** as a proxy for the official averaging periods (24-hour particles, 8-hour ozone), so it reacts faster than the official figure.
- Road-class emission weighting is an approximation; the noise-derived weighting (England) tracks traffic better but is still indicative, not measured air.
- The Defra noise map road overlay is a **long-term annual model**, not live noise.
- Forecast hours carry more uncertainty the further ahead you look.

## Contact

Created by **Rohit Chakraborty**
📧 rcrohit7@gmail.com

Feedback, ideas and collaboration enquiries are welcome.

## Copyright

© 2026 Rohit Chakraborty. All rights reserved.

This software and its design, code and content may not be copied, modified, distributed or used, in whole or in part, without prior written permission from the author. Map data © OpenStreetMap contributors; basemap tiles © CARTO; air-quality data © Copernicus Atmosphere Monitoring Service via Open-Meteo; road-noise data © Department for Environment, Food & Rural Affairs 2023, used under the Open Government Licence v3.0 — each subject to its own licence and attribution requirements.
