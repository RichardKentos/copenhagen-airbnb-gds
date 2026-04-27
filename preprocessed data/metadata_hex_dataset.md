# Hex Dataset Metadata

## File
- Primary handoff layer: `preprocessed data/hex_listing_aggregates_epsg25832.parquet`
- Companion files:
  - `preprocessed data/hex_listing_aggregates_epsg25832.geojson`
  - `preprocessed data/hex_listing_aggregates_epsg25832.csv`

## Spatial specification
- Spatial unit: H3 hexagons
- H3 resolution: `8`
- Geometry type: Polygon
- CRS: `EPSG:25832` (ETRS89 / UTM zone 32N, meters)

## Source and preprocessing
- Source snapshot: `data/copenhagen-listings.csv` (Inside Airbnb Copenhagen)
- Built in: `preprocess.ipynb`
- Main cleaning operations:
  - price parsing from string to numeric (`price_float`)
  - removal of rows with missing required fields (`price`, `latitude`, `longitude`)
  - coordinate validity filtering
  - price outlier filtering with IQR rule (1.5 * IQR)

## Key columns
- `h3_id`: H3 cell id
- `listing_count`: number of listings in hex
- `median_price`: median nightly price in hex
- `mean_price`: mean nightly price in hex
- `min_price`: minimum nightly price in hex
- `max_price`: maximum nightly price in hex
- `accommodates_mean`, `accommodates_median` (if available)
- `bedrooms_mean`, `bedrooms_median` (if available)
- `beds_mean`, `beds_median` (if available)
- `bathrooms_mean`, `bathrooms_median` (if available)
- `geometry`: hex polygon

## Usage notes
- Use this dataset as the common spatial input for downstream analysis by Person B and Person C.
- For web tile basemaps, reproject to `EPSG:3857` before plotting.
