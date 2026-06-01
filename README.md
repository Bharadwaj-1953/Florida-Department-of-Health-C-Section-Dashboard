<h1 align="center">
Florida-Department-of-Health-C-Section-Dashboard
</h1>

---

## 📝 Abstract

<div align="justify">
This project is an interactive, single-file analytics dashboard built for the Florida Agency for Health Care Administration (AHCA) as part of a Government Operations Data Specialist work sample. The dashboard visualizes eight years of Florida Medicaid primary cesarean section data (2016–2023), covering over 860,000 birth records across 11 geographic service regions, 4 maternal age groups, and individual birth ages (14–46).
</div>

<br>

<div align="justify">
The tool is built entirely in vanilla HTML, CSS, and JavaScript — no build step, no framework, no server required. It renders a fully interactive, publication-quality dashboard that a state agency analyst can open in any modern browser and immediately use for policy exploration, stakeholder briefings, or public reporting.
</div>

---

## 🌐 Live Demo

**[https://florida-department-of-health-c-sect.vercel.app/](https://florida-department-of-health-c-sect.vercel.app/)**

> Deployed on Vercel as a static site. No login required — open and explore immediately.

---

## 📁 Repository Structure

```bash
florida-perinatal-dashboard/
├── index.html                                        # Complete self-contained dashboard (HTML + CSS + JS + data)
├── Florida_Medicaid_Primary_C_Section_Data.xlsx     # Source data (5 sheets, raw Medicaid claims extract)
└── README.md                                        # This file
```

> The entire application — data, charts, map, styling, and interactivity — lives in a single `.html` file. No dependencies to install, no build commands to run.

---

## 🎯 Key Features

- **Statewide Trend View** — Annual primary C-section rates from 2016 to 2023 with a 2017 peak annotation, monthly breakdown bars, and a plain-language explainer on what a primary C-section is
- **Age Group Analysis** — Rates by four maternal age groups (Under 20, 20–29, 30–39, 40+), summary KPI cards with year-over-year change badges, a grouped bar chart, an all-groups trend overlay, and a granular single-year scatter showing rates at each individual age from 14 to 46
- **Regional Analysis** — Ranked table of all 11 Florida Medicaid regions with color-coded above/below-average badges, a choropleth map of Florida built with D3 and TopoJSON, clickable region detail cards showing C-section count, total births, and deviation from state average, and a region × age group cross-tabulation chart
- **Interactive Filters** — Year selector (2016–2023) on every panel, region selector on the age-region explorer, synchronized map and table selection on click
- **Public-Facing Narrative Bands** — A "What this means for you" section written for Medicaid recipients, with key takeaways in accessible plain language
- **No External Data Calls** — All data is embedded directly in the JS block; the only external requests are Google Fonts and chart/map libraries loaded from CDN

---

## 🛠️ Technologies Used

| Category | Technology |
|----------|-----------|
| **Structure** | HTML5 |
| **Styling** | CSS3 (custom properties, CSS Grid, Flexbox) |
| **Charting** | Chart.js 4.4 |
| **Mapping** | D3.js v7 · TopoJSON Client v3 · US Atlas (counties-10m) |
| **Typography** | Inter (Google Fonts) |
| **Data** | Microsoft Excel (.xlsx) · 5 sheets · 2,885 rows |
| **Deployment** | Vercel (static) |

---

## 📊 Source Data — Excel Workbook

The raw data behind the dashboard is included as `Florida_Medicaid_Primary_C_Section_Data.xlsx`. It contains 5 structured sheets extracted from Florida Medicaid claims and encounter records.

| Sheet | Rows | Columns | Description |
|-------|------|---------|-------------|
| `Annual C-Sections by Age` | 264 | 5 | Primary C-section count, rate, and total deliveries per year × individual age (14–46) |
| `Annual C-Sections By Month` | 96 | 5 | Monthly C-section count, rate, and total deliveries per year × calendar month |
| `Annual C-Sections by Region` | 88 | 5 | Annual C-section count, rate, and total deliveries per year × Florida Medicaid region (11 regions) |
| `Annual C-Sections by Region & Age` | 2,370 | 6 | Most granular cut — count, rate, and deliveries per region × year × individual age |
| `Region-County Crosswalk` | 67 | 2 | Maps each of Florida's 67 counties to its AHCA Medicaid service region |

### Column Reference

| Column | Description |
|--------|-------------|
| `Year of Service` | Calendar year (2016–2023) |
| `Age` | Maternal age at delivery (14–46) |
| `Month of Service` | Calendar month name |
| `Regions in FL` | Florida Medicaid service region (Region 1–11) |
| `County Name` | Florida county (crosswalk sheet only) |
| `PCS` | Primary C-section count |
| `Percent PCS` | Primary C-section rate (decimal, e.g. 0.177 = 17.7%) |
| `Total` / `Total Deliveries` | Total Medicaid deliveries in that cell |

---

## 📊 Data Coverage

| Dimension | Detail |
|-----------|--------|
| **Source** | Florida Medicaid claims and encounter records |
| **Procedure Codes** | APR-DRG 540, 541, 542, 560 · CPT 59400–59622 |
| **Years** | 2016 to 2023 (8 calendar years) |
| **Annual Deliveries** | ~102,000–121,000 per year |
| **Total Deliveries** | ~884,000 across the full dataset |
| **Regions** | 11 Florida Medicaid geographic service areas |
| **Counties** | All 67 Florida counties mapped to regions |
| **Age Range** | Maternal ages 14–46 (individual) · 4 broad groups |
| **Privacy Threshold** | Cells with fewer than 30 deliveries excluded |

---

## 📈 Key Findings Visualized

**Statewide**
- Primary C-section rate peaked at **22.1% in 2017** and reached a dataset low of **17.7% in 2023** — a decline of 4.4 percentage points
- A small uptick in mid-2021 (driven by summer months) briefly interrupted the downward trend before resuming

**By Age**
- Rates are monotonically increasing with maternal age in every year on record
- Women **40 and older** had the largest absolute decline: from 32.5% (2017) to 24.2% (2023), a drop of 8.3 pp
- Rates stay near 16–17% from age 18 through the late 20s, then climb steadily from age 30 onward

**By Region**
- In 2023, **Region 11 (Miami-Dade/Monroe)** had the highest rate at **24.7%** and **Region 3 (North Central)** had the lowest at **14.2%** — a 10.5 pp gap
- This regional spread has persisted across all eight years in the dataset

---

## ⚙️ Usage

### Open Locally
```bash
# Clone the repository
git clone https://github.com/Bharadwaj-1953/florida-perinatal-dashboard.git

# Open directly in browser — no server needed
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

### Deploy to GitHub Pages
1. Push the repo to GitHub
2. Go to **Settings → Pages → Source: main branch / root**
3. GitHub Pages will serve `index.html` as a static site

### Deploy to Vercel
Drop the folder into Vercel with no configuration required. The file is fully static — Vercel detects and serves it instantly.

> **Note:** The choropleth map loads county geometry from the `us-atlas` CDN. An internet connection is required for the map to render. All charts and tables work offline.

---

## 🗺️ Dashboard Panels

| Panel | What It Shows |
|-------|--------------|
| **Statewide Trend** | Annual rate line chart with 2017 peak marker, monthly bar chart, plain-language C-section explainer |
| **By Age Group** | KPI cards per age group with YoY delta, grouped bar chart, multi-line trend overlay (2016–2023), single-age scatter plot (ages 14–46) |
| **By Region** | Ranked region table with above/below-average badges, interactive D3 choropleth map, region detail card, region × age bar chart |

---

## 🔐 Data Notes

- Data is sourced from **Florida Medicaid claims and encounter records** and represents only Medicaid-covered births — it does not cover privately insured or uninsured deliveries
- Only **primary** cesarean sections are counted — women who had a prior C-section in an earlier pregnancy are excluded from both the numerator and denominator
- All figures are **calendar-year rates** (primary C-sections ÷ total Medicaid deliveries), expressed as percentages
- Cells with fewer than **30 deliveries** are excluded to protect patient privacy

---

## 📊 Experimental Results and Analysis

- The dashboard was developed and tested across Chrome, Firefox, Edge, and Safari on both Windows and macOS
- Chart.js canvas rendering was tuned to initialize after the layout settles (`80ms setTimeout`) to avoid zero-height render artifacts in browsers that compute container size lazily
- The D3 choropleth merges FIPS-coded county geometries into AHCA's 11 service regions at runtime using `topojson.merge`, then fits a Mercator projection to Florida's bounding box — no pre-processed region GeoJSON required
- Custom Chart.js plugins handle the 2017 peak annotation line and the toggle-able legend with checkbox states, keeping all chart logic self-contained without a plugin registry dependency

> If you would like to discuss the design decisions, data methodology, or extend the dashboard with additional years or metrics, feel free to reach out.

---

## 🌐 Contact

- **Email**: bharadwajmanne.195@gmail.com
- **LinkedIn**: [Bharadwaj Manne](https://www.linkedin.com/in/bharadwaj-manne-711476249/)
- **GitHub**: [Bharadwaj-1953](https://github.com/Bharadwaj-1953)
- **Portfolio**: [bharadwaj.vercel.app](https://bharadwaj.vercel.app)

---
