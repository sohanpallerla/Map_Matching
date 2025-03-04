# ST-Matching: GPS Trajectory Map-Matching Algorithm

This repository implements a map-matching algorithm for GPS trajectories, inspired by the ST-Match approach described in "Map-Matching for Low-Sampling-Rate GPS Trajectories" (Microsoft Research). The algorithm aligns GPS trajectory data to a road network, enabling accurate path reconstruction without relying on spatial databases like PostGIS, making it flexible and lightweight.

## Features
- Matches low-sampling-rate GPS trajectories to road networks using Dijkstra's algorithm and probability-based path selection.
- Uses shapefiles (`connected_road.shp` and `track.shp`) for road network and GPS data input.
- Outputs matched paths as shapefiles in `shp/output/` for visualization in GIS tools like QGIS.
- Implements caching for efficiency and handles trajectory connectivity checks to detect issues like super-speed.

## Requirements
- Python 3.9+ (tested with 3.12–3.13)
- Libraries: `networkx`, `psycopg2-binary`, `fiona`, `shapely`, `scipy`
- Input data: `connected_road.shp` (road network) and `track.shp` (GPS trajectories) in the `shp/input/` folder

## Installation
1. Clone this repository:
git clone https://github.com/your-username/map-match.git
2. Install dependencies in a virtual environment:
python -m venv venv
venv\Scripts\activate  # On Windows, use source venv/bin/activate on macOS/Linux
pip install networkx psycopg2-binary fiona shapely scipy
3. Ensure input shapefiles are in `shp/input/`.

## Usage
Run the main script to process GPS tracks and generate matched paths:

python main.py

Output shapefiles will be created in `shp/output/`, e.g., `new_path1.shp`.

## Visualization
- Use QGIS (e.g., version 3.40 LTR or later) to open and visualize `new_pathX.shp` files alongside `connected_road.shp` and `track.shp`.
- Download QGIS from [qgis.org](https://www.qgis.org/) and install the Long Term Release (LTR) for stability.

## Results
The algorithm produces matched paths as line features, ordered by an `idx` field, representing the sequence of roads in each trajectory.

## Reference
- [ST-Match: Map-Matching for Low-Sampling-Rate GPS Trajectories](https://www.microsoft.com/en-us/research/publication/map-matching-for-low-sampling-rate-gps-trajectories/)


## Notes
- This implementation assumes the input data format matches the `shp/input/` examples.
- Adjust `main.py` or input files if your road network or GPS data differs.

## Description
Overview
The ST-Matching project is a Python-based implementation of a map-matching algorithm designed to align low-sampling-rate GPS trajectories with a road network. Inspired by the ST-Match approach developed by Microsoft Research, as detailed in their paper "Map-Matching for Low-Sampling-Rate GPS Trajectories," this project provides a flexible and efficient solution for reconstructing vehicle paths from GPS data. Unlike traditional map-matching systems that rely on spatial databases like PostGIS, this implementation uses shapefiles for inputs and outputs, making it lightweight and adaptable for various use cases.

Purpose
The primary goal of this project is to accurately match GPS trajectory data—often noisy or sparsely sampled—to a predefined road network, enabling applications such as traffic analysis, route optimization, and navigation system improvement. It is particularly useful for scenarios where GPS data is collected at low frequencies, ensuring robust path reconstruction even with limited data points.

Key Features
Efficient Algorithm: Utilizes Dijkstra's algorithm to compute the shortest paths between GPS points and the road network, combined with probability-based matching to determine the most likely path.
Shapefile Integration: Accepts road network data (connected_road.shp) and GPS trajectories (track.shp) as input, stored in the shp/input/ folder, and outputs matched paths as shapefiles in shp/output/ (e.g., new_pathX.shp).
Performance Optimization: Implements caching to store precomputed Dijkstra distances and paths, improving runtime efficiency for repeated queries.
Connectivity Checks: Includes logic to detect and handle issues like super-speed (unrealistic travel speeds), ensuring the validity of matched paths.
Visualization Ready: Outputs are compatible with GIS tools like QGIS, allowing users to visualize matched paths alongside raw GPS data and road networks.
Technical Details
Programming Language: Python 3.9 or higher (tested with versions 3.12–3.13).
Dependencies:
networkx: For graph-based pathfinding and network analysis.
psycopg2-binary: For potential database interactions (optional in this implementation).
fiona: For reading and writing shapefiles.
shapely: For geometric operations on GPS points and road segments.
scipy: For spatial and statistical computations, such as Euclidean distance and probability calculations.
Input Data: Requires two shapefiles:
connected_road.shp: A directed graph of road segments with attributes like source, target, and weight (distance or cost).
track.shp: GPS trajectory points with attributes like x, y, track_id, log_time, car_id, and v (velocity).
Output Data: Generates shapefiles (new_pathX.shp) containing the matched road segments, ordered by an idx field indicating the sequence of roads in each trajectory.

