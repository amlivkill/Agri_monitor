# 🌾 Agri Monitor

**Agri Monitor** is a comprehensive Rural Intelligence & GIS Solutions web application developed by **CHANGE TechLab**, Uttarakhand. It is designed to track agricultural data, monitor climate-smart agriculture practices, and estimate carbon credits for farmers and Community Level Federations (CLFs).

The project focuses on building a **Measurement, Reporting, and Verification (MRV)** support system for climate actions, aligning with India's **Carbon Credit Trading Scheme (CCTS)** and voluntary carbon markets.

---

## 🚀 Features

### 1. 📊 Main Dashboard
- High-level KPIs (Total Farmers, Active CLFs, Total Villages).
- District and Block-wise filtering (Uttarakhand focus).
- Quick navigation to different modules (Satellite, CLF, Alerts, Reports, etc.).

### 2. 🌍 Climate Actions MRV Module
A dedicated module to track and verify climate-friendly agricultural practices.
- **💧 AWD (Alternate Wetting and Drying):** Estimates methane (CH₄) reduction in paddy fields using IPCC Tier 1 Emission Factors.
- **🌾 SOC (Soil Organic Carbon):** Calculates soil carbon stock using 3-layer soil sampling (0-10cm, 10-20cm, 20-30cm), Bulk Density, and lab-tested SOC concentration.
- **🔥 Biochar:** Estimates carbon sequestration through biomass pyrolysis using default (0.50) or lab-tested carbon fractions.
- **🌳 Agroforestry:** Estimates above-ground biomass (AGB) and carbon storage using species-specific allometric equations (e.g., Walnut, Apple, Bamboo, etc.) based on ICFRE/FSI references.
- **Data Persistence:** LocalStorage based auto-saving with fully functional data tables and CSV export.

### 3. 🌱 Carbon Credit Calculator
A robust tool to calculate potential carbon credits and income for farmers.
- Area conversion tool (Nali, Bigha, Acre, Hectare, Muthi).
- Computes Soil Carbon, Tree Carbon, and bonuses for Organic Farming / Drip Irrigation.
- **Credit Standards Comparison:** Provides indicative income estimates across:
  - 🌿 **Verra VCS** (Voluntary Market)
  - 🇮🇳 **India CCTS** (Domestic Market)
  - ⭐ **Gold Standard** (Premium Market with SDG co-benefits)
  - 🇯🇵 **JCM** (Japan-India Joint Crediting Mechanism - Coming Soon)

### 4. 📋 India CCTS Guide
An educational module explaining the carbon market to farmers and project developers.
- Breaks down **Compliance vs. Voluntary** segments.
- Explains the **Farmer Pathway** (6 steps from practice to income).
- Illustrates the **Aggregation Model** (Farmer → CLF → Project Developer → Registry).
- Provides estimated income potential per practice and a roadmap for the Indian Carbon Market.

---

## 💻 Technology Stack

This is a frontend-heavy, mobile-first web application designed to work offline/locally or via a simple static host.

- **Frontend:** HTML5, CSS3 (Custom variables, Dark/Light Theme), Vanilla JavaScript.
- **Storage:** Browser `localStorage` (MVP phase) for data persistence.
- **Design System:** Custom CSS reflecting a modern, GIS-inspired dark theme (Glassmorphism, custom KPI cards, micro-animations).
- **Fonts:** Google Fonts (Noto Sans Devanagari for Hindi, Inter for English).

---

## 🛠️ Installation & Usage

Since the project uses Vanilla HTML/JS and `localStorage`, no complex server setup is required.

1. **Clone the repository:**
   ```bash
   git clone https://github.com/amlivkill/Agri_monitor.git
   ```
2. **Open the application:**
   Simply double-click `index.html` to open it in any modern web browser.
3. **Demo Data:**
   The MRV module (`climate-activities.html`) comes pre-seeded with 12 demo farmer records to showcase the functionality immediately. You can clear or reload this data from the UI.

---

## 📁 Key Files

- `index.html`: Main dashboard and entry point.
- `climate-activities.html`: The core MRV tracking module for AWD, SOC, Biochar, and Agroforestry.
- `carbon_calculator.html`: Farmer-centric carbon credit and income estimator.
- `ccts-guide.html`: Educational guide on the India Carbon Credit Trading Scheme.
- `css/style.css`: Core stylesheet defining the design system and themes.

---

## 🤝 About CHANGE TechLab

**CHANGE TechLab** is a Rural Intelligence, GIS, and Business Planning Company based in Uttarakhand.
*From Rural Data to Business Decisions.*

- **Email:** changetechlab@outlook.com

---
*Note: The carbon estimations provided by this tool are indicative and serve as an MRV support system. Official carbon credit issuance requires independent third-party verification by accredited VVBs.*
