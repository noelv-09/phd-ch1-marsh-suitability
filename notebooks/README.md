# notebooks/

Exploratory Jupyter notebooks for Chapter 1.

## Conventions

- Notebooks are for **exploration and figure generation**, not production
  pipelines. Anything reusable migrates to `src/`.
- Clear all outputs before committing (`jupyter nbconvert --clear-output`)
  to keep the diff readable. Large embedded outputs (figures, NetCDF previews)
  bloat the repo.
- Name notebooks `NN_topic.ipynb` (e.g., `01_eof_diagnostics.ipynb`) so the
  intended reading order is obvious.

## Planned notebooks

| Notebook | Purpose | Status |
|----------|---------|--------|
| `01_eof_diagnostics.ipynb` | North's Rule mode-selection plots, scree, spatial EOF maps | Planned |
| `02_cluster_diagnostics.ipynb` | Hierarchical dendrograms, silhouette scores, slack-cluster identification | Planned |
| `03_tier_comparison.ipynb` | Tier 1 vs Tier 2 vs Tier 3 suitability map side-by-sides, R_fallacy table | Planned |
| `04_rcr_geometry_sweep.ipynb` | RCR across channel-geometry scenarios (Chapter 2 hand-off) | Planned |
| `05_physical_audit.ipynb` | Hysteresis, superelevation, vorticity-proxy diagnostics for §1.3.8 | Planned |

## Data dependencies

Notebooks read from `data/` (manifests + small derived files) and write
figures to `docs/figures/`. Raw NetCDF stays outside the repo.
