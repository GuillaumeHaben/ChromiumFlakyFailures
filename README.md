# ASE 2024 submission
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

# Dataset collection

## Build Dataset

* Get information about a builder

`python buildDataset.py /PATH/TO/RESULTS BUCKET BUILDER_NAME BUILD_NUMBER NB_BUILDS`

Will get information about the BUILDER_NAME from BUCKET. 
Starts with BUILD_NUMBER, then analyze past NB_BUILDS. 
Save results in /PATH/TO/RESULTS

e.g. `python buildDataset.py ./results ci Mac11.0_Tests 825 2` will get information about tests, build, artifacts for [https://ci.chromium.org/ui/p/chromium/builders/ci/Mac11.0%20Tests/825/test-results?q=](https://ci.chromium.org/ui/p/chromium/builders/ci/Mac11.0%20Tests/825/test-results?q=) and 1 build before (824). Will save the results in `./results`

Important: Space in the builder name should be replaced with `_`

* Results

Results are saved in `./results`

Folder structure:
```
./results/
    BUCKET.BUILDER_NAME.BUILD_NUMBER/
        testsInfo.json
        buildInfo.json
        1/
            testInfo.json
            Run-ResultId/
                artifacts[.txt|.html]

```

## Get Sources


* Following updates on the platform, this script add test sources for the current commit.
Works for tests which do not contain line number in their metadata (full file test) so mainly `.html` and `.js`. 

`python getSources.py /PATH/TO/RESULTS/BUILDER/`


## Prepare Dataset


* Go through the results folder and prepare a JSON dataset.

`python prepareDataset.py /PATH/TO/RESULTS/BUILDER/`
