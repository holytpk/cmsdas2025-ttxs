# Installing Pepper

Install Pepper:


```sh
git clone <repository url> pepper
cd pepper
source example/environment.sh
python3 -m pip install --upgrade --upgrade-strategy eager --editable .
python3 -m pip install "urllib3<2"
```

(`<repository url>` can be `ssh://git@gitlab.cern.ch:7999/pepper/pepper.git` or  `https://gitlab.cern.ch/pepper/pepper.git` )

To check that your installation of pepper is working, try running the following commands, which will run an example processor in debug mode. This can be run locally.

```sh
cd example
python3 -m pepper.runproc example_processor.py example_config.json -d
```

# Installing combine

We don't really "use CMSSW" in this exercise, but we use the standard CMS statistical fitting tool combine, which is usually installed within CMSSW.
Follow the instructions below if you do not have an installed version from a previous exercise.

### Combine v9 - recommended version

The nominal installation method is inside CMSSW. The current release targets
CMSSW `11_3_X` series because this release has both python2 and python3 ROOT
bindings, allowing a more gradual migration of user code to python3. Combine is
fully python3-compatible and can work also in 12_X releases.

```sh
cmsrel CMSSW_11_3_4
cd CMSSW_11_3_4/src
cmsenv
git clone https://github.com/cms-analysis/HiggsAnalysis-CombinedLimit.git HiggsAnalysis/CombinedLimit
cd HiggsAnalysis/CombinedLimit
```
Update to a recommended tag - currently the recommended tag is **v9.1.0**: [see release notes](https://github.com/cms-analysis/HiggsAnalysis-CombinedLimit/releases/tag/v9.1.0)

```sh
cd $CMSSW_BASE/src/HiggsAnalysis/CombinedLimit
git fetch origin
git checkout v9.1.0
scramv1 b clean; scramv1 b 
```

### Combine harvester

This package serves as an interface to combine with many scripts that handle some advanced use cases. 
The name is a bad joke about tractors.
We will need it to make some nice plots, so install it using the following commands:

```sh
bash <(curl -s https://raw.githubusercontent.com/cms-analysis/CombineHarvester/main/CombineTools/scripts/sparse-checkout-ssh.sh)
scramv1 b clean; scramv1 b 
```

