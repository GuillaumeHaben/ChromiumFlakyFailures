# ICSE submission
Replication package for the paper: The Importance of Discerning Flaky from Fault-triggering Test Failures: A Case Study on the Chromium CI

# Download datasets
The following files are required:
- `dataset.35past.Linux10k.json`
- `dataset.pass.json`
- `nft-121.json`
- `nft-123.json`

They can be found at this address: https://figshare.com/s/4dbab50a216a1b3a3172

Once downloaded, place the files in this same directory.

# Requirements
In the current folder, create a python virtual environment and install the requirements in it. 
`python3.8 -m venv "venv"`  
`source venv/bin/activate`  
`pip3 install -r requirements.txt`

Install the kernel to use in jupyter  
`python -m ipykernel install --user --name=chromium`


# Run experimentations
Scripts can be found as 2 Jupyter Notebooks.
- `rqs.ipynb` contains the scripts to train and test models used in RQ 1, 2 and 3.
- `discussion.ipynb` contains the scripts used to get information necessary for the Discussion section.

Command to launch Jupyter Notebook:
- `pip install notebook`
- `jupyter notebook` (Launch both notebooks with the chromium kernel)