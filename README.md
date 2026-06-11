# mundial-2026
Interactive dashboard for the 2026 FIFA World Cup with real-time data

Overview

A real-time analytics dashboard for the FIFA World Cup 2026, tracking every match, group standing, top scorer, and assist leader across 48 teams playing in Canada, USA, and Mexico.

Live site: jairo-buenaventura.github.io/mundial-2026

Tech Stack

LayerTechnologyData sourceAPI-Football — paid plan (league=1, season=2026)Data pipelinePython (Jupyter Notebook) — automated every 3 minutesStorageExcel (.xlsx) synced to OneDrive (Universidad Piloto de Colombia)VisualizationPower BI Service — published dashboard via iframeFrontendHTML + Bootstrap 5 + Leaflet.js — hosted on GitHub PagesMapLeaflet.js with live API-Football data per venue

Project Structure

mundial-2026/
├── index.html          # Main page (dashboard, widgets, map)
├── colombia.html       # Colombia national team page
├── Mundial2026_auto.ipynb  # Automated Python pipeline
└── README.md

How It Works

API-Football (every 3 min)
        ↓
Jupyter Notebook (Python)
        ↓
mundial_2026.xlsx (OneDrive)
        ↓
Power BI Service (8x/day refresh)
        ↓
GitHub Pages (public website)

Excel File Structure (mundial_2026.xlsx)

SheetDescriptionPartidosAll 72 matches with results, venues, roundsStandingsGroup stage standingsGoleadoresTop scorersAsistentesTop assist leadersGruposGroup list

Setup & Installation

1. Clone the repository

bashgit clone https://github.com/jairo-buenaventura/mundial-2026.git

2. Install Python dependencies

bashpip install requests pandas openpyxl schedule

3. Configure your API key

In Mundial2026_auto.ipynb, update:

pythonAPI_KEY = "your_api_football_key"
EXCEL_PATH = "/your/path/to/mundial_2026.xlsx"

4. Run the pipeline

Open Mundial2026_auto.ipynb in Jupyter and run all cells in order:

Cell 1 — imports and config
Cell 2 — defines the update function
Cell 3 — starts the automated loop (every 3 minutes)

To stop: Kernel → Interrupt

5. Power BI

Dataset connected to OneDrive via SharePoint URL
Scheduled refresh: 8 times/day (aligned with Colombia timezone UTC-5)
No on-premises gateway needed

API-Football Configuration

Host: v3.football.api-sports.io
Header: x-apisports-key
League: 1 (FIFA World Cup)
Season: 2026
Endpoints used:
  - /fixtures
  - /standings
  - /players/topscorers
  - /players/topassists
  - /fixtures/rounds

API consumption: ~5 calls per execution × every 3 min ≈ 2,400 calls/day (plan allows 7,500/day)

### ⚠️ API Key Notice
This project uses a personal API-Football key for demonstration purposes.
If you clone or fork this repository, **you must replace the API key with your own**.
Get your free key at [api-football.com](https://www.api-football.com/).

Replace it in:
- `index.html` — in the map script and widget config
- `Mundial2026_auto.ipynb` — in Cell 1

Author

Jairo Buenaventura
MSc High Performance Sports Training (Football) · Universidade do Porto


🔗 LinkedIn
🐦 X / Twitter
💻 GitHub

