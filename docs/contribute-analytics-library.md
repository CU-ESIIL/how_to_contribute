# How to Contribute to the OASIS Analytics Library

The OASIS Analytics Library is a collection of **copy-and-paste ready code snippets** for common analytics methods. These snippets are designed to be:

* **Generic**: methods that work with common data types (numeric, categorical, temporal, spatial).
* **Minimal**: no unnecessary dependencies, runnable with simple imports.
* **Educational**: code is clear, commented, and easy to adapt.

Contributors are usually:

* **Data managers** who want to provide accessible analytics methods alongside datasets.
* **Heavy users** (e.g. postdocs, analysts) who rely on methods and want to share tested workflows with others.

---

## Structure of the Analytics Library

* Each analytics method has its own `.md` file in `/analytics-library/`.
* Snippets are organized by tags (numeric, categorical, temporal, spatial, visualization, etc.).
* Code is embedded directly in the Markdown file.
* Snippets may include optional output images or plots, stored in `/images/`.

---

## Standard Entry Template

Each entry must follow this format:

````markdown
---
title: Correlation Heatmap
author: Jane Doe
date: 2025-09-15
tags: [numeric, visualization, correlation]
dependencies: [pandas, seaborn]
description: Given a DataFrame of numeric variables, plot pairwise correlations as a heatmap.
---

# Correlation Heatmap

## Example Code
```python
import seaborn as sns
import matplotlib.pyplot as plt

# Assume `df` is a pandas DataFrame with numeric columns
corr = df.corr()
sns.heatmap(corr, annot=True, fmt=".2f", cmap="coolwarm")
plt.title("Correlation Heatmap")
plt.show()
````

## Notes

* Requires `pandas` and `seaborn`.
* Works only with numeric columns; drop categorical variables beforehand.
* NaN handling follows pandas defaults.

````

---

## Author Guidelines

- **File naming**: use kebab-case, e.g. `correlation-heatmap.md`.
- **Front matter**: include `title`, `author`, `date`, `tags`, `dependencies`, and `description`.
- **Code blocks**: must run as-is; include all imports.
- **Variables**: use generic names like `df` or `data`, not dataset-specific ones.
- **Dependencies**: keep minimal and document explicitly.
- **Plots**: include one simple plot when relevant; store images in `/images/`.
- **Tags**: choose from controlled vocabulary: `numeric`, `categorical`, `temporal`, `spatial`, `visualization`, `transformation`, `grouping`, `missing-data`.
- **Style**: write in plain, clear language; keep sentences short and imperative.

---

## Naming Conventions

- Files: kebab-case (`time-series-smoothing.md`).
- Images: `method-shortdescription.png`.
- Branches: `analytics/new-method` or `fix/update-snippet`.
- Commits: `feat(analytics): add correlation heatmap snippet`.

---

## Submission Process

1. Fork the repository.
2. Create a branch using the naming convention.
3. Add your `.md` file under `/analytics-library/`.
4. Add any plots/images under `/analytics-library/images/`.
5. Test the code locally to ensure it runs as written.
6. Open a Pull Request with a clear title and summary.

---

## Review Standards

- Code must run as provided with no missing imports.
- Snippets must be generic (no dataset-specific column names).
- Metadata fields must be complete.
- Tags must follow the controlled vocabulary.
- Dependencies must be minimal and documented.
- Output plots (if included) must render and match the code.

---

## Example Contribution

```markdown
---
title: Frequency Table of Categorical Variable
author: John Smith
date: 2025-09-15
tags: [categorical, summary]
dependencies: [pandas]
description: Count the frequency of each category in a DataFrame column.
---

# Frequency Table of Categorical Variable

## Example Code
```python
import pandas as pd

# Assume `df` is a pandas DataFrame with a categorical column `species`
counts = df['species'].value_counts()
print(counts)
````

## Notes

* Works with any categorical column.
* Use `.plot.bar()` on the counts to create a bar chart if desired.

```

---

## Maintenance

- Automated checks will test snippets against toy data structures.
- Contributors are expected to update entries if dependencies or APIs change.
- Outdated entries may be archived but can be revived with updates.

---

*Simple, generic, and runnable snippets are what make the Analytics Library useful. Thanks for contributing carefully.*

```
