# Copenhagen Airbnb GDS Project

We will investigate what spatial factors drive Airbnb pricing in Copenhagen and whether there are statistically significant price clusters across the city. Using detailed listing data from Inside Airbnb (https://insideairbnb.com/get-the-data/), we will construct H3 hexagonal grid cells to aggregate listings into spatially uniform units suitable for areal analysis. We will produce choropleth maps using multiple classification schemes to visualize the spatial distribution of median prices across the city. Using spatial weights matrices and spatial autocorrelation analysis (global Moran's I and local LISA statistics), we will identify statistically significant hot and cold spots of Airbnb pricing. We will further apply K-Means clustering on multivariate listing attributes (price, capacity, review scores, room type) to uncover distinct listing typologies and map their spatial distribution. If the scope allows it, we would build interactive visualizations with Folium or PyDeck to allow exploration of the results. With this project, we aim to understand how location and neighbourhood characteristics shape the short-term rental market in Copenhagen

## Data source

- Inside Airbnb snapshot for Copenhagen: <https://insideairbnb.com/get-the-data/>
- Working input file: `data/copenhagen-listings.csv` (or `copenhagen-listings.csv` in project root)

## Preprocessing notebook

- Main workflow: `preprocess.ipynb`
- Core steps implemented:
  - parse and clean listing prices (`price` -> `price_float`)
  - handle nulls and remove coordinate/price outliers
  - build point GeoDataFrame and reproject to `EPSG:25832`
  - build H3 hex grid aggregates (shared spatial unit)
  - exploratory mapping (hexbin, KDE, point-in-neighbourhood, choropleths)

## Shared outputs

- `preprocessed data/hex_listing_aggregates_epsg25832.geojson`
- `preprocessed data/hex_listing_aggregates_epsg25832.parquet`
- `preprocessed data/hex_listing_aggregates_epsg25832.csv`
- `preprocessed data/metadata_hex_dataset.md`

