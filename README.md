# Video Website Data Analysis

This repository contains a small end-to-end data project built around performer/profile web scraping, dataset assembly, and exploratory analysis. The core focus is collecting performer data from an adult video website, consolidating it into CSV datasets, and exploring the results in Jupyter notebooks.

The codebase is best understood as a research or portfolio project rather than a production-ready pipeline. It includes raw scripts, intermediate CSV outputs, and notebooks used for data engineering and analysis.

## What Is In This Repo

Primary workflow:

- Scrape performer listing pages and profile pages
- Extract metadata such as rank, views, video counts, verification status, social links, and profile details
- Save page-level outputs into `pornstars/`
- Concatenate or continue building merged datasets such as `concat_data.csv`, `concat_data2.csv`, `concat_data3.csv`, and `concat_data4.csv`
- Explore/clean/analyze the resulting data in notebooks

## Repository Structure

Key files:

- [main.py](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/main.py): main scraping script for performer pages and dataset assembly
- [pornstar.py](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/pornstar.py): helper functions for parsing individual performer/profile pages
- [DataEngineering.ipynb](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/DataEngineering.ipynb): notebook for dataset preparation and transformation
- [DataAnalysis.ipynb](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/DataAnalysis.ipynb): notebook for exploratory analysis and reporting

Important data artifacts:

- [pornstars/](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/pornstars): page-by-page or batch CSV outputs from scraping runs
- [pornstars.csv](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/pornstars.csv): a smaller CSV snapshot
- [concat_data.csv](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/concat_data.csv): consolidated performer dataset snapshot
- [concat_data2.csv](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/concat_data2.csv)
- [concat_data3.csv](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/concat_data3.csv)
- [concat_data4.csv](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/concat_data4.csv)
- [test_concat_data.csv](/Users/harrylu_mac/eros-data/Video-Website-Data-Analysis/test_concat_data.csv): intermediate merged dataset used by the scraper

## Dataset Fields

The performer dataset includes fields such as:

- `Names`
- `Links`
- `Ranks`
- `Total Videos`
- `Total Views`
- `Images`
- `Verified`
- `Pornhub Award`
- `Abouts`
- `Featured In`
- `Social Medias`
- `Detailed Infos`
- `Weekly Ranks`
- `Monthly Rank`
- `Last Month Rank`
- `Yearly Rank`
- `Subscribers`

## Quick Start

This repo does not currently include a `requirements.txt` or packaged environment, so dependencies are inferred from the source code.

Create an environment and install the core libraries:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install pandas requests beautifulsoup4 lxml notebook
```

Run the performer scraper:

```bash
python3 main.py
```

Open the notebooks:

```bash
jupyter notebook
```

## How The Scraper Works

`main.py` builds a list of performer listing pages, scrapes card-level metadata from each page, then calls `porn_star_collect(...)` in `pornstar.py` to fetch and parse each individual profile page.

The scraper extracts:

- listing metadata such as name, rank, total videos, total views, image URL, verification status, and award status
- profile metadata such as bio/about text, featured appearances, social links, structured info fields, and rank/subscriber metrics

The script then writes batch outputs into the `pornstars/` folder and appends merged results into a larger CSV.

## Current Limitations

This repository is useful, but it is still fairly raw. A few practical caveats:

- the scraping scripts are long-running and not parameterized
- request retries, rate limiting, and error handling are minimal
- some scripts execute immediately on import instead of exposing clean functions or CLI entry points
- the repo stores large generated CSVs directly in version control
- there is no dependency lockfile or reproducible environment file
- automated tests are minimal and currently ad hoc

## Notes On Content And Responsible Use

This repository contains NSFW/adult-domain source data and derived datasets. If you are sharing, extending, or publishing from this project, make sure that:

- you are allowed to scrape or reuse the source content under the source site's terms
- you handle any personal or profile data responsibly
- you understand that source-site structure can change and break the scraper at any time

## Suggested Next Improvements

If you want to keep evolving this project, the highest-leverage next steps would be:

1. Add `requirements.txt` or `pyproject.toml`
2. Split scraping, cleaning, and analysis into separate modules
3. Add CLI arguments for page ranges, output path, and resume behavior
4. Add retry logic, timeouts, and polite throttling
5. Add tests for parsing helpers and schema validation
6. Move large generated data to release assets, cloud storage, or Git LFS

## Status

Current repository status:

- useful as a portfolio/research repo
- not yet productionized
- contains both code and generated data snapshots

If you are reviewing the project for hiring, collaboration, or reuse, the notebooks and merged CSV outputs show the project intent quickly, while `main.py` and `pornstar.py` show the scraping logic in detail.
