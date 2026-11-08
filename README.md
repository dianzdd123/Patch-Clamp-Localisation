# Patch-Clamp-Localisation

**MSEI Lab:** [Website](https://zhangrobotics.com/msei_website/) · [Website on GitHub](https://github.com/dianzdd123/msei_website)

## Start here

**Repository:** [dianzdd123/Patch-Clamp-Localisation](https://github.com/dianzdd123/Patch-Clamp-Localisation)

This repository is a fork of [LannWei/Patch-Clamp-Localisation](https://github.com/LannWei/Patch-Clamp-Localisation). Original authorship, citations and upstream notices are retained. Changes here apply to this fork.

**Scope:** Partial research release; required model and preprocessing modules are absent from this checkout.

| Need | Where to start |
|---|---|
| Setup, file map, inputs/outputs and troubleshooting | [Reuse guide](docs/REUSE.md) |
| Local structural validation | `python scripts/check_repository.py` (Python 3.10+) |
| Proposed fixes and reproducibility details | [Contributing](CONTRIBUTING.md) |

The structural check does not run experiments or certify hardware, model accuracy or dependency compatibility. Reuse permissions need clarification: this checkout has no repository-wide licence file.

The Official Implementation of In Vivo Patch Clamp Multi-Pipette Localisation

Developers: Lan Wei

# This code is the implementation of:
[Heatmap-Augmented Coarse-to-Fine Learning for Automatic In Vivo Patch Clamp Multi-Pipette Real-time Localisation]

Authors: Lan Wei, Gema Vera Gonzalez, Phatsimo Kgwarae, Alexander Timms, Denis Zahorovsky, Simon Schultz, and Dandan Zhang

## Usage

First, install PyTorch == 1.9.1+cu111\\
torchvision == 0.10.1+cu111 \\
tensorboardx == 2.4\\
tensorboard_logger == 0.1.0:
```
pip install torch==1.9.1+cu111 torchvision==0.10.1+cu111 -f https://download.pytorch.org/whl/torch_stable.html
python -m pip install tensorboardx==2.4
python -m pip install tensorboard_logger==0.1.0
```

# Model training

This command requires the missing model/preprocessing modules and external data described in the [reuse guide](docs/REUSE.md).
```
cd Code
python Lan_model_co2fi_inference_train.py --gan_enhance 1 --eu_dist 3 --heatmap_sigma 10 --n_epochs 200
```

