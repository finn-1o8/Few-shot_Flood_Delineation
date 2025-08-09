# External data & weight files

| Artefact | Where to download / find | SHA-256 checksum |
|----------|-------------------------|------------------|
| **STURM dataset (images + masks) ZIP ** |https://drive.google.com/file/d/195O7aaPXF_CkIdgFrSb713dXHHYgEHPl/view?usp=sharing | large folder — skip checksum |
| **SatMAE regional pre-trained weights** (`satmae_region.pt`) |https://drive.google.com/file/d/1BsfdlUz9EBNE5ZQ-MiaNEtfztnDSWj3h/view?usp=sharing | `<TODO>` |
| **SatMAE fine-tuned checkpoint (10 % labels)** (`satmae_10pct.ckpt`) | https://drive.google.com/file/d/1Tm94-MU-Jors9sMSpSebxfra8S15QxWL/view?usp=sharing | `<TODO>` |
| **UNET checkpoint (10 % labels)** (`satmae_10pct.ckpt`) |https://drive.google.com/file/d/1Mqn62TXUHB_t9_jyKo65XTpNbjjlKMpx/view?usp=sharing   | `<TODO>` |
| **SatMAE fine-tuned checkpoint (1 % labels)** (`satmae_1pct.ckpt`) |https://drive.google.com/file/d/1GcVzhdzVJbKqHiaoM9fsCnITIAYcO7qD/view?usp=sharing | `<TODO>` |
| **UNET checkpoint (1 % labels)** (`satmae_1pct.ckpt`) | https://drive.google.com/file/d/1fXrzx5jhxJsjHrkYcuFyyFnaOyFSVudp/view?usp=sharing| `<TODO>` |
| **SatMAE fine-tuned checkpoint (0.5 % labels)** (`satmae_1pct.ckpt`) |https://drive.google.com/file/d/1NP7CDfZGIPYvza-_tQtcXKNd8JQuByeW/view?usp=sharing | `<TODO>` |
| **UNET checkpoint (0.5 % labels)** (`satmae_1pct.ckpt`) | https://drive.google.com/file/d/1Dbb8pDdDNTgzs3Tuk3nQSspkeWTKCVAb/view?usp=sharing| `<TODO>` |

| **Sentinel-2 manifest for pre-training** (`s2_prefixes.txt`) | *(this repo)* | see git blob |

**How to use**

1. Click each Drive link and download the file(s).  
2. In Colab, place the files in `/content/data/weights/` (or the folder each notebook expects) **before** running the notebooks.
