# ⚽ Football Data Analysis HQ

**Exploring the 2023 Africa Cup of Nations through open football event data.**

[![Python Version](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/notebook-Jupyter-orange.svg)](https://jupyter.org/)
[![Data Source](https://img.shields.io/badge/data-StatsBomb%20Open%20Data-1f3864.svg)](https://github.com/statsbomb/open-data)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](#license--acknowledgments)

---

## Table of Contents

- [Overview & Objectives](#overview--objectives)
- [Tech Stack & Dependencies](#tech-stack--dependencies)
- [Dataset Details](#dataset-details)
- [Installation & Setup](#installation--setup)
- [Usage / How to Run the Notebook](#usage--how-to-run-the-notebook)
- [Key Features & Data Output Highlights](#key-features--data-output-highlights)
- [Contributing Guidelines](#contributing-guidelines)
- [License & Acknowledgments](#license--acknowledgments)

---

## Overview & Objectives

**Football Data Analysis HQ** is an exploratory data analysis project focused on the **2023 Africa Cup of Nations (AFCON)** — a tournament that remains comparatively underrepresented in public football analytics work, making it a strong candidate for original analysis.

Using free, open match-event data from StatsBomb, this project walks through the full path from raw API data to a cleaned, analysis-ready dataset:

- Pulling official AFCON 2023 competition, match, and event data programmatically.
- Structuring and cleaning that data into usable tables.
- Performing exploratory analysis on match outcomes and in-match events (shots, passes, and related metrics).

The long-term aim is to build this into a foundation for deeper work — including an Expected Goals (xG) model and tournament-level performance dashboards.

## Tech Stack & Dependencies

| Tool | Purpose |
|---|---|
| **Python 3.12** | Core language |
| **Jupyter Notebook** | Primary analysis environment (`AnalysisHq..ipynb`) |
| **statsbombpy** | Python client for StatsBomb's free open data repository |
| **pandas** | Data manipulation and cleaning |
| **NumPy** | Numerical operations |
| **requests** | Underlying HTTP calls for data retrieval |

## Dataset Details

All data is sourced from [StatsBomb Open Data](https://github.com/statsbomb/open-data), accessed via the `statsbombpy` package — no API key required.

| Detail | Value |
|---|---|
| Competition | Africa Cup of Nations (AFCON) 2023 |
| `competition_id` | `1267` |
| `season_id` | `107` |
| Matches covered | 52 (Group Stage → Final) |
| Data granularity | Match-level results and event-level (shots, passes, and other on-ball actions) |
| Local outputs | `afcon_matches_2023.csv` (match list) and individual per-match event CSVs |

> **Note:** StatsBomb's open data is provided free for public, non-commercial analysis under their [user agreement](https://github.com/statsbomb/open-data). Any published work using this data must credit StatsBomb — see [License & Acknowledgments](#license--acknowledgments).

## Installation & Setup

Clone the repository and set up an isolated Python environment:

```bash
# 1. Clone the repository
git clone https://github.com/Kiletta/Football_Data_Analysis_HQ.git
cd Football_Data_Analysis_HQ

# 2. Create and activate a virtual environment
python3 -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt
```

If a `requirements.txt` isn't yet present in the repo, install the core packages directly:

```bash
pip install statsbombpy pandas numpy requests jupyter
```

## Usage / How to Run the Notebook

1. Activate your virtual environment (see above).
2. Launch Jupyter from the project root:

   ```bash
   jupyter notebook
   ```

3. Open **`AnalysisHq..ipynb`** from the Jupyter file browser.
4. Run the cells sequentially from top to bottom:
   - **Setup** — installs/imports required packages.
   - **Competition discovery** — fetches all available StatsBomb open-data competitions and seasons.
   - **AFCON 2023 extraction** — filters to `competition_id=1267`, `season_id=107`, and pulls the full 52-match list plus event data for each match.
   - **Cleaning & EDA** — inspects, cleans, and explores the resulting match and event datasets.

Running the full notebook will regenerate `afcon_matches_2023.csv` and the per-match event CSVs locally.

## Key Features & Data Output Highlights

- 🔎 **Automated competition discovery** — programmatically lists every free competition/season StatsBomb makes available, rather than hardcoding IDs.
- 📥 **Targeted AFCON 2023 extraction** — pulls exactly the 52 matches of the tournament, from group stage through the final.
- 🧹 **Reproducible cleaning pipeline** — consistent handling of missing values, data types, and match/event identifiers.
- 📊 **Exploratory analysis** — initial breakdowns of match outcomes and event-level metrics (shots, passing activity, and more), laying the groundwork for further modeling.
- 💾 **Local, reusable datasets** — cleaned CSV outputs that can be picked up directly by downstream notebooks or scripts without re-querying the API.

## Contributing Guidelines

Contributions, suggestions, and issue reports are welcome.

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/your-feature-name`.
3. Commit your changes with clear, descriptive messages.
4. Push to your fork and open a Pull Request describing the change.

Please keep notebook cells clean and well-commented, and avoid committing large raw data files where they can instead be regenerated from the notebook.

## License & Acknowledgments

This project is licensed under the **MIT License** — see the `LICENSE` file for details.

**Acknowledgments:**

- Data provided by [StatsBomb](https://statsbomb.com/) via their [Open Data](https://github.com/statsbomb/open-data) repository. StatsBomb's open data is free for public analysis; any published work must credit StatsBomb per their [user agreement](https://github.com/statsbomb/open-data/blob/master/LICENSE.pdf).
- Built with [`statsbombpy`](https://github.com/statsbomb/statsbombpy), the official Python client for StatsBomb open data.

---

<p align="center"><i>Maintained by Kileta — part of an ongoing football analytics portfolio.</i></p>
