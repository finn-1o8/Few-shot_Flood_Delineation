# External data & weight files

| Artefact | Where to download / find | SHA-256 checksum |
|----------|-------------------------|------------------|
| **STURM dataset (images + masks) ZIP ** |https://drive.google.com/file/d/195O7aaPXF_CkIdgFrSb713dXHHYgEHPl/view?usp=sharing | large folder — skip checksum |
| **SatMAE regional pre-trained weights** (`satmae_region.pt`) |https://drive.google.com/file/d/1BsfdlUz9EBNE5ZQ-MiaNEtfztnDSWj3h/view?usp=sharing | `<TODO>` |
| **SatMAE fine-tuned checkpoint (10 % labels)** (`satmae_10pct.ckpt`) | https://drive.google.com/file/d/1Tm94-MU-Jors9sMSpSebxfra8S15QxWL/view?usp=sharing | `<TODO>` |
| **UNET checkpoint (10 % labels)** (`unet_10pct.ckpt`) |https://drive.google.com/file/d/1Mqn62TXUHB_t9_jyKo65XTpNbjjlKMpx/view?usp=sharing   | `<TODO>` |
| **SatMAE fine-tuned checkpoint (1 % labels)** (`satmae_1pct.ckpt`) |https://drive.google.com/file/d/1GcVzhdzVJbKqHiaoM9fsCnITIAYcO7qD/view?usp=sharing | `<TODO>` |
| **UNET checkpoint (1 % labels)** (`unet_1pct.ckpt`) | https://drive.google.com/file/d/1fXrzx5jhxJsjHrkYcuFyyFnaOyFSVudp/view?usp=sharing| `<TODO>` |
| **SatMAE fine-tuned checkpoint (0.5 % labels)** (`satmae_0.5pct.ckpt`) |https://drive.google.com/file/d/1NP7CDfZGIPYvza-_tQtcXKNd8JQuByeW/view?usp=sharing | `<TODO>` |
| **UNET checkpoint (0.5 % labels)** (`unet_0.5pct.ckpt`) | https://drive.google.com/file/d/1Dbb8pDdDNTgzs3Tuk3nQSspkeWTKCVAb/view?usp=sharing| `<TODO>` |
| **Sen1Flood Sealed Test UNET (0.5 %)** (`test2unet_0.5pct.ckpt`) | https://drive.google.com/file/d/1oKX9_8SDM7UQDsqhbczcfP3QPgGHXmlI/view?usp=drive_link| `<TODO>` |
| **Sen1Flood Sealed Test UNET (0.11 %)** (`test2unet_0.11pct.ckpt`) |https://drive.google.com/file/d/1cByBEf4iCd46XNB6kLg8VZpBgrnvhkXq/view?usp=sharing | `<TODO>` |
| **Sen1Flood Sealed Test SatMAE (0.5 %)** (`test2satmae_0.5pct.ckpt`) |https://drive.google.com/file/d/1L5GhADtRUY91XZy-HDSsAwepGXYDd1gd/view?usp=drive_link| `<TODO>` |
| **Sen1Flood Sealed Test SatMAE (0.11 %)** (`test2satmae_0.11pct.ckpt`) |https://drive.google.com/file/d/1CcuA-UErS4PS94UsRIo8daJnDmDEuZiU/view?usp=sharing| `<TODO>` |


| **Sentinel-2 manifest for pre-training** (`s2_prefixes.txt`) | *(this repo)* | see git blob |

**How to use**

1. Click each Drive link and download the file(s).  
2. In Colab, place the files in `/content/data/weights/` (or the folder each notebook expects) **before** running the notebooks.
