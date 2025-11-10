# Fine-tuning SAM 2.1 for Bubble Segmentation

This repository includes the scripts and configuration files used for fine-tuning the SAM 2.1 model on a real-world bubble segmentation dataset.  
The workflow was developed as part of the study *“Segmenting the Complex and Irregular in Two-Phase Flows: A Real-World Empirical Study with SAM2.”*

---

## Repository contents

```
├── sam2_training_bubbly.ipynb      # Main notebook containing the full fine-tuning workflow
├── train_1.yaml                    # Configuration file defining dataset paths and parameters
├── trainer.py                      # Modified SAM 2 trainer with validation loss tracking
└── README.md
```

---

## Description

The repository provides a complete pipeline for adapting the SAM 2.1 model to domain-specific data.  
All necessary steps from data loading to model evaluation are included in the Jupyter notebook.  
Running the notebook end-to-end will reproduce the results described in the paper.

---

## How to run

### 1. Environment setup
Use Python ≥3.10 with CUDA-enabled PyTorch installed.  
Install the dependencies required for SAM 2.1 following the instructions in the official repository.

---

### 2. Notebook execution
Open and run the notebook `sam2_training_bubbly.ipynb` sequentially.  
It handles:
- Loading images and masks  
- Model initialization  
- Configuration parsing from `train_1.yaml`  
- Training and validation  

---

### 3. Configuration
The file `train_1.yaml` contains dataset paths, optimizer parameters (learning rate, weight decay), and augmentation settings.  
To use your own dataset, replace the dataset directory used in our experiments (downloaded from Kaggle) with your own path, for example:

```yaml
train_data_path: "/path/to/your/dataset/train"
val_data_path: "/path/to/your/dataset/val"
```

Keep the same folder structure (`images/` and `masks/`), or update the paths accordingly.

---

### 4. Validation monitoring
To record losses during validation, the standard SAM 2 `trainer.py` script was slightly modified.  
The updated version included here logs additional validation metrics automatically while training.

---

### 5. Adapting to other datasets
Researchers who wish to fine-tune SAM 2.1 on different datasets can follow the same workflow.  
By replacing the dataset path and adjusting `train_1.yaml`, the notebook can be used without additional code changes.  
The most effective fine-tuning parameters may differ depending on image characteristics and illumination.  
Further guidance on parameter selection can be found in the accompanying paper.

---

## Citation
If this code or workflow is used in your research, please cite:

> Kucuk, S., et al. (2025). *Segmenting the Complex and Irregular in Two-Phase Flows: A Real-World Empirical Study with SAM2.*  
> International Journal of Multiphase Flow.

---

## Contact
For any questions or collaboration requests, please contact:  
**Semanur Kucuk** — [s.kuecuek@tudelft.nl / semanurkucuk7997@gmail.com]
