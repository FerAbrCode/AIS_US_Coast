

# ⛴️ AIS Tanker Tracker — Maritime Movement Analysis & Mapping

This project processes AIS (Automatic Identification System) data to identify and visualize the movement of tanker vessels (VesselType 80) across multiple time-stamped datasets. It uses efficient streaming, geospatial mapping, and vessel metadata to produce interactive maps and insights into tanker activity.

---

## 📦 Project Overview

- **Goal:** Extract tanker vessel data from large AIS datasets, compute overlaps, and visualize last known positions and movement trails.
- **Data Source:** AIS logs across 7 chronological files (`data.csv` to `data7.csv`)
- **Focus:** Tankers only (`VesselType == 80`)
- **Output:** Interactive HTML map showing vessel trails and last known positions with directional arrows and metadata popups.

---

## 🧠 Key Features

- **Streamed Reading:** Efficient chunk-wise loading of large CSVs using `pandas.read_csv(..., chunksize=...)`
- **Filtering:** Only rows with `VesselType == 80` are retained
- **Timestamp Normalization:** Auto-detects timestamp column from common candidates
- **Length-Based Coloring:** Custom colormap (blue → purple → red) based on vessel length
- **Disappearance Detection:** Flags vessels missing for over 24 hours from latest timestamp
- **Interactive Mapping:** Uses `folium` with dark basemap, seamark overlay, and SVG arrow markers

---

## 📍 Map Output

- **Trail Lines:** Dashed paths showing vessel movement over time
- **Arrow Markers:** Last known position with heading and length-based size
- **Popups:** MMSI, vessel name, speed, heading, source file, timestamp
- **Disappearance Alert:** Red exclamation icon for vessels missing >24h

Maps generated:
- `tankers_last_positions_map.html`: Consolidated map from all 7 files
- `tankers_detailed_map.html`: Map from single dataset (e.g., `data.csv`)

---

## 📊 Stats Printed

- Unique tankers per file
- MMSIs present in all files
- Top 5 vessels by entry count
- Invalid heading values (>360 or non-numeric)

---

## 🛠️ Technologies Used

- `pandas` for data manipulation
- `folium` for interactive mapping
- `matplotlib.colors` for custom color scaling
- `numpy` for numerical operations

---

## 📁 File Structure

```
AIS Data/
├── data.csv
├── data2.csv
├── ...
├── data7.csv
├── tankers_last_positions_map.html
├── tankers_detailed_map.html
└── ais_tanker_tracker.py  # or notebook
```

---

## 🚀 How to Run

```bash
pip install pandas folium matplotlib
python ais_tanker_tracker.py
```

Or run the notebook step-by-step to explore and visualize.

---

## 📌 Notes

- Handles missing columns gracefully
- Caches loaded data to avoid reprocessing
- Modular helpers for timestamp detection, length parsing, and color mapping

---

## 📈 Future Enhancements

- Add clustering for dense regions
- Integrate real-time AIS feeds
- Export vessel movement summaries
- Animate vessel trails over time

---

Let me know if you'd like a version with embedded screenshots or tailored for a Jupyter Notebook!
