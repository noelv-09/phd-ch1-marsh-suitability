# docs/

Figures, tables, and the eventual reproducibility appendix for Chapter 1.

## Planned structure

```
docs/
├── README.md                          ← this file
├── figures/
│   ├── 01_introduction/               ← problem-framing schematics
│   ├── 02_background/                 ← literature-context figures
│   ├── 03_methods/                    ← pipeline schematics (EOF + clustering, TPI, RCR)
│   ├── 04_results/                    ← Tier 1 / 2 / 3 suitability maps, R_fallacy plots, RCR sweeps
│   └── _generated/                    ← scratch outputs from notebooks (gitignored)
├── tables/
│   ├── suitability_metric_lineage.md  ← Table 1.3.0 (governing-equation lineage)
│   ├── rigor_criteria.md              ← Table 1.3.1 (methodological rigor criteria)
│   └── tier_comparison_summary.csv    ← effect-size summary across Tier 1/2/3
└── reproducibility/
    ├── environment.md                 ← Python / conda environment, HPC modules
    ├── run_instructions.md            ← how to reproduce baseline + sweeps
    └── data_sources.md                ← provenance for forcing, bathymetry, observations
```

## Figure-style conventions

- Vector formats (PDF, SVG) preferred for publication-quality figures.
- PNG at 300 dpi for slides and quick-look figures.
- Colormap: `viridis` for sequential data; `cmocean.balance` for divergent
  (e.g., Tier 1 − Tier 3 difference maps).
- Coordinate frames in **meters** with explicit datum noted in figure caption
  (NAVD88 for elevations referenced to Fir Island Farm).

## Reproducibility appendix

The `reproducibility/` subdirectory will eventually become **Appendix A** of
the dissertation (annotated `merged_analysis.py`) and **Appendix B**
(sinuosity / curvature fix log) — these are deferred until the code is
finalized.
