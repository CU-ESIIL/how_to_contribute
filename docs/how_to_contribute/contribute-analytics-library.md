---
title: Analytics Library Contributions
description: Author workflow for new OASIS Analytics Library method snippets.
---

# Analytics Library Contributions

The Analytics Library hosts method-focused snippets that operate on common data structures without dataset-specific assumptions. Each snippet is a Markdown file with runnable code and minimal dependencies.

## Standard entry template
Use the following structure for every contribution.

````markdown
---
title: METHOD NAME
author: Your Name
date: YYYY-MM-DD
tags: [choose-from-/how_to_contribute/tag-vocab/]
dependencies: [package-one, package-two]
description: One-sentence summary of what the method produces.
---

# METHOD NAME

## Example code
```python
import pandas as pd
# other imports here

def run_method(df: pd.DataFrame) -> pd.DataFrame:
    """Describe inputs and outputs."""
    # method steps
    return df
```

## Notes
- Mention expected input shapes, column requirements, and outputs.
- Link to references or algorithm documentation if helpful.
````

!!! warning
    Snippets must not rely on hidden global variables. Use explicit imports and parameter names (`df`, `series`, `array`) to stay generic.

## Authoring guidelines
- Store files in `/analytics-library/` and supporting images in `/analytics-library/images/`.
- Keep filenames in kebab-case (for example, `rolling-mean.md`).
- Use tags from the [Controlled Vocabularies](/how_to_contribute/tag-vocab/) page.
- Limit dependencies to widely available packages; list them all in `dependencies`.
- Include assertions or comments that clarify assumptions (e.g., numeric columns, sorted dates).
- Provide optional visualization code only when it aids interpretation.
- Add a short “How to adapt” note when parameters commonly change.

## Naming and branching
- Branches: `analytics/topic-action` (for example, `analytics/rolling-mean`) or `fix/analytics-update`.
- Commits: `feat(analytics): add rolling mean snippet`, `refactor(analytics): tighten deps`, etc.
- Images: `method-shortdescription.png` or `.svg`.

## Submission checklist
- [ ] Front matter includes title, author, date, tags, dependencies, and description.
- [ ] Code imports everything it uses and runs with a sample `df` or similar structure.
- [ ] Dependencies are minimal and documented.
- [ ] Tags conform to the controlled vocabulary.
- [ ] File and branch naming follow conventions.
- [ ] Optional assets stored under `/analytics-library/images/`.

## Submission process
1. Fork the Analytics Library repository and create a feature branch.
2. Draft the Markdown entry plus any supporting demo assets.
3. Run the snippet against a toy dataset to confirm it works with generic column names.
4. Execute repository checks, including the link checker and any notebooks/tests.
5. Open a pull request summarizing the method, dependencies, and testing evidence.
6. Incorporate reviewer feedback promptly.

## Review standards
- Code must execute without manual preprocessing beyond what is documented in the snippet.
- Variable names must remain generic (`df`, `array`, `series`) and avoid proprietary column names.
- Dependencies must be minimal, open source, and justified.
- Tags must match the controlled vocabulary exactly.
- Optional plots must render with the provided code.

## Maintenance expectations
- Periodically validate compatibility with current package versions.
- Respond to automated check failures by updating code or dependencies.
- When deprecating a method, follow the process on [Recognition & Maintenance](/how_to_contribute/recognition/) and link to replacements or alternatives.

??? example "Sample snippet excerpt"
    ```markdown
    ---
    title: Rolling Mean with Confidence Interval
    author: A. Contributor
    date: 2024-02-10
    tags: [temporal, smoothing, visualization]
    dependencies: [pandas, matplotlib]
    description: Smooth a time series and plot the rolling mean with a shaded confidence band.
    ---

    # Rolling Mean with Confidence Interval

    ## Example code
    ```python
    import pandas as pd
    import matplotlib.pyplot as plt

    def rolling_mean_with_ci(df: pd.DataFrame, column: str, window: int = 12) -> pd.DataFrame:
        values = df[column].rolling(window=window, min_periods=window)
        result = pd.DataFrame({
            "center": values.mean(),
            "lower": values.mean() - values.std(),
            "upper": values.mean() + values.std(),
        })
        return result.dropna()

    summary = rolling_mean_with_ci(df, column="value")

    ax = summary["center"].plot(label="Rolling mean")
    ax.fill_between(summary.index, summary["lower"], summary["upper"], alpha=0.3)
    ax.set_title("Rolling mean with ±1σ band")
    ax.legend()
    plt.tight_layout()
    plt.show()
    ```
    ```

