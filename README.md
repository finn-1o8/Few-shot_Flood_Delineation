# MSc Flood Mapping Thesis  🌊🛰️

This repository contains **all notebooks, models, and data links** for my MSc thesis:

> *“Region-Aligned Self-Supervised Pre-Training for Few-Shot Flood Delineation.”*

## How to reproduce the results

1. **Open Google Colab** → **File ▸ Open notebook ▸ GitHub** → paste this repo URL.
2. Run the notebooks in order:

| Notebook | 
|---|---|
| `STURMrecreated.ipynb` | 
| `Large_Unlabeled_Pretraining.ipynb` | 
| `Fine-Tuning_on_10_percent_labeled.ipynb` |
| `SatMAE_vs_Unet_one_percent.ipynb` |
| `SatMAE_vs_Unet_0_5_percent.ipynb` | 

The notebooks are numbered to be run sequentially. It is recommended to open them in Google Colab for a seamless experience with pre-configured environments.

| Notebook                                        | Purpose                                                                          | Key Outcome                               |
| ----------------------------------------------- | -------------------------------------------------------------------------------- | ----------------------------------------- |
| **1_STURM_Baseline_Replication.ipynb**          | Reproduces the supervised U-Net baseline on the full STURM-Flood dataset.        | Validates the experimental setup.         |
| **2_Large_Unlabeled_Pretraining.ipynb**         | Curates the 11,997-scene unlabeled corpus and pre-trains the SatMAE encoder.     | Produces `mae9_epoch20.ckpt`.             |
| **3_Finetuning_10_Percent.ipynb**               | Fine-tunes and compares SatMAE vs. U-Net on a 10% labeled data split.            | Shows U-Net's advantage with moderate data. |
| **4_Finetuning_1_Percent.ipynb**                | Compares models on a 1% labeled data split (severe scarcity).                    | Demonstrates the performance inversion.     |
| **5_Finetuning_0.5_Percent_FewShot.ipynb**      | Pushes models to the limit on a 0.5% split (12 images) in a true "few-shot" test. | Confirms SatMAE's profound resilience.      |

**To run in Colab:**
1.  Navigate to [Google Colab](https://colab.research.google.com/).
2.  Click **File ▸ Upload notebook...** and select a notebook from the cloned repository.
3.  Ensure the runtime is set to use a **GPU accelerator** (`Runtime > Change runtime type`).
4.  Run the cells in order. The notebooks will automatically mount your Google Drive to access data and save results.

---

## Key Dependencies

The notebooks handle their own environment setup using `pip` to install version-pinned libraries. The key dependencies are:
-   `torch==2.1.2`
-   `pytorch-lightning==2.2.4`
-   `timm==0.9.16`
-   `rasterio`
-   `geopandas`
-   `pystac-client`

This ensures full reproducibility of the computational environment.

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
