# sleepDanalyzer GUI

With sleepDanalyzer downloaded and added to the MATLAB path, start the GUI by typing:

```matlab
sleepDanalyzer
```

into the MATLAB command window. This will print some text to the command window. If everything has been installed correctly, you should see something like this:

```matlab
Starting sleepDanalyzer version: 0.9.0

NOTE: This is a beta version of sleepDanalyzer!!!
Features still in development

Welcome to sleepDanalyzer!
```
The GUI relies on a number of EEGLAB functions to help import data of different types. If sleepDanalyzer cannot find these import functions, you will get a warning e.g.:

```matlab
Warning: BIOSIG extension for EEGLAB not found. Will not be able to import .edf files
```
If you get a warning like this, check your EEGLAB installation and ensure that 1) EEGLAB is on the MATLAB path, and 2) the relevant EEGlAB extensions are installed (BIOSIG extension required for .edf files, and BVA-IO extension required for BrainVision files).

If all has gone well, a blank GUI will have opened.

![danalyzer_blank](../img/danalyzer_empty.png)

