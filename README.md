# Visual-Polarization-Measurement-Using-Counterfactual-Image-Generation
This paper, we introduce the Polarization Measurement Using Counterfactual Image Generation (PMCIG) method, which combines economic theory with generative models and multi-modal deep learning to fully utilize the richness of image data and provide a theoretically grounded measure of polarization in visual content.




## 📂 Data Setup

This project relies on two dataset files:
- A ZIP archive of images
- A cleaned CSV file that matches each image ID

You can prepare the dataset in **two ways**:

### 🔹 Option 1: Automatic Download (Recommended)

```bash
# 1. Install the required dependency
pip install requests

# 2. Run the setup script
python Initial/setup_data.py

# This will:
# - Download the CSV file into data/cleaned_data.csv
# - Download the ZIP file into data/images.zip
# - Extract the images into data/images/

# After running, your folder structure will look like:
# data/
#  ├── cleaned_data.csv
#  └── images/
#       ├── 0001.jpg
#       ├── 0002.jpg
#       └── ...


### 🔹 Option 2: Manual Download
# 1. Download manually from Google Drive:
# - Images ZIP: https://drive.google.com/file/d/1yv6A7IgkxR7cqQ7pKyDC5VUtlzuZJo9v/view?usp=sharing
# - Cleaned CSV: https://drive.google.com/file/d/1VLKIx58fEqJZ3ButMooVtRBa9_8CZdSl/view?usp=sharing

# 2. Create a folder called "data/" in the project root
mkdir data

# 3. Place the files inside "data/" as follows:
# data/
#  ├── cleaned_data.csv
#  ├── images.zip

# 4. Unzip images.zip so the folder looks like:
# data/
#  ├── cleaned_data.csv
#  └── images/
#       ├── 0001.jpg
#       ├── 0002.jpg
#       └── ...

