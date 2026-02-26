# Visual-Polarization-Measurement-Using-Counterfactual-Image-Generation
This paper, we introduce the Polarization Measurement Using Counterfactual Image Generation (PMCIG) method, which combines economic theory with generative models and multi-modal deep learning to fully utilize the richness of image data and provide a theoretically grounded measure of polarization in visual content. (Link to the Paper: https://arxiv.org/pdf/2503.10738)

---------------------------------------------------------------------------------
This repository contains data, models, and code for analyzing political news images and text using multimodal machine learning.  
It combines scraped metadata, politician images, and counterfactuals to study polarization, prediction, and interpretability.

------------------------------------------------
📂 Data Setup
------------------------------------------------

This project uses several files:
- cleaned_data.csv → metadata scraped from news articles contains full data
- images_Polarization.zip → corresponding politician images in cleaned_data.csv
- Final_CSV_For_Analysis.csv → final dataset containing model predictions and counterfactual outputs
- ML_Model.pth → trained multimodal model weights
- ML_Model_1.pth → trained multimodal model weights on half of the train data
- ML_Model_2.pth → trained multimodal model weights on the other half of the train data
- Counterfactuals.zip → generated counterfactual image sets (smile / no smile variations)

Alignment:
Each image in images_Polarization.zip is named by an ID (e.g., 0.jpg, 2.jpg).
These IDs match the ID column in cleaned_data.csv, ensuring that metadata and photos are aligned.

About cleaned_data.csv (columns):
- Unnamed: 0 → index from original scrape
- image → URL of the associated image
- alt → alt-text description from the HTML
- href → hyperlink to the news article
- title → article title
- 0 → original search query string
- ID → numeric ID (matches image filenames in images.zip)

Example rows:
ID=0 → Bird Strike Cripples Joe Biden Plane in California - ABC News
ID=2 → At West Point Commencement, Joe Biden Focuses on Future Challenges - ABC News

About Final_CSV_For_Analysis.csv:
- Contains counterfactual predictions and all necessary features for replication and further analysis.
- Predictions were obtained from the trained model (ML_Model.pth).
- Counterfactual images were generated using https://www.ailabtools.com/ and are stored in Counterfactuals.zip.

About ML_Model.pth:
- Trained multimodal model and weights.
- Produced using the training pipeline in Git_ML_Code.ipynb.
- Used to generate predictions and interpretability analyses.

About Counterfactuals.zip:
- Contains three sets of generated images (smiling and non-smiling versions of politicians as the main, as well as other visual features such as brightness and frown for the T).
- Generated externally using https://www.ailabtools.com/.
- Used in Git_ML_Code.ipynb for counterfactual prediction and robustness checks.

------------------------------------------------
⚙️ Download Options
------------------------------------------------

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
- Final CSV → https://drive.google.com/file/d/1Y--w5iLYjI2ir1Vk-tblAwB4Flf9o59T/view?usp=sharing
- Trained Model → https://drive.google.com/file/d/1ebV82V-8ZprrV0h59t3X7SUhfoqMUHnL/view?usp=sharing
- Counterfactuals → https://drive.google.com/file/d/1eGvsBXh62PTi4d4RxVMDjIqiuBUNiBKO/view?usp=sharing

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

- **`Scraping.ipynb`**  
  Collects raw images and article-level metadata from news sources and constructs the initial cleaned dataset used throughout the project.

- **`Git_Data_Cleaning.ipynb`**  
  Cleans and annotates the scraped data, including face verification and the construction of LDA-based topic features.

- **`Git_Multimodal_Code.ipynb`**  
  Trains and evaluates the multimodal outlet-prediction model, generates counterfactual predictions, and implements interpretability analyses (e.g., Grad-CAM and t-SNE).

- **`Git_Main_Empirical_Results.ipynb`**  
  Replicates the main empirical results in the paper using `Final_CSV_For_Analysis.csv`, which is constructed from the trained model checkpoint (`ML_Model.pth`). This notebook also implements cross-fitting procedures for estimating Overall Visual Polarization (OVP).

- **`Git_Cross_Fitting.ipynb`**  
  Implements the cross-fitting procedure, training two models on disjoint halves of the training data, and reports the performance and validation results for each model.

- **`Git_Supplementary_Results.ipynb`**  
  Contains supplementary analyses, including robustness checks using alternative visual features (e.g., brightness and frown/sadness), as well as an end-to-end reduced-form approach to studying visual polarization and its external validation.
  
------------------------------------------------
🛠 Requirements
------------------------------------------------

System:
- Python 3.9 or 3.10 (recommended)
- OS: Linux (Ubuntu 20.04+), macOS, or Windows 10/11
- Hardware: NVIDIA GPU with CUDA 
- CUDA: 11.7+ (if training with GPU)

Python packages:

- pip install torch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 --extra-index-url https://download.pytorch.org/whl/cu117
- pip install scikit-learn==1.3.0
- pip install pandas==2.0.3
- pip install matplotlib==3.7.1 seaborn==0.12.2
- pip install tqdm==4.65.0
- pip install requests==2.31.0
- pip install nltk==3.8.1
- pip install gensim==4.3.2
- pip install facenet-pytorch==2.5.2
- pip install opencv-python==4.8.0.74
- pip install pillow==10.0.0
- pip install torch_optimizer==0.3.0


Notes:
- `facenet-pytorch` is required for MTCNN and InceptionResnetV1.
- `torchvision.models.resnet101` is used for image backbone.
- `torch_optimizer` provides advanced optimizers (AdamW etc.).
- Ensure CUDA/cuDNN are installed if you plan to train on GPU.

✅ Once this environment is set up, the notebooks (`Git_Data_Cleaning.ipynb`, `Git_ML_Code.ipynb`, `Git_Results.ipynb`) and the training code will run correctly. Both images and metadata will be aligned via the `ID` field in the CSV.
