# danalyzer

This site provides documentaion and tutorals on analyzing polysomnography (PSG) data in MATLAB using "the danalyzer".

## What is the danalyzer?


Danalyzer is a toolbox for MATLAB for visualizing and analyzing sleep signals. The toolbox contains a graphical user interface (GUI) and a set of functions for performing common electrophysiological analyses including power spectral density, automated sleep spindle and slow oscillation detection, and slow oscillation-spindle coupling. As of **December 2020** the toolbox is available privately, with a public release planned in the early part of 2021. For now, SAMLAB members can download everything from the [lab code wiki](https://osf.io/jcaq7/). Outside users should contact Dan directly to obtain the code.

## Getting started

After downloading sleepDanalyzer, the best place to start is the tutorials. If you are new MATLAB, the [MATLAB tutorials](matlab-tutorial.md) will be helpful for familiarizing yourself with the MATLAB environment, and provides a basic introduction to MATLAB programing. The [GUI tutorial](gui-tutorial.md) provides an in-depth walkthrough for using the GUI. The [tools tutorial](tools-tutorial.md) demonstrates how to use danalyzer functions for sleep EEG analysis. To use danalyzer you will need to install MATLAB. ND members can download MATLAB for free through Software Downloads on Inside ND. 

As well as the base MATLAB installation, you will also need to install the following additional toolboxes:

* Signal processing
* Wavelet
* Machine Learning and Statistics
* Curve Fitting

danalyzer-gui also uses EEGLAB to import .edf and .vhdr files. The GUI will not work without EEGLAB installed and on the MATLAB path. Go [here](https://sccn.ucsd.edu/eeglab/download.php) to download EEGLAB. After install, make sure the *biosig* and *bva* extensions are added. You can learn how to install EEGLAB extensions [here](https://sccn.ucsd.edu/wiki/EEGLAB_Extensions).

## Installing danalyzer

Unzip the files and move to a folder on your computer. In order to run danalyzer in MATLAB, it needs to be added to the path. This can be done either by going Home --> Set Path and adding the danalyzer folder (use the Add with Subfolders option) and then clicking save. Alternatively, add danalyzer to the path with the following code:

```matlab

% Add the toolbox to the path

addpath(genpath('sleepDanalyzer root folder'))


```

If you are using danalyzer frequently, you may want to add it to your [startup](https://www.mathworks.com/help/matlab/ref/startup.html) file in MATLAB. This will save you from needing to add danalyzer to the path each time you use it.