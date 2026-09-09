# HK Bus Live

A professional, responsive Hong Kong KMB/LWB real-time bus arrival web app.

## Features

- Real-time stop-wide ETA data with up to the next three arrivals per route
- Live Hong Kong clock plus countdown ETA and exact ETA clock time
- Bus stop name search using the official KMB/LWB stop directory
- Improved same-name-stop dropdown with coordinates, STOP ID, and pole code when available
- Interactive map picker: search on the map, tap the exact stop marker, then use that stop
- Nearby-stop discovery using browser geolocation
- Direct 16-character STOP ID lookup
- Saved stops and saved route preferences with localStorage
- Saved-stop Edit mode with individual removal, multi-select, Select all, and Remove selected
- Route/destination filtering
- Automatic 60-second refresh and manual refresh
- Traditional Chinese / English interface with matched component sizing so switching language does not shift the main layout
- Light / dark mode
- Responsive desktop and mobile UI
- Search results expand in normal document flow instead of overlapping the saved-stop/data panels
- Mobile-safe header, ETA cards, saved-stop editor, map dialog, and safe-area spacing
- Footer credit: Designed by Lemon in California
- Static deployment with no build system required
- Starts with no bus stop selected; live ETA appears only after the user explicitly chooses a stop

## Bus-stop map and duplicate names

The **地圖找站 / Find on map** button replaces the previous demo-stop button. It uses the official KMB/LWB stop coordinates to place bus-stop markers on an OpenStreetMap base map.

This is useful when several physical stops have the same public name. The search dropdown now distinguishes those stops by location and official STOP ID. Where OpenStreetMap provides a `local_ref`, the app also displays the familiar pole code such as `KT646`. Pole-code lookup is optional and cached locally; if that lookup is unavailable, the official coordinates and STOP ID remain available.

## Data sources

Official KMB/LWB data:

- `https://data.etabus.gov.hk/v1/transport/kmb/stop`
- `https://data.etabus.gov.hk/v1/transport/kmb/stop-eta/{stop_id}`

Map / optional stop-reference support:

- OpenStreetMap map tiles
- OpenStreetMap Overpass API for optional bus-stop `local_ref` values
- Leaflet 1.9.4 for the interactive map

OpenStreetMap attribution is displayed directly on the map.

## Run locally

For the most reliable browser permissions and API behavior, serve the folder with a local web server:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Deploy

Upload the folder to Netlify, GitHub Pages, Cloudflare Pages, or another static host. Keep `index.html` at the project root.

## Notes

- ETA values are estimates and can change due to real traffic conditions.
- Nearby-stop and map location features require the user to grant browser location permission only when location is requested.
- The official stop directory is cached locally for 12 hours.
- Optional pole-code results are cached locally after they are found.
- The map requires an internet connection for OpenStreetMap tiles and Leaflet's CDN assets.
- The app intentionally does not restore the previously viewed stop when the page is reopened or refreshed.

## Saved-stop shortcut editing

The left-side **Saved stops / 收藏車站** panel has an Edit button. In Edit mode, tap a row or its checkbox to select it, use the individual remove button to delete one stop, or choose **Select all / 全選** and then **Remove selected / 移除已選** to clear all saved stops. Route favourites remain separate from the left-side stop shortcut list.

## Bilingual layout stability

The Chinese and English interfaces use matched button widths, fixed title/metadata regions, fixed search-result row heights, and constrained route-card text areas. This prevents the main navigation, stop header, saved-stop controls, and route cards from expanding or shrinking when the language changes.
