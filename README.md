# Visual-Polarization-Measurement-Using-Counterfactual-Image-Generation
This paper, we introduce the Polarization Measurement Using Counterfactual Image Generation (PMCIG) method, which combines economic theory with generative models and multi-modal deep learning to fully utilize the richness of image data and provide a theoretically grounded measure of polarization in visual content. (Link to the Paper: https://arxiv.org/pdf/2503.10738)

---------------------------------------------------------------------------------
This repository contains data, models, and code for analyzing political news images and text using multimodal machine learning.  
It combines scraped metadata, politician images, and counterfactuals to study polarization, prediction, and interpretability.

------------------------------------------------
📂 Data Setup
------------------------------------------------

This project relies on a collection of datasets, trained model checkpoints, and counterfactual image sets that together support full replication of the paper’s empirical results. Below, we describe each file, its role in the pipeline, and how all components align.

### Core Data and Model Files

- **`cleaned_data.csv`**  
  Contains the full set of metadata scraped from news articles. This is the foundational dataset and includes article-level information, image URLs, and unique identifiers used to link metadata to images.

- **`images_Polarization.zip`**  
  Archive of politician images corresponding to observations in `cleaned_data.csv`. Each image represents the visual input analyzed by the multimodal model.

- **`Final_CSV_For_Analysis.csv`**  
  Final analysis dataset used to generate the main empirical results in the paper. It contains model-predicted outlet probabilities, counterfactual predictions, and all derived variables required for replication.

- **`Final_CSV_For_Analysis_Model_1.csv`**  
  Identical in structure to `Final_CSV_For_Analysis.csv`, but generated using **cross-fitting model 1**, trained on one half of the training data.

- **`Final_CSV_For_Analysis_Model_2.csv`**  
  Identical in structure to `Final_CSV_For_Analysis.csv`, but generated using **cross-fitting model 2**, trained on the complementary half of the training data.

- **`ML_Model.pth`**  
  Trained multimodal outlet-prediction model weights estimated using the full training dataset.

- **`ML_Model_1.pth`**  
  Trained multimodal model weights obtained by training on the first half of the training data (used for cross-fitting).

- **`ML_Model_2.pth`**  
  Trained multimodal model weights obtained by training on the second half of the training data (used for cross-fitting).

- **`Counterfactuals.zip`**  
  Archive containing generated counterfactual image sets (e.g., smile vs. no-smile) used to implement the PMCIG counterfactual estimation procedure.

---

### Image–Metadata Alignment

Each image in `images_Polarization.zip` is named using a numeric identifier (e.g., `0.jpg`, `2.jpg`).  
These identifiers **exactly match** the `ID` column in `cleaned_data.csv`, ensuring a one-to-one correspondence between metadata and image files throughout the pipeline.

---

### `cleaned_data.csv`: Column Description

Key columns in `cleaned_data.csv` include:

- **`Unnamed: 0`** → index carried over from the original scraping process  
- **`image`** → URL of the associated image  
- **`alt`** → HTML alt-text description of the image  
- **`href`** → hyperlink to the news article  
- **`title`** → article title  
- **`0`** → original search query string used during scraping  
- **`ID`** → numeric identifier matching image filenames in `images_Polarization.zip`

**Example rows:**
- `ID = 0` → *Bird Strike Cripples Joe Biden Plane in California – ABC News*  
- `ID = 2` → *At West Point Commencement, Joe Biden Focuses on Future Challenges – ABC News*

---

### `Final_CSV_For_Analysis.csv`

- Contains counterfactual predictions and all features required for replication and downstream analysis.
- Predictions are generated using the trained multimodal model (`ML_Model.pth`), or `ML_Model_1.pth` / `ML_Model_2.pth` in the cross-fitting setup.
- Counterfactual images are generated using https://www.ailabtools.com/ and stored in `Counterfactuals.zip`.

**Note:**  
An in-house counterfactual image generation pipeline is also provided at  
https://github.com/mmosaffa/SmileGAN-PTI.

---

### Trained Model Checkpoints

- **`ML_Model.pth`**  
  Contains trained multimodal model weights produced using the training pipeline in `Git_Multimodal_ML_Code.ipynb`. This model is used to generate predictions and interpretability analyses in the main results.

- **`ML_Model_1.pth` and `ML_Model_2.pth`**  
  Contain trained multimodal model weights produced using the training pipeline in `Git_Cross_Fitting.ipynb`. These models are used for cross-fitted prediction, validation, and the construction of Overall Visual Polarization (OVP).

---

### `Counterfactuals.zip`

- Contains multiple sets of generated counterfactual images:
  - smiling and non-smiling versions of politicians (primary analysis),
  - additional visual feature manipulations such as **brightness** and **frown (sadness)**.
- Counterfactuals are generated externally using https://www.ailabtools.com/.
- These images are used in `Git_Multimodal_Code.ipynb` and `Git_Supplementary_Results.ipynb` for counterfactual prediction and robustness checks.

------------------------------------------------
⚙️ Download Options
------------------------------------------------
You can set up the required data and model files using either an **automatic download script** (recommended) or **manual downloads**. Both options result in the same directory structure expected by the notebooks.

Option 1: Automatic Download (Recommended)

pip install requests
python Initial/setup_data.py

 This downloads:
 - cleaned_data.csv
 - images.zip (unzipped into data/images/)

Option 2: Manual Download

Download files from Google Drive:
- Images ZIP → https://drive.google.com/file/d/1yv6A7IgkxR7cqQ7pKyDC5VUtlzuZJo9v/view?usp=sharing
- Cleaned CSV → https://drive.google.com/file/d/1VLKIx58fEqJZ3ButMooVtRBa9_8CZdSl/view?usp=sharing
- Final CSV (Final_CSV_For_Analysis.csv) → https://drive.google.com/file/d/1Y--w5iLYjI2ir1Vk-tblAwB4Flf9o59T/view?usp=sharing
- Final Cross-Fitting CSV 1 (Final_CSV_For_Analysis_Model_1.csv) → https://drive.google.com/file/d/1_wBsNgZyhMGpOk3YvsSM0VboLPJ5T5Jb/view?usp=sharing
- Final Cross-Fitting CSV 2 (Final_CSV_For_Analysis_Model_2.csv) → https://drive.google.com/file/d/14PQLtSrYivyQpIpYR1buf4q3a2BIQBkF/view?usp=sharing
- Trained Main Model (ML_Model.pth) → https://drive.google.com/file/d/1UOsbrBunqAj5gDuM7YSelwXvczCboV_o/view?usp=sharing
- Trained Cross-Fitting Model 1 (ML_Model_1.pth) → https://drive.google.com/file/d/1BjF7JdipSaAB7J41K3hQbP6EjjhJK3BQ/view?usp=sharing
- Trained Cross-Fitting Model 2 (ML_Model_2.pth) → https://drive.google.com/file/d/1aX116VhPCiuda9R8x_Hu-lsimTkH74pF/view?usp=sharing
- Counterfactuals → https://drive.google.com/file/d/1Xv0xB231wOVY-sQ7yRD_aj5j7NmC2Ziu/view?usp=sharing

mkdir data

Place the files as:

data/

 ├── cleaned_data.csv
 
 ├── images.zip
 
 ├── Final_CSV_For_Analysis.csv
 
 ├── ML_Model.pth
 
 └── Counterfactuals.zip

Unzip images.zip and Counterfactuals.zip so the folder looks like:

data/

 ├── cleaned_data.csv
 
 ├── Final_CSV_For_Analysis.csv
 
 ├── ML_Model.pth
 
 ├── images/
 
 │    ├── 0.jpg
 
 │    ├── 2.jpg
 
 │    └── ...
 
 └── Counterfactuals/
 
      ├── no_smile_set/
      
      └── smile_set/
      └── brightness_set/
      └── frown_set/

✅ Once set up, notebooks (Git_Data_Cleaning.ipynb, Git_ML_Code.ipynb, Git_Results.ipynb) will load the correct datasets and models.

------------------------------------------------
📓 Notebooks Overview
------------------------------------------------

### Repository Structure and Notebooks

This repository is organized as a sequence of Jupyter notebooks that together implement the full empirical pipeline of the paper—from data collection and preprocessing to model training, counterfactual analysis, and validation. Each notebook corresponds to a distinct stage of the analysis and can be run independently once the required inputs are available.

- **`Scraping.ipynb`**  
  Scrapes raw politician images and article-level metadata from major news sources. This notebook constructs the initial dataset by collecting image URLs, article titles, hyperlinks, alt-text, and associated search queries, and assigns a unique numeric `ID` to each observation. The resulting output serves as the starting point for all subsequent cleaning and analysis.

- **`Git_Data_Cleaning.ipynb`**  
  Processes the scraped data by cleaning metadata, verifying faces in images, and filtering out low-quality or invalid observations. This notebook also constructs additional structured features, including LDA-based topic distributions derived from article text, which are later used as inputs to the multimodal model.

- **`Git_Multimodal_Code.ipynb`**  
  Trains and evaluates the multimodal outlet-prediction model that combines visual features, facial embeddings, textual topic features, and metadata. This notebook generates predicted outlet probabilities for both observed and counterfactual images and implements interpretability analyses such as Grad-CAM visualizations and t-SNE embeddings to understand how the model uses visual information.

- **`Git_Main_Empirical_Results.ipynb`**  
  Replicates the main empirical results reported in the paper using `Final_CSV_For_Analysis.csv`, which is constructed from predictions produced by the trained model checkpoint (`ML_Model.pth`). This notebook computes key measures such as Conservative Visual Slant (CVS) and Overall Visual Polarization (OVP), produces the main figures and tables, and implements cross-fitting procedures for estimating OVP using independently trained models.

- **`Git_Cross_Fitting.ipynb`**  
  Implements the cross-fitting pipeline used to estimate OVP. The notebook trains two separate models on disjoint halves of the training data, evaluates their predictive performance, and saves the resulting model checkpoints (`ML_Model_1.pth`, `ML_Model_2.pth`) and prediction outputs. These models are later combined to construct cross-fitted polarization measures.

- **`Git_Supplementary_Results.ipynb`**  
  Contains supplementary and robustness analyses that extend beyond the main results. This includes assessments of alternative visual features (e.g., brightness and frown/sadness), additional counterfactual experiments, and an end-to-end reduced-form approach to measuring visual polarization, along with external validation against established non-visual media ideology benchmarks.
  
------------------------------------------------
🛠 Requirements
------------------------------------------------

### System Requirements

To ensure full reproducibility of the results, we recommend the following system configuration:

- **Python**: 3.9 or 3.10 (tested and recommended)
- **Operating System**:  
  - Linux (Ubuntu 20.04 or later)  
  - macOS  
  - Windows 10/11
- **Hardware**:  
  - NVIDIA GPU with CUDA support is strongly recommended for training and large-scale inference  
  - CPU-only execution is possible for analysis notebooks using precomputed outputs
- **CUDA**:  
  - CUDA 11.7 or later (required if training or running models on GPU)

---

### Python Dependencies

Install the required Python packages using the versions below to match the environment used in the paper:

```bash
pip install torch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 \
  --extra-index-url https://download.pytorch.org/whl/cu117

pip install scikit-learn==1.3.0
pip install pandas==2.0.3
pip install matplotlib==3.7.1 seaborn==0.12.2
pip install tqdm==4.65.0
pip install requests==2.31.0
pip install nltk==3.8.1
pip install gensim==4.3.2
pip install facenet-pytorch==2.5.2
pip install opencv-python==4.8.0.74
pip install pillow==10.0.0
pip install torch_optimizer==0.3.0
