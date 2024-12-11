# CMSDAS 2024 - Run3 tt Cross Section

In this exercise we will perform a measurement of the top quark pair production cross section using ~1 fb-1 of data collected during the early days of LHC Run 3.

This exercise was adapted from the measurement [TOP-22-012](https://cds.cern.ch/record/2852881).

## About the exercise

The exercise will use pepper, an analysis framework started at DESY that was used for the original analysis. Students will learn to work with recently popular columnar analysis strategies in python.

The analysis required custom NanoAOD samples skimmed from Winter22 early run 3 CMS Monte Carlo samples. To keep the exercise python-focused and separated from CMSSW, these samples are provided, along with a working but simplified pepper setup. Many things are missing in this setup, which will be added over the course of the exercise, until a measurement can be performed.

While the analysis used $t\bar{t}$ dilepton and lepton+jets decays, the exercise will focus on the dilepton channel for simplicity. Some goals of the exercise are:

1. Understand the basic structure of pepper
2. Make histograms and plots of CMS Run3 data
3. Add new cuts and uncertainties to the analysis
4. perform a fit to measure the cross section using [Combine](https://cms-analysis.github.io/HiggsAnalysis-CombinedLimit/)
5. Study the fit outcome, and improve the analysis to obtain the most realistic result possible in the alloted time!

## About pepper

[Pepper](https://gitlab.cern.ch/pepper/pepper) is a python-based analysis framework designed for CMS data in the nanoAOD format. It uses columnar methods, meaning that it avoids event loops and instead prefers to load data by columnar chunks and use vector/matrix methods to speed up computation time in python. It makes use of methods from coffea and packages in the sci-kit HEP ecosystem, in particular uproot, awkward arrays, and the hist package.

Pepper uses dask for job management. The default condor submission options were originally tuned to run on DESY's NAF computing facilities, but it seems fine on LXPLUS as well. It is used by a number of analyses in the DESY CMS Top group and is spreading to other groups in Germany which use the same computing resources.

Let’s get started and make the most of your CMSDAS experience!
