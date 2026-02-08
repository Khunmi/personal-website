# Building a Web Map with the Esri JavaScript API

:::{div}
:class: project-hero
**Building a Web Map with the Esri JavaScript API**

Lightweight web map built with the ArcGIS JS API and local GeoJSON layers.
{span}`ArcGIS JS API • GeoJSON • HTML`
:::

:::{div}
:class: project-meta
**Stack:** ArcGIS JavaScript API, HTML, GeoJSON  
**Data:** Local GeoJSON layers (boundaries, lines, points)  
**Goal:** Build an embeddable web map with clean styling, widgets, and popups
:::

## Live Webmap

:::{div}
:class: full-bleed-embed
<iframe
  src="https://esrijsapi.kunmiadebanjo.com/"
  class="full-bleed-iframe"
  loading="lazy"
  referrerpolicy="strict-origin-when-cross-origin"
  allowfullscreen>
</iframe>
:::

If the embed does not load, click [here](https://esrijsapi.kunmiadebanjo.com/).

## Project Overview

This project is a lightweight web map that uses the ArcGIS JavaScript API to render local GeoJSON layers. It focuses on clean symbology, quick loading, and a simple HTML-based setup you can run on a local server.

## What This Project Does

- Loads a basemap from the ArcGIS JS API.
- Overlays multiple local GeoJSON layers.
- Styles each layer with attribute-driven symbology.
- Adds widgets for navigation, search, and map interaction.
- Displays popups and labels to explain features.

## Project Structure

- `webmap.html`  
  Single-page app with map, layers, and widgets.
- `files/`  
  Local GeoJSON data for boundaries, lines, and points.

## Tools and Dependencies

- ArcGIS JavaScript API 4.20 loaded from the Esri CDN.
- A local web server such as XAMPP or Apache.
- A modern browser.

## How the Map Is Organized

Inside `webmap.html` the code is organized into small functions:

- `createDmaBoundaryLayer()`
- `createZoneBoundaryLayer()`
- `createTransmissionLinesLayer()`
- `createDeepTubeWellLayer()`
- `createDmaChamberLayer()`

Each function builds a `GeoJSONLayer` with:

- A `url` pointing to a GeoJSON file in `files/`.
- A renderer to control colors and line widths.
- A popup template.
- Optional labeling.

Widgets are added in a dedicated `addWidgets(view)` function.

## Data Layers

The project uses five GeoJSON layers:

- DMA boundaries, symbolized by status.
- Zone boundaries, shown as outlines with labels.
- Transmission lines, styled by diameter.
- Deep tube wells as points.
- DMA chambers, styled by type.

Each layer expects specific attribute fields in the GeoJSON. If a field name changes, the renderer or popup will break until updated.

## Setup and Run

1. Place the project folder under your local web server `htdocs`.
1. Start Apache.
1. Open the map in your browser. Example:
   - `http://localhost/esri_jv_api/esri_javascript_api/webmap.html`

Avoid opening the file directly with `file://` because browsers block local file requests.

## Key Implementation Steps

1. Load the ArcGIS JS API in the HTML `head`.
1. Create a `Map` and `MapView`.
1. Build `GeoJSONLayer` instances with renderers and popup templates.
1. Add the layers to the map.
1. Add UI widgets like LayerList, Legend, Search, and Locate.

## Common Issues and Fixes

- No layers show up: confirm Apache is running and file paths are correct.
- CORS errors: use `http://localhost` rather than opening the file directly.
- Labels missing: verify the attribute names in your GeoJSON.

## Why This Approach Works

The ArcGIS JS API handles all rendering in the browser. GeoJSON files provide a simple, local data format that is easy to edit and version. This makes it a clean starting point before moving to hosted feature services or more complex GIS infrastructure.

## Next Steps

- Move GeoJSON into hosted feature layers for scalability.
- Add edit workflows using FeatureLayers and an enterprise geodatabase.
- Split config from logic into a JSON or JS config file.
