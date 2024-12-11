# Pre-Exercise

This section provides the preliminary steps to set up the environment for the CMSDAS 2024 exercises. Follow these instructions carefully to ensure a smooth analysis workflow.

## Pre-requisites
Two installations are required to complete the exercises:

1. **Pepper Analysis Framework**
2. **Combine Fitting Tool**

### Installing Pepper

We use a special fork of the Pepper analysis framework for this exercise. Follow these steps:

1. Clone the repository and set up the environment:
```bash
git clone <repository_url> pepper
cd pepper
source example/environment.sh
```

2. Create a Python virtual environment:

```sh
python -m venv env_pepper
source env_pepper/bin/activate
export PYTHONPATH=$(pwd)/env_pepper/lib/python3.9/site-packages
```

3. Install Pepper and required packages:
```sh
python -m ensurepip --upgrade
python -m pip install -r pip_requirements.txt
python -m pip install --upgrade-strategy only-if-needed --editable .
```

Replace <repository_url> with:

ssh://git@gitlab.cern.ch:7999/cmsdas-cern-2024/long-ex-top-xsec.git or
https://gitlab.cern.ch/cmsdas-cern-2024/long-ex-top-xsec.git

4. Test the Pepper installation:
```sh
cd example
python3 -m pepper.runproc example_processor.py test_config.hjson -d

```

### Setting Up the Environment

To simplify the setup in new sessions:

1. Copy the example/environment.sh file to a personal script:
```bash
cp example/environment.sh my_environment.sh
```
2. Edit my_environment.sh to include the Python environment and Pepper repository directory. Uncomment the relevant lines.
3. Run the script in new sessions:
4. source my_environment.sh

### Installing Combine

We don't really "use CMSSW" in this exercise since we use Run-III datasets, but we use the standard CMS statistical fitting tool combine, which is usually installed within a CMSSW environment. Follow the instructions below if you do not have an installed version from a previous exercise. This should be done in a fresh LXplus session.

The Combine fitting tool is used for statistical analysis. Follow these steps for installation:

1. Use CMSSW version CMSSW_14_1_0_pre4:
```bash
source /cvmfs/cms.cern.ch/cmsset_default.sh
cmsrel CMSSW_14_1_0_pre4
cd CMSSW_14_1_0_pre4/src
cmsenv
git clone https://github.com/cms-analysis/HiggsAnalysis-CombinedLimit.git HiggsAnalysis/CombinedLimit
cd HiggsAnalysis/CombinedLimit
git fetch origin
git checkout v10.0.0
scramv1 b clean; scramv1 b -j 8
```
2. Use a separate terminal for Combine due to CMSSW-specific environment variables:
```bash
cd src/
cmsenv
```
Combine is now ready to use.

### CombineHarvester

As of v10, the "CombineTool" scripts needed to make impact plots are included in the main combine installation, so a separate installation of CombineHarvester is not needed for this exercise. Currently, if you want to use CombineHarvester for its other features beyond those provided in the "combineTool" scripts, you will need to run it using a container (el7 or similar) 
