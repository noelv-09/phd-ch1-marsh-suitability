# PhD Chapter 1 — Channel Geometry Influence on Restoration Suitability

**Author:** Noelani Villa
**Program:** Civil & Environmental Engineering (Water Resources), University of New Mexico
**Status:** 🚧 Pre-defense draft (Fall 2026 target)
**Visibility:** Private — code and manuscript not yet released

---

## Overview

This repository houses the analysis code, configuration files, and reproducibility
artifacts for **Chapter 1** of the dissertation:

> *Tier 3 post-processing of D-Flow FM output for tidal-marsh restoration suitability:
> empirical orthogonal function decomposition, hierarchical clustering, and the
> Restoration Coherence Ratio.*

The chapter develops a phase-resolved post-processing framework that replaces
conventional time-averaged (**Tier 1**) and percentile-based (**Tier 2**) suitability
metrics with an EOF + clustering pipeline (**Tier 3**) that isolates slack-water
states relevant to pioneer salt-marsh seed settlement.

The manuscript LaTeX is **not** in this repo yet — it will be added after committee
review.

---

## Three-tier post-processing taxonomy

| Tier | Reduction | Suitability map driven by |
|------|-----------|----------------------------|
| **Tier 1** | Time-averaged per cell | Tidal-cycle-mean velocity and shear |
| **Tier 2** | Percentile / threshold-exceedance per cell | Exceedance statistic of velocity or shear |
| **Tier 3** | Phase-resolved subset of timestamps | EOF + clustering → slack-water states only |

---

## Research questions

- **RQ1.** Can EOF decomposition + hierarchical clustering on D-Flow FM output
  objectively identify slack-water timestamps for seed-settlement evaluation?
- **RQ2.** Does substituting Tier 3 inputs for Tier 1 / Tier 2 inputs change the
  magnitude, spatial pattern, and apparent suitable area of restoration-suitability
  maps — and by an amount exceeding documented input-side uncertainty?
- **RQ3.** Does the Restoration Coherence Ratio (RCR) discriminate between
  channel-geometry configurations with equivalent suitable area but distinct
  patch organization?

---

## Repository layout

```
.
├── README.md                  ← this file
├── .gitignore                 ← Python / LaTeX / macOS / NetCDF ignores
├── LICENSE-PLACEHOLDER.md     ← license decision deferred until release
├── src/                       ← analysis code (merged_analysis.py lands here)
│   └── README.md
├── notebooks/                 ← exploratory + figure-generating notebooks
│   └── README.md
├── data/                      ← manifests + small derived files only
│   └── README.md              ← (raw NetCDF outputs are NOT version-controlled)
└── docs/                      ← figures, tables, reproducibility appendix
    └── README.md
```

(Chapter manuscript files — `Chapter1.tex`, `refs.bib`, `Chapter1.pdf`,
consolidated markdown — will be added under `chapter/` after committee review.)

---

## Methodological anchors (locked)

| Parameter | Value | Reference |
|-----------|-------|-----------|
| Grid spacing | ~0.25 m unstructured triangular mesh | §1.3.2 |
| Tidal forcing | Skagit Bay observed tides | Yang et al. (2006); Williams et al. (2014) |
| Marsh slope | Fir Island Farm field measurement | Grossman et al. (2011) |
| Velocity threshold (vthr) | 0.03 m/s | Cao et al. (2018); Fivash et al. (2021) |
| Shear threshold (τthr) | 0.1 Pa | Cao et al. (2018); Fivash et al. (2021) |
| Critical erosion shear (τcrit) | 0.3 Pa | Grabowski et al. (2011) |
| Depth filter for slack cluster | h > 0.10 m | §1.3.4 |
| EOF mode retention | k = 10 via North's Rule | North et al. (1982) |
| TPI radius | 50 m, threshold = −0.05 m | De Reu et al. (2013); Weiss (2001) |
| Fallacy ratio (representative case) | R_fallacy ≈ 1.764 (~76% overestimation) | Chapter 2 |

---

## Build / run (placeholder)

```bash
# Environment setup (to be finalized once src/ is populated)
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt   # not yet committed

# Run the pipeline (entrypoint to be added under src/)
# python -m src.merged_analysis --config config/baseline.yaml
```

---

## Citation

If using code or methods from this repository in your own work (after public
release), please cite:

> Villa, N. (in prep.). *Channel Geometry Influence on Restoration Suitability*.
> PhD Dissertation, Chapter 1, University of New Mexico.

A formal CITATION.cff file will be added at the time of public release.

---

## License

License decision is **deferred** — see `LICENSE-PLACEHOLDER.md`. All rights
reserved until that decision is made.
