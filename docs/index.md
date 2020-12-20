# danalyzer

This site provides documentaion and tutorals on analyzing polysomnography (PSG) data in MATLAB using "the danalyzer".

## What is the danalyzer?


Danalyzer is a toolbox for MATLAB for visualizing and analyzing sleep signals. The toolbox contains a graphical user interface (GUI) and a set of functions for performing common electrophysiological analyses including power spectral density, automated sleep spindle and slow oscillation detection, and slow oscillation-spindle coupling. As of **December 2020** the toolbox is available privately, with a public release planned in the early part of 2021. For now, SAMLAB members can download everything from the [lab code wiki](https://osf.io/jcaq7/). Outside users should contact Dan directly to obtain the code.

## Getting started

After downloading sleepDanalyzer, the best place to start is the tutorials. 

After downloading danalyzer, the best place to start is the tutorials. Work through these to familiarize yourself with how to use the toolbox. There are separate tutorials for [using MATLAB](matlab-tutorial.md),using [danalyzer-gui](gui-tutorial.md) and [danalyzer-tools](tools-tutorial.md). To use danalyzer you will need to install MATLAB. ND members can download MATLAB for free through Software Downloads on Inside ND. 

As well as the base MATLAB installation, you will also need to install the following additional toolboxes:

* Signal processing
* Wavelet
* Machine Learning and Statistics
* Curve Fitting

danalyzer-gui also uses EEGLAB to import .edf and .vhdr files. The GUI will not work without EEGLAB installed and on the MATLAB path. Go [here](https://sccn.ucsd.edu/eeglab/download.php) to download EEGLAB. After install, make sure the *biosig* and *bva* extensions are added.

## Installing danalyzer

Unzip the files and move to a folder on your computer. In order to run danalyzer in MATLAB, it needs to be added to the path. You can do this in MATLAB:

```matlab

% Add the GUI to the path

addpath(genpath('danalyzer-gui root folder'))

% Add the tools to the path

addpath(genpath('danalyzer-tools root folder'))

```

If you are using danalyzer frequently, you may want to add it to your *startup* file in MATLAB