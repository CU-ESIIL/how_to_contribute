title: "How to Contribute to the OASIS Data Library"
description: "Author guidelines for adding new data source entries and examples to the OASIS Data Library."
-----------------------------------------------------------------------------------------------------------

# How to Contribute to the OASIS Data Library

The OASIS Data Library is a curated collection of **copy-and-paste ready code examples** that show how to download and plot data from trusted sources. Each data source has its own Markdown entry, organized by a tag system for easy discovery.

Contributors are typically:

* **Data managers** who steward datasets and want them to be more accessible.
* **Power users** (e.g., postdocs, analysts) who rely on certain datasets and want to share working code with others.

This page defines the author guidelines for making a contribution.

---

## Structure of the Data Library

* Each data source has a dedicated `.md` file in the `/data-library/` directory.
* Entries are organized by tags for discoverability.
* Example code is embedded directly in the Markdown file (Python, R, or shell).
* Plots and figures live in an `/images/` subdirectory.
* The library is **stream-first**: demonstrate streaming access (STAC, GDAL/VSI, cloud-optimized formats) whenever possible.

---

## Standard Entry Template

Each entry must follow this structure:

````markdown
---
title: NDVI Time Series (MODIS)
author: Jane Doe
date: 2025-09-15
tags: [remote-sensing, vegetation, time-series, global]
source: https://lpdaac.usgs.gov/
license: NASA Open Data License
summary: Example of downloading MODIS NDVI time series and plotting vegetation dynamics.
---

# NDVI Time Series (MODIS)

## Description
The MODIS NDVI dataset provides global vegetation indices at 250m resolution, updated every 16 days.

## Example Code
```python
import xarray as xr
import matplotlib.pyplot as plt

data = xr.open_dataset("https://modis-data.example.com/ndvi_2020.nc")
ndvi = data['NDVI']

ndvi.mean(dim=["lat","lon"]).plot()
plt.title("Global Mean NDVI – 2020")
plt.show()
```

## Output

![NDVI Plot](images/ndvi-example.png)

## Notes

* Requires `xarray` and `matplotlib`.
* Data updates every 16 days.
* Missing values are marked as -9999.

````

---

## Author Guidelines

- **File naming**: use kebab-case, e.g. `ndvi-time-series.md`.
- **Front matter**: include `title`, `author`, `date`, `tags`, `source`, `license`, and `summary`.
- **Code blocks**: must be runnable with copy-paste on a fresh environment; include `import` statements.
- **Access method**: prioritize *stream-first* approaches such as STAC APIs, GDAL/VSI paths, or other remote protocols.
  Only fall back to downloads when streaming is impossible, and then show fully programmatic retrieval—no manual file moves.
- **Plots**: include at least one simple plot. Save example plots to `/images/` with alt text.
- **Dependencies**: list required packages explicitly.
- **Tags**: choose from the controlled vocabulary (climate, fire, vegetation, hydrology, emissions, spatial, time-series, US, global, etc.).
- **Citations**: if relevant, cite publications or documentation.

---

## Naming Conventions

- Files: kebab-case (`fire-perimeters-us.md`).
- Images: `dataset-shortdescription.png`.
- Branches: `data/new-dataset` or `fix/update-code`.
- Commits: use conventional style, e.g. `feat(data): add MODIS NDVI entry`.

---

## Submission Process

1. Fork the repository.
2. Create a branch using the naming convention.
3. Add your `.md` file under `/data-library/`.
4. Add any plot images under `/data-library/images/`.
5. Test the code locally to ensure it runs.
6. Open a Pull Request with a clear title and summary.

---

## Review Standards

- Code must run as-is with no missing imports or hidden steps.
- Plots must render correctly and match the code provided.
- Metadata fields must be complete.
- Tags must follow the controlled vocabulary.
- Access methods should favor streaming (STAC, GDAL/VSI, etc.) or demonstrate automated downloads with no manual steps.
- Links to data sources must resolve.

---

## Example Contributions

??? example "Minimal Dataset Entry"
    ```markdown
    ---
    title: USGS Streamflow Data
    author: John Smith
    date: 2025-09-15
    tags: [hydrology, us, time-series]
    source: https://waterdata.usgs.gov/nwis
    license: Public Domain
    summary: Access and plot daily streamflow data for a USGS gauge.
    ---

    # USGS Streamflow Data

    ## Example Code
    ```python
    import pandas as pd
    import matplotlib.pyplot as plt
    
    url = "https://waterdata.usgs.gov/nwis/dv?format=rdb&sites=06730500&parameterCd=00060&startDT=2020-01-01&endDT=2020-12-31"
    df = pd.read_csv(url, comment="#", sep="\t", header=1)
    
    plt.plot(df['datetime'], df['00060_Mean'])
    plt.title("USGS Streamflow at 06730500 – 2020")
    plt.show()
    ```
    ```

---

## Maintenance

- Automated checks will verify links and code functionality periodically.
- Contributors are expected to update entries if data sources or APIs change.
- Outdated entries may be archived but can be revived with updates.

---

*Consistent formatting and runnable code make the Data Library usable. Thanks for taking the time to prepare your entry carefully.*

