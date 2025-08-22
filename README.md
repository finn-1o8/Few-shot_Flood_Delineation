# Label-Efficient Self-Supervised Pretraining for Few-Shot Flood Delineation from Sentinel-2 Optical Imagery 🌊🛰️"

This repository contains the **notebooks, model weights, and data manifests** for my MSc thesis on label-efficient flood mapping from Sentinel-2 optical imagery. The central idea:  
**Pretrain once on unlabeled, flood-prone Sentinel-2 regions → adapt with only a handful of labels.**

> **Headline results (STURM-Flood, optical, event-wise validation):**  
> • **10% labels:** U-Net slightly leads (F1 = 0.774 vs. 0.714 for SatMAE+ASPP).  
> • **1% labels:** SatMAE+Hybrid wins (F1 = 0.751 vs. 0.692 for U-Net).  
> • **0.5% labels (12 tiles):** U-Net collapses (0.309) while SatMAE+Hybrid sustains 0.752 (+143% rel. gain).  
> • **Sealed external test (Sen1Floods11 optical subset):** U-Net slightly leads at 36 tiles (0.5%), but **SatMAE decisively wins at 8 tiles (0.11%)**, confirming robustness under domain shift.

---

## How to reproduce the results

1. **Open Google Colab** → **File ▸ Open notebook ▸ GitHub** → paste this repo URL.
2. Run the notebooks in order:

The notebooks are numbered to be run sequentially. It is recommended to open them in Google Colab for a seamless experience with pre-configured environments.

| Notebook                                        | Purpose                                                                          | Key Outcome                               |
| ----------------------------------------------- | -------------------------------------------------------------------------------- | ----------------------------------------- |
| **STURMrecreated.ipynb**          | Reproduces the supervised U-Net baseline on the full STURM-Flood dataset.        | Validates the experimental setup.         |
| **Large_Unlabeled_Pretraining.ipynb**         | Curates the 11,997-scene unlabeled corpus and pre-trains the SatMAE encoder.     | Produces `mae9_epoch20.ckpt`.             |
| **Fine-Tuning_on_10_percent_labeled.ipynb**               | Fine-tunes and compares SatMAE vs. U-Net on a 10% labeled data split.            | Shows U-Net's advantage with moderate data. |
| **SatMAE_vs_Unet_one_percent.ipynb**                | Compares models on a 1% labeled data split (severe scarcity).                    | Demonstrates the performance inversion.     |
| **SatMAE_vs_Unet_0_5_percent.ipynb**      | Pushes models to the limit on a 0.5% split (12 images) in a true "few-shot" test. | Confirms SatMAE's profound resilience.      |
| **Sealed_Test_Sen1Floods11.ipynb** | Cross-dataset sealed test on the Sen1Floods11 **optical** subset. Compares zero-shot vs few-shot (36 & 8 tiles) adaptation for U‑Net (from scratch) vs SatMAE‑Hybrid (frozen encoder). | Confirms the low‑label “tipping‑point” advantage under domain shift. |


**To run in Colab:**
1.  Navigate to [Google Colab](https://colab.research.google.com/).
2.  Click **File ▸ Upload notebook...** and select a notebook from the cloned repository.
3.  Ensure the runtime is set to use a **GPU accelerator** (`Runtime > Change runtime type`).
4.  Run the cells in order. The notebooks will automatically mount your Google Drive to access data and save results.

---

## Sealed External Test (Sen1Floods11, optical-only)

**Why this matters.** Beyond STURM, we run a *sealed* cross‑dataset test on the **optical subset** of Sen1Floods11 to check robustness under domain shift. Zero‑shot fails (as expected), but with just a few labeled tiles the SatMAE‑initialized model takes the lead in the extreme few‑shot regime.

**Setup (mirrors the thesis):**
- Dataset: Sen1Floods11 **optical** subset (hand‑labeled S2 chips).  
- Tiling & filter: chips → 128×128 tiles; keep tiles with **1–95%** water coverage.  
- Few‑shot budgets: **36 tiles (≈0.5%)** and **8 tiles (≈0.11%)** for training.  
- Normalization: **reflectance-only** (divide S2 L2A by 10 000). *Do not* apply STURM z‑scores to this dataset.  
- Threshold: fixed at **0.5** for all metrics.  
- Models: 
  - **U‑Net (from scratch)** — 9‑band S2.
  - **SatMAE‑Hybrid** — frozen SatMAE encoder + lightweight U‑Net‑style decoder.

**Results (F1/Dice; IoU derived via IoU = F1/(2−F1)):**

| Setup | F1 (Dice) | IoU | Note |
| --- | ---: | ---: | --- |
| Zero‑shot (STURM‑tuned model) | **0.0100** | 0.0050 | Domain shift ⇒ essentially non‑functional without adaptation. |
| 36 tiles (≈0.5%), U‑Net | **0.8424** | 0.7278 | Slight edge to U‑Net when labels are modest. |
| 36 tiles (≈0.5%), SatMAE‑Hybrid | **0.8290** | 0.7085 | Close second. |
| 8 tiles (≈0.11%), U‑Net | **0.4873** | 0.3222 | From‑scratch begins to collapse. |
| 8 tiles (≈0.11%), SatMAE‑Hybrid | **0.6060** | 0.4346 | **Decisive win** in the true few‑shot setting. |

**How to run it (Colab-friendly):**
1. Download the optical subset (see `DATA_LINKS.md`) and place tiles under, e.g., `/content/data/sen1floods11_optical/`.
2. Open **`Sealed_Test_Sen1Floods11.ipynb`** in Colab.
3. Ensure `NORMALIZATION = "reflectance_only"` in the config cell.
4. Choose a budget (`n_train_tiles = 36` or `8`) and run. The notebook will train:
   - U‑Net (from scratch) and
   - SatMAE‑Hybrid (encoder frozen),
   then report F1/IoU at a fixed 0.5 threshold.

*Scope note:* This sealed test is **optical‑only** to match the project’s scope; SAR or S1+S2 fusion is out of scope for this repo.


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
