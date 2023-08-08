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

A random point is generated on a randomly selected road segment using the `create_random_point_on_road` function.

### Network Analysis

The road network is constructed using NetworkX, and the shortest path between the random point and each gas station is calculated using Dijkstra's algorithm. The nearest gas station is then identified.

### Visualization

The final visualization includes the study area boundary, OSM roads, gas stations, random point, and the route to the nearest gas station.

## Results

The analysis identifies the nearest gas station and visualizes the route, providing insights into the spatial relationships between the random point and nearby gas stations.

![Final Plot](path_to_your_plot_image.png)  <!-- Replace with the actual path to your plot image -->

## Conclusion

This project demonstrates how to conduct spatial and network analysis using Python's geospatial libraries. It offers a practical example of solving real-world spatial problems and can be extended to other applications in urban planning, transportation, and logistics.

## License

This project is open-source and available under the MIT License. Feel free to fork, modify, and share!
