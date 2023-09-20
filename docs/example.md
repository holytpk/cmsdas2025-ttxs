# Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

# Pepper - ParticlE Physics ProcEssoR
A python framework for analyzing NanoAODs. Easy to use and highly configurable.

The framework is designed to allow analysis of any type of event topology. For reference this repository comes with the necessary tools for a <img src="https://latex.codecogs.com/gif.latex?\mathrm{t\bar{t}}\rightarrow\mathrm{b\bar{b}}\mathrm{ll\nu\nu}" /> analysis.



## Installation
It is recommended to use a proper environment with Pepper. An example environment setup for DESY NAF can be found [here](example/environment.sh), which can be sourced after cloning the repository.
Pepper can be installed as a python package as follows:
```sh
git clone <repository url> pepper
cd pepper
source example/environment.sh
python3 -m pip install --upgrade --upgrade-strategy eager --editable .
# Additionally only if on CentOS7 (e.g. DESY NAF in 2023):
python3 -m pip install "urllib3<2"
```
This will update all dependencies to the latest version. Now `pepper` can be imported as any other python package from any location. Because of the `--editable` option, if you edit files inside your cloned pepper directory, the changes will be in effect already the next time you `import pepper`.

__Note__: If you are on CentOS7, please run `python3 -m pip install "urllib3<2"`, as written above. CentOS7 is lacking a recent OpenSSL version, thus an older urllib3 version is required.



## Usage

### Getting started

In Pepper an analysis is implemented as a Processor class. A short example of such a Processor with many explanatory comments can be found in [here](example/example_processor.py). This processor can be run by executing `python3 -m pepper.runproc example_processor.py example_config.json` (when inside the example directory). Also running `python -m pepper.runproc -h` will show the available command line options.

