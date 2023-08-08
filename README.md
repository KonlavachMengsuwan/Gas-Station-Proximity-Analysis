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
```python

### Network Analysis
The road network is constructed using NetworkX, and the shortest path between the random point and each gas station is calculated using Dijkstra's algorithm. The nearest gas station is then identified.

#### Building the Network Graph
```python
G = nx.Graph()
for _, row in osm_roads_gdf.iterrows():
    if row.geometry.geom_type == 'MultiLineString':
        for line in row.geometry.geoms:
            add_edges_from_linestring(G, line, weight=line.length)
    else:
        add_edges_from_linestring(G, row.geometry, weight=row.geometry.length)
```

#### Calculating Shortest Paths
```python
def shortest_path_to_gas_station(graph, source_node, target_node):
    return nx.shortest_path_length(graph, source=source_node, target=target_node, weight='weight')
```

#### Identifying the Nearest Gas Station
```python
nearest_gas_station = gas_stations_gdf.loc[gas_stations_gdf['distance_to_random_point'].idxmin()]
```

### Visualization
The final visualization includes the study area boundary, OSM roads, gas stations, random point, and the route to the nearest gas station.
```python
fig, ax = plt.subplots(figsize=(10, 10))
osm_roads_gdf.plot(ax=ax, color='#B0B0B0', linewidth=0.5)
...
plt.show()
```

### Results
The analysis identifies the nearest gas station and visualizes the route, providing insights into the spatial relationships between the random point and nearby gas stations.

 <!-- Replace with the actual path to your plot image -->

### Conclusion
This project demonstrates how to conduct spatial and network analysis using Python's geospatial libraries. It offers a practical example of solving real-world spatial problems and can be extended to other applications in urban planning, transportation, and logistics.

### License
This project is open-source and available under the MIT License. Feel free to fork, modify, and share!
```python

You can copy and paste this markdown chunk into the desired location in your `README.md` file. Make sure to replace `path_to_your_plot_image.png` with the actual path to the image of your plot if you decide to include it in the README.
```




