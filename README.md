# 🛰️ GPS-Based Feller Machine Activity Analysis Per Block

This repository contains a geospatial analysis pipeline to assess and visualize the activity of a feller machine within forest blocks using GPS tracking data. The workflow includes GIS-based preprocessing, anomaly detection, time tracking per forest block, and animated visualization of machine activity over time.

## 📌 Project Highlights

- ⏱️ Calculates **active machine time per forest block** (excluding anomalies)
- ⚠️ Identifies and logs **anomalous time gaps** in GPS movement
- 🗺️ Visual overlay of machine path over GeoTIFF basemap and forest block layers
- 🎞️ Generates **frame-by-frame animation** and compiles into an `.mp4` video
- 📊 Outputs `block_total_time.csv` and `block_anomalies.csv` for post-analysis

## 🗂️ Folder Structure

📁 Data/
├── GEOTIFF_Sample.tif # Raster basemap
├── GPS_Sample.csv # Raw GPS points (WKT + timestamp)
└── Blocks_Sample.gpkg # Polygon geometries of forest blocks

📁 Outputs/ (Will create automatically)
└── block_total_time.csv # Final summary of time per block

📁 frames/
└── frame_####.png # Animation frames

📄 demo.ipynb # Full analysis notebook

## ⚙️ Setup Instructions

1. Clone the repository**  
```
git clone https://github.com/fasilkhannageri/gps-feller-machine-analysis.git
cd gps-feller-machine-analysis
```

2. Install dependencies
```
pip install -r requirements.txt
```
3. Run analysis
Open demo.ipynb in Jupyter Notebook and run all cells.

4. Export animation
Ensure ffmpeg is installed to generate the .mp4.

- On MacOS
```
brew install ffmpeg
```
(Requires Homebrew. Install it first if not present.)

- On Windows:

1. Download from: https://ffmpeg.org/download.html

2. Extract the .zip archive

3. Add the bin/ folder to your system PATH environment variable

To check installation:
```
ffmpeg -version
```
##▶️ How to Run

- Open the demo.ipynb notebook and execute cells step-by-step:

- Data loading (CSV, GeoTIFF, GPKG)

- Line segment creation and filtering

- Block intersection and time calculation

- Anomaly logging to block_anomalies.csv

- Frame generation and animation

Summary outputs:

- block_total_time.csv
- block_anomalies.csv

- gps_animation.mp4

📊 Output Summary

- block_total_time.csv: Total time spent by the feller machine within each block

- block_anomalies.csv: Time gaps >5 minutes, with location context and block IDs

- gps_animation.mp4: Visual journey of the machine with color-coded temporal segments

🧠 Applications

- Forest operation monitoring

- Anomaly detection in machinery usage

- Geospatial-temporal analytics for sustainability studies

🕒 Time Calculation per Forest Block — Summary

1. Point-to-Point Segments

The GPS data is first sorted by time, and the code creates line segments between every pair of consecutive GPS points.

2. Duration Check

Each segment’s time duration (in minutes) is calculated:

If duration ≤ 5 min: the segment is valid and used for time calculations.

If duration > 5 min: the segment is flagged as an anomaly and excluded from block time accumulation (but saved in a separate CSV).

3. Intersection with Blocks

Valid segments are intersected with forest blocks (polygon boundaries). If a line crosses multiple blocks, the intersection is computed.

4. Time Distribution

For each intersected block:

The segment’s total length is calculated.

The fraction of the segment that lies within each block is computed.


The block time is then estimated as:

Time_In_Block = Segment_Duration × Fraction_Within_Block

Block-wise Summation
For each block, all its Time_In_Block values are summed up to produce the total operation time the feller machine spent inside that block.


5. Final Output

- A CSV file block_total_time.csv contains the valid time per block.

- Anomalous segments are stored in block_anomalies.csv for transparency and review.
---

####
for any assistance or information please dont hesitate to contact me at,

Name: Fasilkhan Nageri
email. fasilkhan.nageri@studenti.unipd.it








