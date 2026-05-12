# data/

## What lives here

- **Manifests** (CSV / YAML) describing where the raw D-Flow FM outputs live,
  their checksums, run configuration, and tidal forcing references.
- **Small derived files** that are cheap to regenerate but useful for quick
  inspection (e.g., timestamp lists for the Tier 3 slack cluster, sinuosity /
  curvature CSVs once the fix is in).
- **Configuration YAML** for the run sweeps in Chapter 2.

## What does NOT live here

Per `.gitignore`, the following are excluded from version control:

- Raw NetCDF map files (`FlowFM_map.nc`) — typically GB-scale per run.
- `.npy`, `.npz`, `.parquet` derived arrays.
- Bathymetry `.xyz` files.
- GIS rasters and shapefiles.

These are tracked externally (HPC scratch, institutional storage, or a
data archive like Zenodo at the time of publication). The manifests here
point to those locations.

## Planned structure

```
data/
├── README.md                          ← this file
├── manifests/
│   ├── runs.csv                       ← one row per D-Flow FM run (name, config, output path, checksum)
│   ├── forcing_references.yaml        ← Skagit Bay tidal forcing provenance
│   └── bathymetry_sources.yaml        ← .xyz file provenance and elevation datum
├── configs/
│   ├── baseline.yaml                  ← representative-case config used in Chapter 1
│   └── scenarios/                     ← per-geometry configs for Chapter 2 sweep
└── derived/
    ├── slack_timestamps.csv           ← Tier 3 timestamp set per run (placeholder)
    └── sinuosity_curvature.csv        ← post-fix geometry metrics (placeholder)
```

(All `manifests/`, `configs/`, and small `derived/` files are tracked. The
larger derived arrays under `derived/*.npy`, `derived/*.npz`,
`derived/*.parquet` are gitignored.)
