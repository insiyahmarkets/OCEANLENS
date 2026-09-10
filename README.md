# OceanVision 3D - Global Interactive Ocean Model & Observation Platform

**SIH 2026 Problem Statement Prototype**: *"Develop a web-based interactive 3D visualization platform that integrates numerical ocean model outputs and in-situ observations."*

---

## 🌊 Project Overview

**OceanVision 3D** is a professional oceanographic data visualization platform. It empowers oceanographers, researchers, climate scientists, and defense personnel to explore ocean parameters in 3D across global ocean basins, switch between numerical ocean model forecasts (INCOIS / HYCOM / NEMO predictions) and real-world in-situ observations (Moored Buoys, Argo Floats, Coastal Gauges, Research Vessels, Ocean Gliders, Drifting Buoys), calculate validation metrics (MAE, RMSE, Bias), and detect marine anomalies.

---

## ✨ Key Features

1. **Global 3D Ocean Exploration (`Three.js` / React Three Fiber)**
   - Interactive 3D Earth Globe featuring crisp landmass polygons for all **7 continents** (Africa, Europe, Asia, North America, South America, Australia, Antarctica).
   - Deep ocean blue base color with zero black patches or missing data holes.
   - Smooth heatmaps for **SST**, **Salinity**, **SSH**, **Wave Height**, **Current Speed**, and **Chlorophyll**.
   - Depth slicing level slider (`0m` to `2000m`).

2. **Global Particle Vector Current Fields**
   - Flow particle animations visualizing major global currents (Gulf Stream, Kuroshio, Agulhas Current, Wyrtki Jet, Equatorial Currents, Antarctic Circumpolar Current).

3. **6 Observation Station Marker Types**
   - **Moored Buoy** (Cyan)
   - **Argo Float** (Purple/Magenta)
   - **Coastal Station** (Emerald/Green)
   - **Research Vessel** (Amber/Orange)
   - **Ocean Glider** (Pink/Rose)
   - **Drifting Buoy** (Royal Blue)
   - Compact hover tooltips and sleek, non-intrusive floating click inspector.

4. **Model vs Observation Matching & Validation**
   - Dual-series Recharts line plots, anomaly area shading, and validation matrix tables.
   - Automated error metrics: MAE, RMSE, Bias, and Pearson Correlation ($r$).

5. **Guided Hackathon Demo Mode (`Run Demo`)**
   - Automated 10-step guided evaluation tour with step progress indicator (`STEP 1/10` to `STEP 10/10`) for 30-second SIH presentations.

6. **NetCDF / CSV Ingestion Pipeline**
   - Interactive file parser simulator for NetCDF (`.nc`) and CSV observational data uploads.

---

## 🛠 Technology Stack

- **Frontend Core**: React 18, JavaScript (ES6+), Vite 8
- **3D Visualization**: Three.js, `@react-three/fiber`, `@react-three/drei`
- **Scientific Plotting**: Recharts
- **Styling & UI**: Tailwind CSS v4, Lucide React Icons
- **Deployment**: Vercel ready (`vercel.json`)

---

## 📁 Project Structure

```
oceanvision-3d/
 ├── public/
 ├── src/
 │    ├── components/
 │    │    ├── Navbar.jsx               # Global search & demo controls
 │    │    ├── Sidebar.jsx              # Left navigation menu
 │    │    ├── LayerControl.jsx         # 3D layer toggles widget
 │    │    ├── DataPanel.jsx            # Compact station inspector modal
 │    │    ├── DemoController.jsx       # Guided SIH 10-step tour controller
 │    │    └── OceanGlobe/
 │    │         ├── OceanCanvas.jsx     # R3F viewport & orbit controls
 │    │         ├── EarthGlobe.jsx      # Procedural 3D Earth sphere with continents & heatmaps
 │    │         ├── OceanCurrentParticles.jsx # Global current flow particle fields
 │    │         ├── StationMarkers.jsx  # 3D station pins with hover & LOD management
 │    │         └── Legend.jsx          # Parameter & station type color scale legend
 │    │
 │    ├── pages/
 │    │    ├── Dashboard.jsx            # Global KPIs, mini-globe, alert feeds
 │    │    ├── OceanExplorer.jsx        # Full 3D interactive viewport
 │    │    ├── ModelObservation.jsx     # Model vs Observed comparative table & dual plots
 │    │    ├── LocationAnalysis.jsx     # Regional spatial breakdown
 │    │    ├── TimeSeriesPage.jsx       # Temporal horizon graphs
 │    │    ├── DataSourcesPage.jsx      # Scientific data pipeline & NetCDF/CSV uploader
 │    │    ├── ValidationMetrics.jsx    # MAE, RMSE, Bias, Correlation matrix
 │    │    ├── AlertsPage.jsx           # Ocean anomaly notifications
 │    │    └── AboutPage.jsx            # SIH problem statement & architecture
 │    │
 │    ├── data/
 │    │    └── mockOceanData.js         # ~54 global ocean stations & parameter definitions
 │    ├── utils/
 │    │    ├── metrics.js               # MAE, RMSE, Bias, Correlation & color interpolation
 │    │    └── dataProcessing.js        # NetCDF/CSV dataset validation & pipeline simulator
 │    │
 │    ├── App.jsx                       # Tab routing & guided demo state
 │    ├── main.jsx
 │    └── index.css                    # Tailwind imports & dark ocean theme styles
 ├── package.json
 ├── vite.config.js
 ├── vercel.json                        # Vercel deployment config
 ├── DEPLOYMENT.md                      # Public deployment guide
 └── README.md                          # Project documentation
```

---

## 🚀 How to Run Locally

1. Open your terminal in VS Code:
   ```bash
   cd C:\Users\Insiyah\.gemini\antigravity\scratch\oceanvision-3d
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start local development server:
   ```bash
   npm run dev
   ```
4. Open **`http://localhost:5173/`** in your browser.

---

## 🎬 How Demo Mode Works

Click the **"Run Demo"** button in the top navbar or dashboard. An automated 10-step guided tour will guide you through:
1. Opening 3D Explorer & focusing camera on Indian Ocean / Arabian Sea.
2. Enabling Sea Surface Temperature (SST) layer.
3. Displaying in-situ observation station markers.
4. Selecting Mumbai Coastal Station & opening Model vs Observation panel.
5. Inspecting predicted vs measured delta (0.5°C difference, 1.72% error).
6. Viewing 24-hour time series trend plots.
7. Checking scientific validation metrics (MAE = 0.43°C, RMSE, Bias).
8. Highlighting active ocean anomaly alerts.

---

## 🔌 How to Connect Real NetCDF / REST API Data

The platform separates data ingestion, metric calculations, and rendering logic:
1. Replace `mockOceanData.js` imports in `App.jsx` with an async API fetch hook (e.g. fetching NetCDF JSON endpoints from INCOIS / HYCOM THREDDS server).
2. Use `src/utils/dataProcessing.js` to parse incoming NetCDF arrays into spatial latitude/longitude grids.
3. Pass parsed arrays into `EarthGlobe.jsx` and `StationMarkers.jsx`.

---

## 🌐 Public Deployment

To deploy to Vercel or Netlify, see **[`DEPLOYMENT.md`](./DEPLOYMENT.md)** for step-by-step instructions.
