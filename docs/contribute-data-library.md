# Contribute to the Data Library

**Goal:** cut‑and‑paste R/Python that connects to a dataset, plus one **raw‑data plot** to prove it worked, and **scientific context** so users apply it responsibly.

## Required sections
1. **Overview** — what the dataset is; coverage; variables; resolution.
2. **Access / Streaming** — R and/or Python snippet that downloads/streams the data.
3. **Quick raw‑data plot** — immediate plot of what you just pulled.
4. **Scientific context** — how people use this scientifically; caveats.
5. **Citation** — how to cite dataset and creators.
6. **Troubleshooting** — common errors, auth, CRS, etc.

> **Reminder:** Every Data Library page must include one quick **raw-data plot** immediately after access, to show that the code worked.

## Author checklist
- [ ] Streams/downloads from an authoritative source
- [ ] One quick plot of the **raw** data to prove it works
- [ ] Scientific context (what, where, why, how used)
- [ ] Full citation & license
- [ ] Links live; assets < 2 MB; alt text present

## Style sheet (authoritative)
Follow the Data Library style rules:  
https://github.com/CU-ESIIL/data-library/blob/main/STYLE_SHEET.md

## Tiny example (placeholder)
```python
# Python
# df = fetch_dataset(...)
# df.plot(); plt.show()  # raw diagnostic plot
```

```r
# R
# df <- fetch_dataset(...)
# plot(df)               # raw diagnostic plot
```
