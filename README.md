# Acoustic-Scene-Clasification
### Local folder setup (required before running)

The dataset is **not included** in this repository and must be downloaded separately (see [Dataset Preparation](#dataset-preparation)). Once downloaded, create the following folder structure **locally** on your machine:

```
your_project_folder/
│
├── no_augmentation/
│   ├── scenes_stereo/             <- training set (100 .wav files)
│   │   ├── bus01.wav
│   │   ├── ...
│   │   └── tubestation10.wav
│   ├── scenes_stereo_testset/     <- test set (100 .wav files)
│   │   ├── bus01.wav
│   │   ├── ...
│   │   └── tubestation10.wav
│   ├── Block1_Setup.ipynb
│   ├── Block2_Features.ipynb
│   ├── Block3_Baseline.ipynb
│   ├── Block4_CNN.ipynb
│   └── Block5_ErrorAnalysis.ipynb
│
└── augmentation/
    ├── scenes_stereo/             <- same training set (100 .wav files)
    │   ├── bus01.wav
    │   ├── ...
    │   └── tubestation10.wav
    ├── scenes_stereo_testset/     <- same test set (100 .wav files)
    │   ├── bus01.wav
    │   ├── ...
    │   └── tubestation10.wav
    ├── Block1_Setup_Augmented.ipynb
    ├── Block2_Features_Augmented.ipynb
    ├── Block3_Baseline_Augmented.ipynb
    ├── Block4_CNN_Augmented.ipynb
    └── Block5_ErrorAnalysis_Augmented.ipynb
```


Each pipeline generates its own output folder automatically when the notebooks are run:
- `no_augmentation/output_block1/` — features, models and figures (baseline pipeline)
- `augmentation/output_block2/` — features, models and figures (augmented pipeline)

---

## Software Requirements
Python 3.11.1 or higher is recommended. The notebooks were developed and tested on **Windows 11** with a local Python environment.

### Dependencies

Install each block's dependencies individually — each notebook contains a self-contained install cell at the top:

```python
import sys
!{sys.executable} -m pip install librosa==0.11.0 soundfile numpy pandas matplotlib seaborn scikit-learn tqdm tensorflow --quiet
```
# Dataset Preparation

### 1. Download the dataset

Request access and download the DCASE 2013 Task 1 corpus from the official page:  
https://dcase.community/challenge2013/task-acoustic-scene-classification

The dataset contains:
- **Training set:** 100 WAV files (10 classes × 10 recordings each)
- **Test set:** 100 WAV files (10 classes × 10 recordings each)

## Known Issues

- **Path separators:** paths use Windows-style backslashes (`r"C:\..."`) — on Linux/Mac replace with forward slashes or use `os.path.join()`
- **TensorFlow on Apple Silicon:** replace `tensorflow` with `tensorflow-macos` and `tensorflow-metal` if running on an M-series Mac
