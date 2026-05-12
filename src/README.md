# src/

Analysis source code for Chapter 1.

## Planned contents

| File | Purpose | Status |
|------|---------|--------|
| `merged_analysis.py` | Main pipeline: read D-Flow FM `FlowFM_map.nc`, compute TPI, run EOF + clustering, generate Tier 1 / Tier 2 / Tier 3 suitability maps, compute RCR and EPI | 🔄 Pending fixed sinuosity calculation |
| `tpi.py` | Topographic Position Index channel/platform delineation (§1.3.3) | Planned |
| `eof_clustering.py` | EOF decomposition + hierarchical / k-means clustering on PC scores (§1.3.4) | Planned |
| `suitability.py` | Tier 1 / Tier 2 / Tier 3 suitability mapping (§1.3.5) | Planned |
| `rcr.py` | Restoration Coherence Ratio (§1.3.6) | Planned |
| `epi.py` | Erosion Potential Index + auxiliary geomorphic metrics (§1.3.7) | Planned |
| `diagnostics.py` | Tidal hysteresis, centrifugal superelevation, vorticity proxy (§1.3.8) | Planned |
| `io_utils.py` | NetCDF loaders for `mesh2d_s1`, `mesh2d_ucx/ucy`, `mesh2d_taus`, etc. | Planned |
| `cli.py` | Command-line entrypoint | Planned |

## Conventions

- **Python ≥ 3.11**, type-hinted, formatted with `ruff format`.
- Each module exposes pure functions where possible; side effects (file I/O,
  plotting) confined to `cli.py` and `notebooks/`.
- Numerical anchors (vthr, τthr, τcrit, depth filter, TPI radius, EOF k) are
  defined as module-level constants in a single `config.py`, not duplicated.
- Tests live in `tests/` (to be added) and use `pytest`.

## Sinuosity bug (outstanding)

The current implementation has a known issue in the sinuosity calculation
from the unstructured grid. The planned fix is to recompute sinuosity
**directly from the `.xyz` bathymetry file** rather than from the centerline
extracted post-hoc. This will be documented in an appendix of Chapter 1
(Appendix B: sinuosity / curvature fix log) once the code is finalized.
