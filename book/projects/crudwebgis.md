# CRUD Web GIS: Build Process

:::{div}
:class: project-hero
**CRUD Web GIS: Build Process**

Interactive webmap for CRUD operations on spatial layers with Leaflet and PostGIS.
{span}`Leaflet • PHP • PostGIS`
:::

:::{div}
:class: project-meta
**Stack:** Leaflet, PHP, PostGIS  
**Data:** Infrastructure layers (valves, pipelines, buildings)  
**Goal:** Enable CRUD workflows directly on the map
:::

Get started by clicking the home button 🏠 at the top left and filtering to your desired locality. Create features, update attributes and delete features below 👇. 

## Live Webmap

:::{div}
:class: embed-section
**Live Webmap**
:::

:::{div}
:class: full-bleed-embed
<iframe
  src="https://webmap.kunmiadebanjo.com/"
  class="full-bleed-iframe"
  loading="lazy"
  referrerpolicy="strict-origin-when-cross-origin"
  allowfullscreen>
</iframe>
:::

If the embed does not load, open: https://webmap.kunmiadebanjo.com/

## How to Use the Webmap

1. Open the live webmap and choose a DMA from the sidebar to load features.
2. Click a feature to inspect attributes in the popup.
3. Use the edit tools in the popup to update or delete a feature.
4. Use the sidebar forms to add new valves, pipelines, or buildings.

## Quick Overview

- **Stack**: Leaflet + Bootstrap + jQuery on the frontend; PHP API with PostGIS on the backend.
- **Core layers**: valves (points), pipelines (lines), buildings (polygons).
- **Primary flows**: load by DMA, inspect with tooltips/popups, edit or delete in-place, insert via sidebar forms.

## Architecture

- Frontend: Leaflet map UI with plugins, AJAX calls to PHP endpoints, GeoJSON rendering.
- Backend: PHP API endpoints for CRUD and lookup operations.
- Database: PostGIS-enabled PostgreSQL (inferred from `ST_AsGeoJSON` and `ST_GeomFromGeoJSON`).

### High-level flow

1. User loads the webmap and selects a DMA (area filter).
2. Frontend calls backend endpoints to load features by DMA.
3. GeoJSON is returned and rendered by Leaflet with styling and tooltips/popups.
4. Edits and deletes occur from popups, inserts from sidebar forms, all handled via AJAX POST to PHP endpoints.

## Frontend build (Leaflet UI)

Key file: `index.php`

### Libraries and plugins

- Leaflet 1.7
- Bootstrap 3.4 for layout and form styling
- jQuery + jQuery UI (autocomplete)
- Leaflet Sidebar (tabbed sidebar)
- Leaflet Geoman (drawing tools)
- Leaflet PolylineMeasure (measurement tool)
- MiniMap and ZoomBar controls
- SweetAlert2 for confirmation dialogs

### Map setup

- Base layers: Google Streets, OpenStreetMap, CartoDB Positron, Esri World Imagery, OpenTopoMap
- Controls: sidebar, layer control, scale, minimap, polyline measure, geoman drawing
- Default view: centered around `[23.7923, 90.4167]` with zoom 13

### Layer logic

- **Valves**: point layer with circle markers, styled by `valve_type`.
- **Pipelines**: line layer styled by `pipeline_category`.
- **Buildings**: polygon layer styled by `building_category` and `building_storey`.

Each layer includes:

- Tooltip for quick inspection
- Popup form with editable attributes and Update/Delete actions
- Autocomplete search by ID (valve_id, pipe_id, account_no)

### Drawing + insert workflow

Geoman drawing creates a geometry, then writes GeoJSON into a hidden textarea:

- Marker -> Point (valves)
- Line -> MultiLineString (pipelines)
- Polygon -> MultiPolygon (buildings)

Insert forms collect attributes + geometry and POST to `insert_data.php`.

## Backend build (PHP + PostGIS)

Key files: `init.php`, `load_data.php`, `find_data.php`, `insert_data.php`, `update_data.php`, `delete_data.php`

### Database connection

`init.php` reads database config from `/home/kunmiade/config/db.php` or environment variables:

- `WEBMAP_DSN`
- `WEBMAP_DB_USER`
- `WEBMAP_DB_PASS`

If config is missing, the API exits with an error.

### Write security token

Write operations require a token (via header `X-WEBMAP-TOKEN` or POST `token`).
Token is read from config or `WEBMAP_WRITE_TOKEN` environment variable.

### Read endpoints

- `load_data.php`: loads features for a selected DMA
- `find_data.php`: returns a feature by ID

Both endpoints return GeoJSON FeatureCollections using `ST_AsGeoJSON(geom)`.

### Write endpoints

- `insert_data.php`: validates unique IDs, inserts with `ST_GeomFromGeoJSON` and SRID 4326
- `update_data.php`: updates attributes with checks for unique IDs
- `delete_data.php`: deletes by database primary key

## Data model (as used by the app)

Tables referenced by the frontend:

- `valves`
  - ids and attributes: `valve_id`, `valve_type`, `valve_dma_id`, `valve_diameter`, `valve_visibility`, `valve_location`
  - geometry: `geom`
- `pipelines`
  - ids and attributes: `pipe_id`, `pipeline_category`, `pipeline_dma_id`, `pipeline_diameter`, `pipeline_material`, `pipeline_location`, `length`
  - geometry: `geom`
- `buildings`
  - ids and attributes: `account_no`, `building_category`, `building_dma_id`, `building_storey`, `building_population`, `building_location`
  - geometry: `geom`

## Deployment notes

- The live webmap serves the same PHP-based frontend and backend.
- Make sure the server includes PHP + PDO + PostGIS support.
- Store database credentials and the write token in in an external directory e.g `/home/kunmi/config/db.php` or environment variables to avoid exposing secrets in source control.

## What I would improve next

- Move hardcoded base layers and API paths into a config file.
- Add input validation and server-side request rate limiting.
- Use prepared geometry validation to avoid invalid shapes.
- Add a lightweight authentication screen or user roles for write access.
- Add backups and migrations for the spatial database.
- Use GDAL for raster layer tiling as optional overlay for AOCs
