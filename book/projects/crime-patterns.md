# Crime Patterns Webmap

:::{div}
:class: project-hero
**Crime Patterns Webmap**

Interactive crime analytics webmap with server-side aggregation for fast heatmap insights.
{span}`Leaflet • PHP • PostGIS`
:::

:::{div}
:class: project-meta
**Stack:** Leaflet, Bootstrap, jQuery, PHP (PDO), PostGIS  
**Data:** City-level crime incidents with spatial geometry  
**Goal:** Explore hotspots, trends, and category breakdowns by place and time
:::

## Live Webmap

:::{div}
:class: full-bleed-embed
<iframe
  src="https://crime-patterns.kunmiadebanjo.com/"
  class="full-bleed-iframe"
  loading="lazy"
  referrerpolicy="strict-origin-when-cross-origin"
  allowfullscreen>
</iframe>
:::

For a better experience, click [here](https://crime-patterns.kunmiadebanjo.com/).

## Project Overview

Crime Patterns is a city-focused analytics webmap that makes it easy to explore reported crime incidents across time, location, and category. The frontend provides interactive basemaps and filters, while the backend performs server-side aggregation to produce performant heatmap layers and summary statistics.

## Why It Matters

- **Situational awareness:** Highlights hotspot clusters and temporal shifts for public safety insights.
- **Exploratory analysis:** Enables quick filtering by city, date range, and occurrence category.
- **Performance at scale:** Heatmap aggregation reduces client load on large datasets.
- **Decision support:** Summaries and time-series breakdowns help compare periods and categories.

## Key Features

- **Interactive map** with multiple basemaps and layers.
- **Server-side heatmap** aggregation for large datasets.
- **Dynamic filters** for city, date range, and occurrence category.
- **Summary stats** and top groups/types for quick context.
- **Point layer** with tooltips for incident-level inspection.

## Architecture

**Frontend**
- Leaflet map UI with filters, heatmap, and point layers.
- Bootstrap and jQuery for layout and interactions.
- UI widgets and plugins for enhanced map controls.

**Backend**
- PHP endpoints that return GeoJSON, aggregated heat points, and stats.
- Token-based write security (configurable, if enabled).

**Database**
- PostgreSQL + PostGIS with a `crimes_master` table containing geometry and attributes.

## Data Model Requirements

Key fields used in the app:

- `crime_database_id` (integer)
- `date_reported` (date)
- `reported_date` (varchar)
- `reported_day` (integer)
- `reported_month` (integer)
- `reported_year` (varchar)
- `occurrence_category` (varchar)
- `occurrence_group` (varchar)
- `occurrence_type_group` (varchar)
- `intersection` (varchar)
- `objectid` (integer)
- `province` (text)
- `city_name` (text)
- `geom` (geometry, MultiPoint, SRID 4326)

Recommended indexes:

```sql
CREATE INDEX crimes_master_geom_gix ON crimes_master USING GIST (geom);
CREATE INDEX crimes_master_date_idx ON crimes_master (date_reported);
CREATE INDEX crimes_master_city_idx ON crimes_master (city_name);
```

## API Endpoints

All endpoints accept POST parameters.

- `api_calls/load_crimes.php`  
  Returns GeoJSON points for the selected filters.
- `api_calls/heat_crimes.php`  
  Returns aggregated heatmap points (optional `grid_size`).
- `api_calls/stats_crimes.php`  
  Returns summary stats and time-series breakdowns.
- `api_calls/cities.php`  
  Returns available cities.
- `api_calls/categories.php`  
  Returns categories for a selected city.
- `api_calls/latest_date.php`  
  Returns the latest report date by city.

## Configuration

Create a config file or use environment variables:

```
/Applications/XAMPP/xamppfiles/htdocs/config/db.php
```

Supported environment variables:

- `WEBMAP_DSN`
- `WEBMAP_DB_USER`
- `WEBMAP_DB_PASS`
- `WEBMAP_WRITE_TOKEN`

## Local Run (XAMPP)

1. Start Apache (and PostgreSQL if local).
2. Place the project in your web root.
3. Open the site in a browser and test the filters.

## Suggested Improvements

- Add cached aggregation for frequently queried views.
- Replace the time-series list with a charting library (ECharts/Chart.js).
- Add occurrence group/type filters and saved filter presets.
- Explore vector tiles or hexbin aggregation for smoother zoom behavior.
