---
title: Data Library Contributions
description: Author workflow for new OASIS Data Library entries.
---

# Data Library Contributions

The OASIS Data Library collects runnable, copy-paste examples that retrieve data from a single source and produce a basic visualization. Each entry is a Markdown page stored in the Data Library repository.

## Standard entry template
Use this layout for every entry. Adapt values but keep the structure.

````markdown
---
title: TITLE OF DATA SOURCE
author: Your Name
date: YYYY-MM-DD
tags: [choose-from-/how_to_contribute/tag-vocab/]
source: https://source-url.example.org
license: SOURCE LICENSE NAME
summary: One-sentence description of what the code does.
---

# TITLE OF DATA SOURCE

## Description
Brief context about the dataset, typical use cases, and update cadence.

## Example code
```python
import pandas as pd
import matplotlib.pyplot as plt

url = "https://example.org/data.csv"
df = pd.read_csv(url)

ax = df.plot(x="date", y="value", figsize=(8, 4))
ax.set_title("Descriptive title")
plt.tight_layout()
plt.show()
```

## Notes
- Dependencies required to run the snippet.
- Caveats such as missing value markers or authentication needs.
````

!!! note
    Include explicit imports, URLs, and parameters so contributors can run the snippet without guessing hidden steps.

## Authoring guidelines
- Place entries in the `/data-library/` directory and images in `/data-library/images/`.
- Keep filenames in kebab-case, such as `global-fire-emissions.md`.
- Use tags from the [Controlled Vocabularies](/how_to_contribute/tag-vocab/) page only.
- Favor streaming or API access (STAC, cloud-optimized formats, direct CSV URLs). If downloads are required, script them end-to-end.
- Document authentication steps if tokens or environment variables are needed.
- Provide at least one figure or table. Supply alt text and store assets locally.
- List Python or R packages needed for the example and pin unusual versions.
- Cite data sources and documentation links in a References or Notes section.

## Naming and branching
- Branch names: `data/topic-shortdescription` (for example, `data/modis-ndvi`) or `fix/data-update`.
- Commit messages: follow `feat(data): ...`, `fix(data): ...`, or `docs(data): ...`.
- Image naming: `dataset-shortdescription.png` or `.svg`.

## Submission checklist
- [ ] Front matter includes title, author, date, tags, source, license, and summary.
- [ ] Code runs from a clean environment using documented dependencies.
- [ ] Plot or table renders and is saved under `/data-library/images/` if embedded.
- [ ] Tags adhere to the controlled vocabulary.
- [ ] Links to sources and docs resolve.
- [ ] Branch and file naming follow conventions.

## Submission process
1. Fork the Data Library repository and create a branch.
2. Add your Markdown entry and any supporting images.
3. Test the snippet in a fresh environment or container.
4. Run repository checks, including the link checker workflow when available.
5. Open a pull request summarizing the dataset, testing evidence, and any follow-up tasks.
6. Respond to review comments and update the entry until approved.

## Review standards
- Metadata fields must be complete and accurate.
- Code must execute without manual file moves or missing imports.
- Tags must match the controlled vocabulary exactly.
- Visual outputs must align with the code and include descriptive captions or alt text.
- Entries that cannot be run due to inaccessible data will be requested to add fallbacks or be declined.

## Maintenance expectations
- Monitor the source for API or URL changes and update entries proactively.
- Automated link and runtime checks may flag issues; address them promptly.
- If an entry becomes obsolete, mark it as deprecated with guidance for replacement and link to updates in [Recognition & Maintenance](/how_to_contribute/recognition/).

??? example "Sample entry excerpt"
    ```markdown
    ---
    title: Global Surface Temperature Anomaly (GISTEMP)
    author: A. Contributor
    date: 2024-01-15
    tags: [climate, global, temporal, visualization]
    source: https://data.giss.nasa.gov/gistemp/
    license: Public Domain
    summary: Download global monthly temperature anomalies and plot a quick line chart.
    ---

    # Global Surface Temperature Anomaly (GISTEMP)

    ## Example code
    ```python
    import pandas as pd
    import matplotlib.pyplot as plt

    url = "https://data.giss.nasa.gov/gistemp/tabledata_v4/GLB.Ts+dSST.csv"
    df = pd.read_csv(url, skiprows=1)

    monthly = df.melt(id_vars=["Year"], value_vars=["Jan", "Feb", "Mar"], var_name="month", value_name="anomaly")
    monthly.dropna(inplace=True)

    ax = monthly.plot(x="Year", y="anomaly", kind="scatter", s=10)
    ax.set_ylabel("Temperature anomaly (°C)")
    ax.set_title("GISTEMP monthly anomalies")
    plt.tight_layout()
    plt.show()
    ```
    ```

