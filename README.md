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
