Run Guide

This project runs in Google Colab using datasets 

 1. Clone or open the notebooks


git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git


Replace the URL with your GitHub repository URL. Open the `.ipynb` files in [Google Colab](https://colab.research.google.com/) and select Runtime > Change runtime type > GPU>A100.

2. Install libraries and connect Drive

Run in Colab:

python
%pip install -q timm captum lime shap scikit-image opencv-python-headless
from google.colab import drive
drive.mount('/content/drive')

3. Prepare files

Download the DR2015, DRIVE, and CHASE_DB1 datasets. Place the datasets, generated vessel masks in Google Drive. 

Note: Cloning the repository does not automatically download datasets, generated masks.

4. Execute in order
Combine(2).ipynb - prepare vessel data.
Stage1 (13)(1).ipynb - train/evaluate RGB-only B0.
stage2_latest (9)(20261030-161345).ipynb/s2.ipynb - segment vessels.
s3part1 (10)(20261030-161353).ipynb - generate masks and run cGAN refinement.
DCgan (3).ipynb - generate masks and run DCGAN refinement (separate experiment).
stage3classificationusingstage2predictedmask (17)(20261030-161403).ipynb - Stage 3 predicted-mask classification configuration (B0+B3+SE) and XAI.
stage3part2 (25)(20261102-054250).ipynb - Stage 3 cGAN-refined-mask classification configuration (B0+B4+SE) and XAI.
B0+B3+SEDCganmasks.ipynb - DCGAN-refined masks classification configuration (B0+B3+SE).
Zero_mask (1)(2).ipynb - run zero-mask tests.
b0+b3.ipynb, b0+b4s3.ipynb-Without SE tests
vesselonlydr.ipynb-stage 4 vessel only classification
