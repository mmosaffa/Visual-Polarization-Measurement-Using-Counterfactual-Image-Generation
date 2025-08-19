# Visual-Polarization-Measurement-Using-Counterfactual-Image-Generation
This paper, we introduce the Polarization Measurement Using Counterfactual Image Generation (PMCIG) method, which combines economic theory with generative models and multi-modal deep learning to fully utilize the richness of image data and provide a theoretically grounded measure of polarization in visual content.




📂 Data Setup

Required files:
- cleaned_data.csv
- images.zip (with all images)

Option 1: Automatic Download (Recommended)
------------------------------------------
pip install requests
python Initial/setup_data.py
(Downloads CSV + ZIP and extracts into data/)

Option 2: Manual Download
-------------------------
Download from:
- Images ZIP: https://drive.google.com/file/d/1yv6A7IgkxR7cqQ7pKyDC5VUtlzuZJo9v/view?usp=sharing
- CSV File : https://drive.google.com/file/d/1VLKIx58fEqJZ3ButMooVtRBa9_8CZdSl/view?usp=sharing

mkdir data
Place files as:
data/cleaned_data.csv
data/images.zip

Unzip manually:
data/
 ├── cleaned_data.csv
 └── images/
      ├── 0001.jpg
      ├── 0002.jpg
      └── ...

✅ Done! Now run the notebooks (Scraping.ipynb, Data_Cleaning.ipynb, etc.)

