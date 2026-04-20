# STRATFUSE — Multi-Source Intelligence Fusion Dashboard

> **Problem Statement 1** | CyberJoar Hiring Assignment  
> Developed by: Sudheer | Stack: HTML5 · CSS3 · JavaScript · Leaflet.js

---

##  Live Demo

**[https://Sudheer-cpu93.github.io/intelligence_fusion_dashboard/](https://Sudheer-cpu93.github.io/intelligence_fusion_dashboard/)**

---

## Problem Statement

In modern intelligence operations, analysts are overwhelmed by fragmented data arriving from disparate sources — OSINT, HUMINT, and IMINT — spread across databases, spreadsheets, and image galleries. There is a critical need for a **centralized Strategic Fusion Dashboard** capable of ingesting and visualizing multi-modal intelligence data on a single unified interface.

---

##  Solution Overview

**STRATFUSE** is a fully browser-based intelligence fusion dashboard that ingests multi-source data, geo-references each intelligence node, and renders everything as interactive markers on a live dark terrain map — giving analysts a complete **common operating picture** in real time.

---

##  Features

###  Geospatial Map Interface
- Real-time dark terrain map powered by **Leaflet.js + CartoDB Dark**
- All intelligence nodes plotted as animated, color-coded geospatial markers
- Live coordinate tracking as the analyst moves the cursor

###  Multi-Source Data Ingestion
| Source | Method |
|--------|--------|
| **MongoDB / AWS S3** | Simulated cloud pull with animated activity log |
| **CSV / JSON Files** | Drag-and-drop or file browser — auto-parsed and plotted |
| **Satellite Imagery (JPG/PNG)** | Drag-and-drop upload → rendered as IMINT node |
| **Manual Entry** | Form-based node creation with coordinates and metadata |

###  Intelligence Node Types
| Type | Color | Description |
|------|-------|-------------|
| **OSINT** |  Cyan | Open Source Intelligence — social media, news, dark web |
| **HUMINT** |  Green | Human Intelligence — field agent reports |
| **IMINT** |  Orange | Imagery Intelligence — satellite and drone imagery |

### 🖱️ Hover-and-View Popup
- Hovering over any map node triggers an **instant popup** with:
  - Canvas-generated intel visual (unique per node type)
  - Source, timestamp, confidence %, and classification level

###  Dynamic Threat Level Engine
- Auto-calculates a **composite threat score** from node count, classification levels, and confidence ratings
- 5-segment gauge: `MINIMAL → LOW → GUARDED → ELEVATED → HIGH → CRITICAL`
- CRITICAL level triggers a red pulsing animation

###  Search & Classification Filter
- Live keyword search across title, source, notes, and type
- Filter by classification: `ALL / UNCLASSIFIED / SECRET / TOP SECRET`
- All filters apply simultaneously and update the map in real time

###  Export Intelligence Report
- One-click generation of a structured **Intelligence Fusion Report**
- Includes: metadata, threat assessment, summary statistics, full node listing
- Printable as PDF via browser print dialog

###  Real-Time Activity Log
- Every ingestion event, pull, and node addition is time-stamped
- Color-coded by intel type for fast visual scanning

---

##  Tech Stack

| Technology | Usage |
|-----------|-------|
| **HTML5 / CSS3** | Full dashboard layout and styling |
| **Vanilla JavaScript** | All logic, data processing, filtering |
| **Leaflet.js v1.9.4** | Interactive geospatial map |
| **CartoDB Dark Tiles** | Dark terrain map layer |
| **HTML5 Canvas API** | Auto-generated intel visuals per node |
| **FileReader API** | Client-side CSV / JSON / Image ingestion |
| **Google Fonts** | Share Tech Mono · Rajdhani · Exo 2 |

>  Zero dependencies beyond Leaflet. No build tools. No frameworks. Runs entirely in the browser.

---

##  Project Structure

```
intelligence_fusion_dashboard/
│
├── index.html          # Complete single-file dashboard application
└── README.md           # Project documentation
```

---

##  Logic & Architecture

```
Data Sources
    │
    ├── S3 / MongoDB  ──────────┐
    ├── CSV / JSON Upload ──────┤
    ├── Image Upload ───────────┼──► Node Parser ──► Node Store (Array)
    └── Manual Form ────────────┘         │
                                          │
                                   Filter Engine
                                  (type + search + classification)
                                          │
                                   Leaflet Map Renderer
                                  (animated markers + popups)
                                          │
                                   Threat Score Calculator
                                  (classification × confidence × type)
                                          │
                                   Export Report Generator
```

### Key Design Decisions

- **Canvas-generated visuals** — each node type (OSINT/HUMINT/IMINT) gets a unique programmatically-drawn intelligence visual, ensuring zero broken images and full offline capability
- **Single-file architecture** — the entire dashboard is self-contained in one HTML file for maximum portability
- **Composite threat scoring** — threat level weighs classification level (TOP SECRET = 3pts), confidence rating (>90% = 2pts), and node type (IMINT = +1pt) to produce a realistic risk assessment
- **Real-time filter fusion** — source toggles, view mode filter, keyword search, and classification filter all apply simultaneously via a single `nodeVisible()` function

---

##  How to Run Locally

```bash
# No installation required — just open the file
# Option 1: Double-click index.html in your file manager

# Option 2: VS Code with Live Server extension
# Right-click index.html → "Open with Live Server"

# Option 3: Python simple server
python -m http.server 8000
# Then open http://localhost:8000
```

---

##  Dashboard Preview

| Section | Description |
|---------|-------------|
| **Top Bar** | System status, live UTC clock |
| **Threat Bar** | Dynamic threat gauge + search + export |
| **Left Panel** | Source toggles, data ingestion, activity log |
| **Center Map** | Interactive geospatial node visualization |
| **Right Panel** | Live stats, node detail card, manual entry form |

---

##  Submission

Submitted for **CyberJoar Hiring Assignment — Problem Statement 1**  
Contact: Sashrik@cyberjoar.com

---

##  License

Built for evaluation purposes as part of the CyberJoar hiring process.
