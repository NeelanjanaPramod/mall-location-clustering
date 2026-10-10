# Mall location clustering - Los Angeles County

Capstone-style data science project: **maximize profit for a shopping-mall business by segmenting locations with clustering**, using city data scraped from Wikipedia and venue data around each city centre.

**Notebook:** `mall_location_clustering.ipynb` (open in Colab and Run all - no API key needed)

## Pipeline
1. Scrape the cities of Los Angeles County and their 2020 populations from Wikipedia (`pandas.read_html`)
2. Get each city's coordinates from the Wikipedia (MediaWiki) API
3. Count venues within 2.5 km of each city centre in 7 categories (malls, other retail, grocery, food and drink, entertainment, services, education) via the OpenStreetMap Overpass API
4. K-Means clustering on log-scaled venue counts and population (k chosen by silhouette score)
5. Folium maps of the segments and of candidate mall locations (rendered when you run the notebook)
6. Rank cities with high demand and no mall nearby

## Result
Three segments: Los Angeles (a one-city, saturated cluster), established commercial hubs, and residential suburbs with light retail. Top candidates for a new mall: Long Beach, Burbank, Redondo Beach, Santa Clarita.

## Files
- `mall_location_clustering.ipynb` - the full notebook with outputs
- `data/venue_counts.csv` - snapshot of the venue counts (Oct 2026); the notebook loads it by default, set `LIVE = True` to re-query OpenStreetMap
- `data/cities.csv` - scraped cities, populations and coordinates

## Notes
The original IBM course uses the Foursquare API, which needs a personal key and has changed its endpoints; OpenStreetMap is used here as a free keyless source of the same kind of data (venues around a lat/lng). OpenStreetMap coverage varies, so mall counts are approximate.
