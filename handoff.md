# 🌾 Agri Monitor – Project Handoff Document

This document serves as a comprehensive handoff guide for **Agri Monitor**, detailing the current architecture, recent optimizations, deployment configuration, and future roadmap.

## 1. Project Overview
**Agri Monitor** is a Rural Intelligence & GIS Solutions web application developed by **CHANGE TechLab**, Uttarakhand. It tracks agricultural data, monitors climate-smart agriculture practices (AWD, SOC, Biochar, Agroforestry), and estimates carbon credits for farmers and Community Level Federations (CLFs).

- **Target Audience:** Agricultural officers, CLF coordinators, and farmers in mountainous regions (e.g., Uttarakhand).
- **Core Strategy:** **Offline-First, Mobile-First PWA** optimized for slow 3G networks.

## 2. Architecture & Technology Stack
The project consciously avoids heavy build tools (like Vite/Webpack) to ensure maximum compatibility, ease of maintenance for non-technical officers, and pure offline capabilities.

- **Frontend:** Vanilla HTML5, CSS3, JavaScript (ES Modules / IIFE).
- **Offline PWA:** Service Worker (`sw.js`) with a 7-day TTL caching strategy (`sw-fetch-time` header).
- **Storage:** Browser `localStorage` for MVP data persistence, with fallback/sync hooks for Supabase.
- **Mapping:** Leaflet.js (Offline compatible).
- **Styling:** Custom CSS variables, Glassmorphism, Dark/Light theme toggling.

## 3. Recent Optimizations & Changes
To achieve a "production-ready" state with blazing-fast load times on weak networks:
1. **Local Assets (No CDNs):** All heavy dependencies (Leaflet, Chart.js, Supabase JS, jsPDF) and fonts (`Noto Sans Devanagari`) were downloaded locally to `js/vendor/` and `public/fonts/`.
2. **Code-Splitting & Lazy Loading:**
   - Extracted massive inline CSS and JS from `carbon_calculator.html` and `climate-activities.html` into separate files (`css/carbon-calc.css`, `css/climate.css`, `js/modules/...`).
   - Implemented dynamic `import()` in `app.js` for heavy modules like `farmers.js` and `ndvi.js`.
3. **Cross-Platform Deployment Fixes:**
   - Fixed absolute paths (`/`) to relative paths (`./`) in `sw.js` and `manifest.json` to ensure the PWA installs correctly on both root domains (Vercel) and sub-paths (GitHub Pages).
   - Removed deprecated `builds` and catch-all routes from `vercel.json` to fix Vercel 404 errors.
4. **UI Additions:**
   - Added a premium, dynamic **Carbon Tracker Widget** to the main dashboard (`index.html`).
   - Added exhaustive block lists for **Tehri Garhwal** (`app.js`, `index.html`).

## 4. Key Files Directory
```text
Agri_monitor/
├── index.html                  # Main Dashboard
├── climate-activities.html     # MRV Tracking (AWD, SOC, Biochar)
├── carbon_calculator.html      # Carbon Credit & Income Estimator
├── ccts-guide.html             # India CCTS Educational Guide
├── css/
│   ├── style.css               # Core variables, layout, themes
│   ├── climate.css             # Scoped CSS for climate activities
│   └── carbon-calc.css         # Scoped CSS for the calculator
├── js/
│   ├── app.js                  # Main bootstrap, global state, dynamic imports
│   ├── offline.js              # IndexedDB / localStorage syncing logic
│   ├── map.js & layers.js      # Leaflet map configuration
│   ├── vendor/                 # Local 3rd-party libraries
│   └── modules/                # Code-split logical modules
├── sw.js                       # Service Worker (Cache & Network logic)
├── manifest.json               # PWA Manifest
└── vercel.json                 # Vercel deployment headers
```

## 5. Deployment Setup
The project is currently deployed automatically via GitHub:
- **Primary Hosting (Vercel):** https://agri-monitor-one.vercel.app/
  - Deploys as a standard Static output via Zero Configuration.
  - `vercel.json` is strictly used for setting HTTP Cache-Control headers.
- **Secondary Hosting (GitHub Pages):** https://amlivkill.github.io/Agri_monitor/
  - Fully compatible due to the recent relative path (`./`) fixes.
- **GitMCP Integration:** An MCP server is live at `https://gitmcp.io/amlivkill/Agri_monitor` to allow AI agents to chat with the repository documentation online.

## 6. Next Steps & Roadmap
If a new developer or AI agent takes over, here are the immediate next priorities:
1. **JCM Methodology Integration:** Implement the Japan-India Joint Crediting Mechanism formulas in the Carbon Calculator (currently marked as "Coming soon").
2. **Supabase Syncing:** Fully wire up `js/offline.js` and `js/upload.js` to push `localStorage` records to the Supabase backend when the device detects a strong online connection.
3. **Agroforestry DBH Calculations:** Refine the allometric equations (ICFRE/FSI) for specific tree species in the MRV module to provide more accurate AGB (Above-Ground Biomass) estimates.
4. **Map Polygon Intersections:** Enhance `js/farmers.js` to prevent overlapping field polygons when drawing on Leaflet.
