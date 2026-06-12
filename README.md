# Airscape

**A living map of the air.**

Airscape turns hourly air-quality data into a moving picture of the atmosphere over any place on Earth. Pollution appears as colour and motion: cool teal for cleaner air, shifting through amber to deep red as levels rise. Haze drifts across the map with the real wind, hotspots glow along major roads, and a timeline lets you replay the past month or look four days ahead.

**Live site:** https://rohit-rcrohit7.github.io/airscape/

## Features

- **Live, rolling data** — hourly values for the most recent 31 days plus a 4-day forecast, refreshed every 15 minutes while the page is open. Never a frozen snapshot.
- **Anywhere on Earth** — search any city, street address or postcode (with suggestions), or tap ⌖ to centre on your own live-tracked location.
- **Multiple pollutants** — PM2.5, PM10, NO₂, O₃, SO₂ and CO everywhere; in Europe the official EAQI index and grass pollen appear automatically where available.
- **Three layers** — a smooth heatmap surface, wind-driven haze particles, and major-road emission corridors, each toggleable.
- **Timeline scrubbing** — drag through a month hour by hour, play a timelapse, or jump back to NOW. Forecast hours are clearly labelled.
- **Hover to probe** — read the estimated value at any exact point on the map.
- **Built-in guide** — what every control means, how to read the colours, and the health effects of each pollutant alongside WHO 2021 guideline levels.

## Data sources

| Data | Source |
|---|---|
| Air quality & forecast | CAMS (Copernicus Atmosphere Monitoring Service) via the Open-Meteo Air Quality API, hourly |
| Wind (recorded & forecast) | Open-Meteo |
| Basemap & road geometry | OpenStreetMap contributors; dark basemap style by CARTO; roads via Overpass API |
| Geocoding & address search | Nominatim (OpenStreetMap) |

Air-quality values are model estimates, not physical sensor readings, and can differ from street-level monitors. Road emission weighting is an approximation based on road class, not live traffic counts; hotspot shapes near roads are indicative.

## Running it

Airscape is a single self-contained HTML file with no build step and no API keys.

- **Online:** open the live site above.
- **Locally:** download `index.html` and open it in any modern browser.

Note: the ⌖ location feature requires a secure context (https or a local file), which GitHub Pages provides.

## Contact

Created by **Rohit Chakraborty**
📧 rcrohit7@gmail.com

Feedback, ideas and collaboration enquiries are welcome.

## Copyright

© 2026 Rohit Chakraborty. All rights reserved.

This software and its design, code and content may not be copied, modified, distributed or used, in whole or in part, without prior written permission from the author. Map data © OpenStreetMap contributors; basemap tiles © CARTO; air-quality data © Copernicus Atmosphere Monitoring Service via Open-Meteo — each subject to its own licence and attribution requirements.
