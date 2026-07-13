# When the Water Remembers
### Ocean Sessions Dataviz Challenge 2026 — Copernicus Marine Service

**Author:** Sunday Kenneth Shaho · GIS Analyst · Nigeria  
**Challenge:** [Ocean Sessions Dataviz Challenge 2026](https://events.marine.copernicus.eu/ocean-sessions-dataviz-challenge)  
**Submission format:** Interactive HTML · Single self-contained file  
**Data source:** Copernicus Marine Service (CMEMS)

---

## The Story

The Gulf of Guinea is changing. Its water is warmer than it has ever been in the satellite record. Its sea level has risen 106 millimetres since 1993 and is still climbing. Its seasonal phytoplankton cycle — the heartbeat that drives the entire coastal food web — is shifting in ways that directly shorten the productive fishing season.

These aren't projections. They're measurements.

This project tells that story through three decades of real Copernicus Marine Service data, narrated from the shoreline of Badagry, Nigeria, by a woman named Amara whose family has lived that story long before any satellite confirmed it.

---

## Live Demo

> Open `When_The_Water_Remembers_COMPLETE.html` in any modern browser.  
> The file is fully self-contained — no internet connection required after download.

---

## Three-Act Structure

### Act I — The Gulf Has Forgotten How to Cool Down
*Blue Ocean · Sea Surface Temperature*

The Gulf of Guinea has warmed at **+0.22°C per decade** since 1993 — statistically significant at p < 0.001. All five warmest years in the 33-year record fall after 2016. March 2024 recorded 28.70°C, the single hottest month ever observed in this dataset. The 2024 annual mean anomaly reached +0.82°C above the 1993–2016 climatological baseline of 25.39°C.

The visualization shows this as a living ribbon heatmap — three overlapping sine waves mimic surface current turbulence while a travelling heat-pulse sweeps the chart continuously, the baseline visibly drifting warmer from left to right.

### Act II — My Mother's Net Comes Back Lighter
*Green Ocean · Chlorophyll-a & Marine Food Web*

The story here is more nuanced than a simple decline. The overall chlorophyll trend shows a modest +8.7% over the period — but the seasonal pattern is shifting. The off-season winter minimum (January–April) has declined across the most recent decade, even as the summer upwelling peak holds. A warmer ocean stratifies more strongly, upwelling weakens, and the productive season shortens.

The visualization pairs an animated monthly CHL time series against a line-racer seasonal climatology — three coloured runners racing across 12 months, each representing a decade — and closes with an interactive Marine Food Chain Sankey diagram showing the narrowing flow from riverine nutrients through phytoplankton, zooplankton, and small pelagics to coastal fishing communities.

### Act III — Water in the Living Room
*Blue Ocean · Sea Level Anomaly*

The most dramatic signal in the dataset. Sea level in the Gulf of Guinea has risen at **3.32 mm/yr** — above the global average. The April 2024 monthly anomaly reached **141.8 mm**, the highest single value in the full record. The annual mean climbed from ~5 mm in 1993 to 114 mm by 2024. Negative SLA months, once common in the 1990s, have essentially disappeared since 2018.

The visualization renders this as a flood-fill animation — water rising from the 1993 baseline, colour-shifting from teal through amber to deep red as it climbs, with expanding ripple rings at the leading edge.

---

## Datasets

All data downloaded directly from the Copernicus Marine Service data portal.

| Variable | Product ID | Dataset | Temporal Res. | Spatial Res. | Period |
|---|---|---|---|---|---|
| Sea Surface Temperature | `GLOBAL_MULTIYEAR_PHY_001_030` | `cmems_mod_glo_phy_my_0.083deg_P1M-m` | Monthly | 1/12° (~8 km) | 1993–2025 |
| Sea Level Anomaly | `SEALEVEL_GLO_PHY_L4_MY` | DUACS gridded altimetry | Monthly | 1/4° (~28 km) | 1993–2025 |
| Chlorophyll-a | `OCEANCOLOUR_GLO_BGC_L4_MY_009_104` | GlobColour L4 gap-free | Monthly | 4 km | 1997–2025 |

**Record counts:** SST — 396 months · SLA — 393 months · CHL — 396 months

**Why L4 for ocean colour:** The Gulf of Guinea sits under the Inter-Tropical Convergence Zone (ITCZ) cloud belt. L3 daily satellite products are severely incomplete or entirely missing on most days in this region. L4 gap-free interpolated products are the only reliable choice for continuous regional analysis.

---

## Key Findings

- **SST warming trend:** +0.22°C per decade (p < 0.001 · 33-year record)
- **Climatological mean:** 25.39°C (1993–2016 baseline)
- **Record month:** March 2024 at 28.70°C
- **Sea level rise rate:** 3.32 mm/yr
- **Total SLR since 1993:** 106 mm
- **Record SLA month:** April 2024 at 141.8 mm
- **Peak CHL month:** July 2014 at 0.397 mg m⁻³
- **CHL seasonal swing:** 0.149 mg m⁻³ (February) → 0.321 mg m⁻³ (August)

---

## Visualization Features

- **7 animated canvas charts** across three acts
- **Continuous ocean-current heatmap** with three-frequency sine-wave turbulence and a travelling heat-pulse
- **Line-racer seasonal CHL chart** — three decade runners racing simultaneously across 12 months
- **Flood-fill SLA animation** — water rising with ripple rings at the leading cursor
- **Interactive Marine Food Chain Sankey** with three era toggles (1993–97 baseline / 2020–24 current / compare both) and hover tooltips on each food chain node
- **5 CMEMS MyOcean Viewer screenshots** embedded as JPEG — THETAO March 2024, CHL February 2025, CHL August 2025, SLA April 2004, SLA April 2024
- **ArcGIS Pro locator map** with pulsing animated Badagry marker
- **Closing resolution panel** with causal narrative and data summary
- All animations replay every 7 seconds

---

## Methodology

**SST anomalies** are computed relative to the 1993–2016 climatological monthly mean (25.39°C) derived from the GLORYS12 reanalysis. GLORYS12 assimilates along-track altimeter sea level anomaly, satellite SST, sea ice concentration, and in-situ temperature and salinity profiles. Known regional temperature biases are less than 0.4°C with respect to the World Ocean Atlas climatology.

**Sea Level Anomaly** values were converted from metres to millimetres. The DUACS altimetry product merges data from multiple satellite missions including TOPEX/Poseidon, Jason-1/2/3, and Sentinel-6.

**Chlorophyll-a** from the GlobColour L4 product uses multi-sensor fusion across SeaWiFS, MODIS, MERIS, VIIRS-SNPP & JPSS1, and OLCI-S3A & S3B to fill cloud gaps through space-time interpolation.

The study region covers approximately **5°W–9°E, 0–6°N** — the coastal Gulf of Guinea centred on the Nigerian EEZ and Badagry shoreline.

---

## Tools & Stack

| Tool | Purpose |
|---|---|
| **CMEMS Data Portal** | Data download (thetao, sla, chl) |
| **ArcGIS Pro** | Locator map cartography |
| **Python · Pillow · Pandas** | Data processing and image compression |
| **HTML / CSS / JavaScript** | Complete interactive visualization |
| **Canvas API** | All chart rendering and animation |

No external JavaScript libraries. No framework dependencies. The entire visualization runs on native browser APIs.

---

## File Structure

```
When_The_Water_Remembers_COMPLETE.html   ← full submission (single file)
README.md                                ← this document
```

The HTML file is self-contained at approximately 2.2 MB. All data, images, fonts, and JavaScript are embedded. It opens directly in any modern browser — Chrome, Firefox, Safari, Edge — with no server required.

---

## Geographic Context

**Badagry** (6.42°N, 2.88°E) is a coastal town in Lagos State, southwestern Nigeria, situated on the Gulf of Guinea between a tidal creek and the Atlantic Ocean. It is one of the oldest towns in Nigeria and has been a fishing and trading community for centuries. Today it sits in one of the most exposed low-elevation coastal zones in West Africa — flat, densely populated, and directly in the path of rising seas.

The Gulf of Guinea coastline from Liberia to Gabon is home to over 200 million people. Fishing communities along this coast rely on the seasonal upwelling cycle — the same cycle this project shows shifting and shortening under sustained ocean warming.

---

## About This Project

This project was built for the **Ocean Sessions Dataviz Challenge 2026**, hosted by the Copernicus Marine Service as part of the Ocean Sessions event series. The challenge invited participants to create a visualization based on CMEMS open ocean data in any format — static, animated, or interactive.

The narrative choice — a first-person West African coastal voice, three causally linked ocean signals, a human story grounded in real data — reflects a conviction that ocean science communication is most powerful when it starts from lived experience and lets the data confirm what communities already know.

*The ocean has been speaking for thirty years. In Badagry, we have been listening. Now it is time for the world to hear.*

---

## License

Data © Copernicus Marine Service (CMEMS) — open access under the [Copernicus Marine Service Terms of Use](https://marine.copernicus.eu/user-corner/service-commitments-and-licence).

Visualization code and narrative © Sunday Kenneth Shaho 2026.

---

*Sunday Kenneth Shaho · GIS Analyst · Nigeria*  
*Ocean Sessions Dataviz Challenge 2026*
