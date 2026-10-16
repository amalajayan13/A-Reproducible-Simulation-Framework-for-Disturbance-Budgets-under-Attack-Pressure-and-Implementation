# Secure operating envelope of a BB84-inspired finite-key link

Simulation code for estimating the secure-to-insecure operating boundary of a
BB84-inspired finite-key quantum key distribution link under channel
disturbance, attack pressure and implementation drift.

The notebook `mainv4.ipynb` runs the complete study:

- endpoint Monte Carlo sweep over 85 × 8 × 4 operating conditions (250 replicates each)
- margin-based and probability-based boundary estimation with bootstrap intervals
- shot-count and classification-margin robustness
- repeated trajectory analysis for four representative scenarios
- early-warning validation (pooled and within-condition ROC, lead time)
- coefficient sensitivity and a three-way uncertainty budget
- structural sensitivity (±25% and ±50% coefficients, alternative functional forms)
- comparison of the margin with asymptotic and finite-key bounds
- attack-vector model with loss-only and hidden-leakage components
- key-yield and key-availability analysis

## Requirements

Python 3.10 or later. Install the pinned dependencies with

```
pip install -r requirements.txt
```

The reference results were produced with numpy 2.2.5. Other numpy versions
run correctly but may generate different binomial streams, which changes
values in the trailing decimal places.

## Running

Open the notebook and run all cells, or execute it from the command line:

```
jupyter nbconvert --to notebook --execute bb84_operating_envelope.ipynb
```

A full run takes a few minutes on a laptop. No GPU or compiled extensions are
needed. In Google Colab, outputs are written to Google Drive under
`MyDrive/Outputs`; elsewhere, to `Outputs/` in the working directory.

## Outputs

Each run creates `Outputs/bb84_finite_key_envelope_study_<run id>/` with

| Folder    | Contents |
|-----------|----------|
| `tables/` | all results as CSV files |
| `figures/`| all figures as PNG files (240 dpi) |
| `others/` | run manifest (seed, software versions, platform) and text summaries |

## Reproducibility

All random draws come from NumPy generators seeded from a single base seed
(`SEED = 42`). Each analysis uses its own stream, so any section can be
modified or removed without changing the results of the others.

## Citation

If you use this code, please cite the accompanying article.
