# PubScience Biodiversity Dashboard

A fully client-side dashboard that visualizes wildlife observations in Fairfax County, VA. It fetches raw JSON from the iNaturalist API, filters points to the county boundary, and renders an interactive map, dynamic charts, and “Most Commonly Seen” species cards—no backend server required.

---

## 🎥 Demo

Watch the completed dashboard in action:

[![Demo Video](https://i9.ytimg.com/vi/8dq--sy1f_w/mqdefault.jpg?sqp=CNSjocAG-oaymwEmCMACELQB8quKqQMa8AEB-AHUBoACxgOKAgwIABABGGggaChoMA8%3D&rs=AOn4CLB7hJQ0ZlgTbfvTYj0ZkXPYUxqM2w&retry=4)](https://youtu.be/8dq--sy1f_w)  
*Click to play demo → shows fetching MLST profiles, mapping species, filtering endangered taxa.*

**Discord Name**
   - chrisdev_74671 

---

## How It Works

1. **Data Acquisition & Filtering**  
   - Download yearly JSON dumps (`data/observations_<year>.json`) from the iNaturalist API.  
   - Run `data/filter_observations.py`, which uses Python with Shapely and PyProj to clip points to the Fairfax County polygon, producing GeoJSON files (`observations_<year>_ffx.geojson`).

2. **Static Hosting**  
   - All assets (HTML, JS, CSS, JSON, GeoJSON) live in the repo—no database or server code.  
   - Deploy on GitHub Pages, Netlify, or any static-file server.

3. **Interactive Frontend**  
   - **Leaflet.js** plots each observation as a map marker and displays county boundaries.  
   - **D3.js** generates:  
     - A bar chart of the top 10 most-observed species.  
     - A time-series chart of monthly observation counts.  
   - **Vanilla JS** populates “Most Commonly Seen” species cards with thumbnail images and total counts.

4. **Dynamic Filters**  
   - Dropdowns for year and taxonomic group trigger real-time reloading of the relevant JSON/GeoJSON files and re-render all visualizations without a page refresh.

---

## Key Highlights

- **Innovation**: Delivers rich geospatial and temporal analytics purely client-side—no backend or database setup.  
- **Technical Feasibility**: Built with standard web technologies (HTML, CSS, JS) and a small Python preprocessing script; can be hosted anywhere.  
- **UI/UX**: Intuitive controls, responsive charts, and map interactions let users explore spatial patterns, seasonal trends, and species rankings seamlessly.  
- **Developer Experience**: Clear code structure and a self-contained data pipeline make customization and extension straightforward.

---

## Getting Started

I strongly recommend you run the commands for installations and running of the server on github codespace. This I believe will ensure a smooth development experience.

1. **Clone & Enter Directory (if running locally)**  
   ```bash
   git clone https://github.com/jandreanalytics/FFX-County-Urban-Wildlife-Dashboard-.git
   cd FFX-County-Urban-Wildlife-Dashboard-
   
2. **Installing dependencies**  
   ```bash
   npm install

3. **(Optional) Regenerate Filtered Data**  
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   pip install shapely pyproj
   cd data
   python filter_observations.py
   cd ..

4. **Install HTTP Server (Optional)**  
   ```bash
   npm install -g http-server

5. **Serve Locally**  
   ```bash
   # Python HTTP server
   python3 -m http.server 8000

   # or Node.js http-server
   http-server . -p 8000



