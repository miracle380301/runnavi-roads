# runnavi-roads

Pre-built road tiles for the RunNavi app's shape runs, so the app does not depend on public Overpass servers.

- Tiles: `<region>/<lat>/<lon>.bin` — a 0.02° cell whose south-west corner is `(lat, lon) × 0.02°`.
- Content: raw DEFLATE of `{"v":1,"ways":[{"i":<OSM way id>,"t":{tags},"g":[delta-encoded lat/lon in 1e-7°]}]}`.
- `<region>-paths/<lat>/<lon>.bin` — same format, for the app's Nearby Paths: footways, pedestrian streets, paths, cycleways, plus rivers/streams/canals and coastlines (with `name`, `foot`, `access` and similar tags).
- `index.json` lists the regions that are covered (`path` = roads layer, `paths` = nearby-paths layer). A tile inside a region's bounds that 404s has no roads (open sea, etc.) — the app treats it as an empty tile.
- Empty tiles (sea, no runnable roads) are stored as an empty `ways` list.

Map data © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors, available under the Open Database License (ODbL) 1.0.
Built from Geofabrik extracts with `tools/roads/build_road_tiles.py` and `build_path_tiles.py` in the app repository.

Regions: `kr` (all of South Korea), `jp-tokyo` (35.30–36.00°N, 139.20–140.20°E: Tokyo, Yokohama, Kawasaki, Chiba, Saitama), `jp-osaka` (34.30–35.20°N, 135.00–136.00°E: Osaka, Kobe, Kyoto, Nara).
