# Visual-Polarization-Measurement-Using-Counterfactual-Image-Generation
This paper, we introduce the Polarization Measurement Using Counterfactual Image Generation (PMCIG) method, which combines economic theory with generative models and multi-modal deep learning to fully utilize the richness of image data and provide a theoretically grounded measure of polarization in visual content.

---------------------------------------------------------------------------------

📂 Data Setup

This project uses two files:
- cleaned_data.csv  → metadata scraped from news articles
- images.zip        → corresponding images

Alignment:
----------
Each image in images.zip is named by an ID (e.g., 0.jpg, 2.jpg).  
These IDs match the ID column in cleaned_data.csv → so metadata and photos are aligned.

About cleaned_data.csv (columns):
---------------------------------
- Unnamed: 0  → index from original scrape
- image       → URL of the associated image
- alt         → alt-text description from the HTML
- href        → hyperlink to the news article
- title       → article title
- 0           → original search query string
- ID          → numeric ID (matches image filenames in images.zip)

Example rows:
ID=0 → Bird Strike Cripples Joe Biden Plane in California - ABC News  
ID=2 → At West Point Commencement, Joe Biden Focuses on Future Challenges - ABC News

Option 1: Automatic Download (Recommended)
------------------------------------------
pip install requests
python Initial/setup_data.py
(downloads CSV + ZIP and extracts into data/)

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
      ├── 0.jpg
      ├── 2.jpg
      └── ...

✅ Once set up, notebooks (Scraping.ipynb, Data_Cleaning.ipynb, etc.) will load both images and metadata correctly, with IDs keeping them aligned.
