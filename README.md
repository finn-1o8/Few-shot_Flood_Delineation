# MSc Flood Mapping Thesis 

This repository contains **all notebooks, models, and data links** for my MSc thesis:

> *"Region-Aligned Self-Supervised Pre-Training for Few-Shot Flood Delineation"*.

## How to reproduce the results

1. **Open Google Colab** → click **File ▸ Open notebook ▸ GitHub** → paste this repo URL.  
2. Run the notebooks in order  

   | Notebook | Purpose |
   |----------|---------|
   | `STURMrecreated.ipynb` | Reproduce STURM baseline |
   | `Large_Unlabeled_Pretraining.ipynb` | Pre-train SatMAE encoder |
   | `Fine-Tuning_on_10_percent_labeled.ipynb` | 10 % label experiment |
   | `SatMAE_vs_Unet_one_percent.ipynb` | 1 % label experiment |

3. **Before running**:  
   * Download the files listed in **DATA_LINKS.md**  
   * Upload them to `/content/data/weights/` (or adjust paths at the top of each notebook).

 Each notebook saves its results to `/content/results/`.

## Questions?

Open an issue or email me at <ftweldem@bradford.ac.uk>.
