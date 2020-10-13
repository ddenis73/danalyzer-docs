# danalyzer

This site provides documentation and tutorials on performing analyses of sleep polysomnography (PSG) data in MATLAB using "the danalyzer"

## What is the danalyzer

danalyzer is a set of MATLAB tools for visualization and analysis of sleep signals. There are two core components to the toolbox. The GUI (danalyzer-gui) for visual data inspection, sleep scoring, and manual artifact rejection. Second, there are a set of tools (danalyzer-tools) to perform common electrophysiological analyses including power spectral density, sleep spindle and slow oscillation detection, and slow oscillation-spindle coupling. As of **October 2020** the tools are available privately. The plan is to make a public release in the future. For now, SAMLAB members can download everything from the lab code wiki. Outside users should contact Dan to obtain the code. 

## Getting started

After downloading danalyzer, the best place to start is the tutorials. Work through these to familiarize yourself with how to use the toolbox. There are separate tutorials for using danalyzer-gui and danalyzer-tools. To use danalyzer you will need to install MATLAB. ND members can download MATLAB for free through Software Downloads on Inside ND. 

As well as the base MATLAB installation, you will also need to install the following additional toolboxes:

* Signal processing
* Wavelet
* Machine Learning and Statistics
* Curve Fitting

danalyzer-gui also uses EEGLAB to import .edf and .vhdr files. The GUI will not work without EEGLAB installed and on the MATLAB path. Go here to download EEGLAB. After install, make sure the *biosig* and *bva* extensions are added.

## Installing danalyzer

Unzip the files and move to a folder on your computer. In order to run danalyzer in MATLAB, it needs to be added to the path. You can do this in MATLAB:

```matlab

% Add the GUI to the path

addpath(genpath('danalyzer-gui root folder'))

% Add the tools to the path

addpath(genpath('danalyzer-tools root folder'))

```

If you are using danalyzer frequently, you may want to add it to your *startup* file in MATLAB