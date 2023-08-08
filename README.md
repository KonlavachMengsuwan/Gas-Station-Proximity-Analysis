# Gas-Station-Proximity-Analysis

## Overview
This project demonstrates a spatial analysis that involves finding the nearest gas station to a randomly generated point within a given study area. The analysis leverages GeoPandas, Shapely, and NetworkX libraries to handle geospatial data and perform network analysis.

## Objectives
1. **Random Point Generation:** Create a random point on a randomly selected road segment within the study area.
2. **Gas Station Proximity Analysis:** Determine the shortest path from the random point to all gas stations and identify the nearest one.
3. **Visualization:** Plot the study area, roads, gas stations, random point, and the route to the nearest gas station.

## Data
The analysis uses the following GeoJSON files:
- `Gas_Stations.geojson`: Contains the locations of gas stations.
- `Study_Area.geojson`: Defines the boundary of the study area.
- `OSM_Roads_StudyArea.geojson`: Contains the OpenStreetMap roads within the study area.

## Methodology

### Random Point Generation
A random point is generated on a randomly selected road segment using the following code:
```python
def create_random_point_on_road(roads_gdf):
    random_road = roads_gdf.sample(1).iloc[0]['geometry']
    random_point_on_road = random_road.interpolate(random.random(), normalized=True)
    return Point(random_point_on_road)
