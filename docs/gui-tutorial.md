# sleepDanalyzer GUI

With the sleepDanalyzer folder downloaded and added to the MATLAB path, you can load the GUI by typing:

```matlab
sleepDanalyzer
```

into the MATLAB command line. This will print some text to the Command Window:

```matlab
Starting sleepDanalyzer version: 0.9.0

NOTE: This is a beta version of sleepDanalyzer!!!
Features still in development

Welcome to sleepDanalyzer!
```
Make a note of the version of danalyzer you are using. This will help with troubleshooting! The GUI relies on a number of EEGLAB functions to help import data of different types. If danalyzer cannot find these import functions, it will give you a warning. e.g.:

```matlab
Warning: BIOSIG extension for EEGLAB not found. Will not be able to import .edf files
```
While this message won't prevent you from opening the GUI, it will mean that you won't be able to import any .edf files. If you get a warning like this, check your EEGLAB installation and ensure that it is 1) on the MATLAB path, and 2) the relevant extensions are installed (BIOSIG extension in this is case).

If all has gone well, a blank GUI will have opened. We can now get started analyzing data!

![danalyzer_blank](../img/danalyzer_empty.png)

