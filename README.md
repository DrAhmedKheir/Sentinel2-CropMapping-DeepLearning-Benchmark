# Sentinel-2 crop/non-crop mapping benchmark

Research code associated with a manuscript comparing DINOv2, 3D UNet++, TemporalViT, and UNet–ConvLSTM for binary crop/non-crop segmentation using multitemporal Sentinel-2 imagery.

## Status and limitations
This is a cleaned version of the authors' supplied research notebook, **not an independently validated reproduction package**. No trained weights, datasets, or original evaluation output files are included. Please check that the notebook corresponds exactly to the reported experiments before making reproducibility claims.

## Data
Public dataset: https://www.kaggle.com/datasets/ignazio/sentinel2-crop-mapping
Record the dataset version, date accessed, source licence, region/year/tile identifiers and the exact train/validation/test split before publication. Do not commit third-party imagery without permission.

## Setup
Use a Python environment with compatible PyTorch/CUDA versions. Install dependencies with `pip install -r requirements.txt`. The original notebook assumes Kaggle path `/kaggle/input/sentinel2-crop-mapping`; update `DATA_ROOT` for your environment. Run notebook cells sequentially, reviewing each model configuration first. Some evaluation cells require previously generated checkpoints or metric files.

## Model implementations
- DINOv2 baseline and evaluation
- 3D UNet++ and evaluation
- TemporalViT variants and evaluation
- UNet–ConvLSTM and evaluation
- Aggregate comparison plots

## Critical manuscript consistency checks
1. **Loss functions differ by default:** 3D UNet++ has `USE_FOCAL=True`, while TemporalViT and UNet–ConvLSTM have `USE_FOCAL=False`; DINOv2 uses cross-entropy. Do not claim identical loss functions unless the reported runs used identical configurations.
2. Batch sizes differ (8, 4, 8, 6 respectively); document optimizer and training-budget differences and avoid attributing all performance differences exclusively to architecture.
3. DINOv2 is a spatial pretrained baseline while other models use temporal sequences. Clarify this limitation.
4. Verify whether splitting is independent by geography, tile ID and year, and retain split manifests.
5. The supplied notebook has no saved cell outputs; published numerical results have not been independently verified.
6. Check whether the manuscript's three random seeds were actually run for each model and provide seed-level results.
7. Include exact package versions, hardware, checkpoint selection, and evaluation protocol before archival release.

## Citation
Add the final manuscript citation and a permanent release DOI when available.

## License
No license has been assigned. Confirm all co-authors' permission and choose a license before inviting reuse.
