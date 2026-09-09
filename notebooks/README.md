# Notebooks

Demonstration notebooks for the Chapter 1 tidal-marsh restoration suitability
pipeline. These are teaching notebooks that run on **synthetic data**; the
production pipeline consumes D-Flow FM output on the Auburn Easley HPC cluster
and is released alongside the manuscript after committee review.

## Available notebooks

### `tier3_demo.ipynb` — Tier 3 post-processing on a synthetic tidal channel

Walk-through of the Tier 3 pipeline (EOF decomposition → k-means clustering on
principal components → slack-state identification → Tier 1 vs Tier 3
suitability comparison) on a small analytical marsh-and-channel domain. Runs
in under 10 seconds; no NetCDF, no D-Flow FM, no HPC access required.

**Run it in the browser (no install):**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelv-09/phd-ch1-marsh-suitability/blob/main/notebooks/tier3_demo.ipynb)

> **Private-repo note.** While this repository is private, the Colab launcher
> requires Colab to be authorised against your GitHub account and requires
> read access to `noelv-09/phd-ch1-marsh-suitability`. When the repository
> becomes public, the launcher works for anyone without authorisation.

**Run it locally:**

```bash
git clone https://github.com/noelv-09/phd-ch1-marsh-suitability.git
cd phd-ch1-marsh-suitability
python -m pip install numpy scipy scikit-learn matplotlib jupyter
jupyter lab notebooks/tier3_demo.ipynb
```

**What it demonstrates**

- Synthesising phase-resolved D-Flow FM-like fields (`s1`, `speed`, `taus`)
  over a 50 × 50 idealised marsh domain with a sinuous channel and a mixed
  semidiurnal M2 + S2 tide
- EOF decomposition of the centered shear-stress anomaly (SVD)
- k-means clustering on the leading two principal components
- Slack-state identification as the two lowest-mean-speed clusters
  (HW-slack and LW-slack analogues)
- Tier 1 (tidally-averaged threshold) vs Tier 3 (slack-only threshold)
  suitability maps and the reporting triple: `R = A_T1 / A_T3`, T1 over-call
  percentage, and Cohen's κ

**What it deliberately omits** (see the notebook's closing section for
the full pipeline mapping to `src/` modules):

- NetCDF loaders (`mesh2d_s1`, `mesh2d_ucx/ucy`, `mesh2d_taus`)
- Controlled `.xyz` bathymetry generation with tapered inverts
- 21-scenario sensitivity sweep across side slope, cluster count, and
  thresholds
- Ebb-residual streamlines and drain-window platform fraction diagnostics
- Restoration Coherence Ratio (RCR) and Ecological Persistence Index (EPI)
- Bathymetry QC guardrails and boundary-buffer checks

## Reproducing the real pipeline

The production Chapter 1 pipeline runs on Auburn Easley HPC via SLURM job
chains submitted with `run_all_scenarios.sh`. Code migration into this
repository follows the committee review and manuscript-submission timeline.
