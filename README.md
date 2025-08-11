# MSc Flood Mapping Thesis  🌊🛰️

This repository contains **all notebooks, models, and data links** for my MSc thesis:

> *“Region-Aligned Self-Supervised Pre-Training for Few-Shot Flood Delineation.”*

## How to reproduce the results

1. **Open Google Colab** → **File ▸ Open notebook ▸ GitHub** → paste this repo URL.
2. Run the notebooks in order:

| Notebook | Purpose |
|---|---|
| `STURMrecreated.ipynb` | Reproduce STURM-Flood baseline |
| `Large_Unlabeled_Pretraining.ipynb` | Region-aligned SatMAE pre-training (streams S2) |
| `Fine-Tuning_on_10_percent_labeled.ipynb` | 10% label experiment |
| `SatMAE_vs_Unet_one_percent.ipynb` | 1% label experiment |
| `SatMAE_vs_Unet_0_5_percent_.ipynb` | 0.5% label experiment |

3. **Before running**  
   - Download files listed in **`DATA_LINKS.md`** (STURM, pre-trained weights, checkpoints).  
   - Place them as expected by each notebook (e.g., `/content/data/weights/`), or edit paths at the top cells.

4. **Pre-training manifest**  
   - Pre-training streams Sentinel-2 prefixes listed in **`s2_prefixes.txt`** (no raw tile download required).

## Repo contents

- `DATA_LINKS.md` — Google Drive URLs for large artefacts (and checksums).  
- `s2_prefixes.txt` — exact S2 scene prefixes used for streaming pre-training.  
- Notebooks — end-to-end reproduction of baseline and few-shot experiments.  
- (Optional) `appendices/`, `figs/`, etc., for thesis assets.

## Questions?

Open an issue or email me at **finanwmkl@gmail.com**.
