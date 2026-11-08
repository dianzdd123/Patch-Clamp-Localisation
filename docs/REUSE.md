# Reusing Patch-Clamp-Localisation

Coarse-to-fine multi-pipette localisation.

**Current scope:** Partial research release; required model and preprocessing modules are absent from this checkout.

This repository is a fork of [LannWei/Patch-Clamp-Localisation](https://github.com/LannWei/Patch-Clamp-Localisation). Original authorship, citations and upstream notices are retained. Changes here apply to this fork.

## Included implementation

| Path | Purpose |
|---|---|
| `Code/Lan_model_baseline.py` | Baseline neural-network definitions |
| `Code/Lan_model_co2fi_inference_train.py` | Heatmap training/evaluation experiment |
| `index.html`, `resource/` | Project page and figures |
| `Data` | Data reference file; not a populated training-data directory |

## Verify the checkout

```bash
python scripts/check_repository.py
```

The indentation defect in the training loop is fixed, and training mode is restored at the start of each epoch after validation. This allows the source to parse; it does not make the incomplete release runnable.

## Missing prerequisites

The training script imports `Lan_model_co2fi_inference` (including `ViTHeatmapKeypointModel`, `ViTHeatmapModel` and `UNet`) and the `Alex_pipette_tracking.micropipette_tracker.preprocessing` package. These are not present. Obtain the matching implementation from the project authors before attempting training; substituting the baseline file is not equivalent.

It also expects microscopy image directories and Excel coordinate annotations listed near the top of the script. The public snapshot does not supply those complete inputs. Confirm annotation conventions, maximum keypoint count, image resolution and split membership before preparing your own data.

The original environment notes mention PyTorch 1.9.1 / torchvision 0.10.1 with CUDA 11.1. Additional imports include OpenCV, Pillow, NumPy, albumentations, matplotlib, scipy, scikit-image, scikit-learn, transformers, timm and TensorBoard. These notes are historical, not a tested full environment specification.

## Training entry point after prerequisites are restored

```bash
cd Code
python Lan_model_co2fi_inference_train.py --gan_enhance 1 --eu_dist 3 --heatmap_sigma 10 --n_epochs 200
```

The old `Lan_model_train.py` command referred to a file that is not included; `--change_epoch_1` and `--change_epoch_2` are not parser options in the supplied training script. Outputs go under `logs_new/<experiment>/` (models, images and TensorBoard logs).

## Reproduction record

Preserve microscope/session IDs, annotation provenance, train/validation/test assignment, augmentation settings and checkpoint identity. Verify keypoint-level metrics and empty-keypoint handling on representative annotated examples. No full training, inference accuracy or real-time performance claim follows from the structural check.

## Attribution and reuse permissions

No repository-wide licence file is included in this checkout. Confirm reuse and redistribution permissions with the relevant rights holders; this maintenance update does not add a licence or relicense upstream code, data or assets.

## Contributing

See [CONTRIBUTING.md](../CONTRIBUTING.md) for the local workflow and what to include with a proposed change.
