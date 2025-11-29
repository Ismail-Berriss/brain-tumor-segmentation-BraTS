# BraTS-2020 — 3D U-Net Brain Tumor Segmentation (MONAI + TorchIO)

End-to-end 3D brain tumor segmentation pipeline using the BraTS-2020 dataset, a 3D U-Net model, and the MONAI / TorchIO ecosystem.  
The project includes data preprocessing, patch-based training, evaluation, uncertainty estimation (MC Dropout), and NIfTI export.

---

## Project Structure

.
├── BraTS2020_3DUNet.ipynb # Main Jupyter Notebook (full pipeline)  
├── README.md # Project documentation  
├── checkpoint/ # Saved model weights (created at runtime)  
│ └── best_model.pth  
├── output/ # Predictions, plots, metrics (created at runtime)  
│ ├── training_metrics.csv  
│ └── training_history.png  
├── dataset/  
│ ├── MICCAI_BraTS2020_TrainingData/  
│ │ ├── BraTS20_Training_001/  
│ │ │ ├── BraTS20_Training_001_flair.nii  
│ │ │ ├── BraTS20_Training_001_seg.nii  
│ │ │ ├── BraTS20_Training_001_t1.nii  
│ │ │ ├── BraTS20_Training_001_t1ce.nii  
│ │ │ ├── BraTS20_Training_001_t2.nii  
│ ├── BraTS20_Training_002/  
│ └── ...  

You can adjust folder names as needed, but the notebook assumes `checkpoints/` and `outputs/` exist or can be created.

---

## Features

-   3D U-Net architecture implemented with MONAI (4 input modalities, 4 output classes).
-   Multi-modal MRI input: T1, T1ce, T2, FLAIR.
-   Patch-based 3D training for memory efficiency.
-   Z-score intensity normalization with brain masking.
-   Data augmentation (flips, rotations, intensity changes, etc.).
-   Training/validation split with configurable quick-debug mode.
-   Dice + Cross-Entropy loss (DiceCELoss) and region-wise Dice metrics:
    -   Whole Tumor (WT)
    -   Tumor Core (TC)
    -   Enhancing Tumor (ET)
-   Sliding-window 3D inference with overlap.
-   Post-processing via connected-component removal.
-   Monte Carlo Dropout for voxel-wise uncertainty estimation.
-   Visualization of predictions and uncertainty maps.
-   Metrics CSV, plots, and NIfTI predictions exported for further analysis.

---

## How to Run

All instruction are in the notebook
