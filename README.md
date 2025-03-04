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

## License
[Specify your license here, e.g., MIT, Apache 2.0, or GPL-3.0. If unsure, you can use MIT for simplicity. For example:]
MIT License

Copyright (c) [Your Name or Organization] [Year]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

[Include the rest of the MIT License text or link to a LICENSE file.]



## Notes
- This implementation assumes the input data format matches the `shp/input/` examples.
- Adjust `main.py` or input files if your road network or GPS data differs.
How to Use This README
Create or Update README.md in VS Code:
Open VS Code and navigate to the map-match folder.
If README.md doesn’t exist, right-click in the Explorer pane, select New File, name it README.md, and press Enter.
If it exists, open it by double-clicking.
Copy the entire Markdown text above, paste it into README.md, and save the file (Ctrl+S).
Upload to GitHub:
If you haven’t uploaded the project yet, follow these steps in the VS Code terminal (ensure you’re in C:\Users\Dell\Documents\map-match):
Initialize a Git repository (if not already done):

git init

git add .

git commit -m "Initial commit with map-matching project and README"
Press Enter.
Create a repository on GitHub:
Go to github.com/new, name it map-match (or your preferred name), and initialize it with a README (optional, but you can uncheck it since you’re uploading your own).
Link your local repo to GitHub:

git remote add origin https://github.com/your-username/map-match.git
Press Enter (replace your-username with your GitHub username).
Push the files:

git push origin main
Press Enter. You might need to log in to GitHub or set up an SSH key if prompted.
If the repository already exists, you can push updates:

git add .
git commit -m "Added README and project updates"
git push origin main
Customize the License:
Replace [Specify your license here, e.g., MIT, Apache 2.0, or GPL-3.0] with your chosen license. If you’re unsure, the MIT License is simple and permissive.
You can create a separate LICENSE file with the full license text and reference it in the README.
Personalize the README:
Replace [Your Name or Organization] and [Year] in the license section with your details (e.g., your name and 2025).
Update the GitHub link in “Acknowledgments” to point to your repository once it’s created (e.g., https://github.com/your-username/map-match).
