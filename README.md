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

1. **Clone the repository**  
```bash
git clone https://github.com/fasilkhannageri/gps-feller-machine-analysis.git
cd gps-feller-machine-analysis
fasilllkdcsjf
