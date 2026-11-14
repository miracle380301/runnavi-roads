# runnavi-roads

Pre-built road tiles for the RunNavi app's shape runs, so the app does not depend on public Overpass servers.

- Tiles: `<region>/<lat>/<lon>.bin` — a 0.02° cell whose south-west corner is `(lat, lon) × 0.02°`.
- Content: raw DEFLATE of `{"v":1,"ways":[{"i":<OSM way id>,"t":{tags},"g":[delta-encoded lat/lon in 1e-7°]}]}`.
- `index.json` lists the regions that are covered. A tile inside a region that 404s is not covered.
- Empty tiles (sea, no runnable roads) are stored as an empty `ways` list.

Map data © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors, available under the Open Database License (ODbL) 1.0.
Built from the Geofabrik South Korea extract with `tools/roads/build_road_tiles.py` in the app repository.
