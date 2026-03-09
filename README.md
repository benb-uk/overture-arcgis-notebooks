overture-arcgis-notebooks
Cloud-native spatial analysis using ArcGIS Online Notebooks, DuckDB and Overture Maps Foundation data. No data is downloaded or permanently stored — DuckDB queries Overture GeoParquet directly from S3, and only the analysis output is saved to ArcGIS Online.

Notebooks
Pubs from Liverpool Street Station
Queries Overture Maps place data for pubs and bars within a bounding box around Liverpool Street, then uses the ArcGIS OD Cost Matrix service to calculate real walking distances along the street network from the station to each one.

Outputs:

Dot map of pub locations symbolised by walking time band
Heatmap showing where pubs cluster within 10 minutes on foot
Enriched pub point layer saved to ArcGIS Online with walking times
How it works
Overture Maps GeoParquet on S3
        ↓
DuckDB — SQL query filtered to bounding box, no full dataset download
        ↓
ArcGIS Python API — geometry conversion, spatial accessor
        ↓
ArcGIS OD Cost Matrix GP service — walking distances along street network
        ↓
ArcGIS Online — analysis output layer only
Requirements
ArcGIS Online account with Notebooks enabled (Standard or Advanced runtime)
DuckDB available in the notebook runtime (ArcGIS Notebook Python 3 Standard 13.0+)
ArcGIS Online credits for the OD Cost Matrix service
Dependencies
All available in the ArcGIS Online notebook runtime — no additional installs required.

duckdb
arcgis
pandas
matplotlib
Data
Overture Maps Foundation place data, licensed under CDLA Permissive 2.0. Queried directly from s3://overturemaps-us-west-2.

Street network routing via the ArcGIS Logistics OD Cost Matrix service, powered by HERE.

Usage
Open the notebook in ArcGIS Online Notebooks
Run all cells in order
Adjust xmin, ymin, xmax, ymax to change the area of interest
Adjust STATION_X, STATION_Y and the origin name to change the origin point
Adjust the category filter in the SQL query to change the place type
Notes
The Overture release version is set in RELEASE — update this to the latest release as needed. Current releases are listed at overturemaps.org
The heatmap cell publishes a temporary layer to ArcGIS Online to apply the renderer, which is deleted immediately after viewing
OD Cost Matrix credit consumption depends on the number of destinations — 616 destinations cost approximately 1.25 credits in testing
License
MIT
