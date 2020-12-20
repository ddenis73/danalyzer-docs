# Loading data

To import data, navigate to File --> Load data or press CTRL + O (CMD + O on Macs). This will bring up a window giving you options to load various types of data. Either type or use the push button to navigate to the file you wish to load. Currently, sleepDanalyzer can open the following types of file:

- **Load dataset**: This is the PSG data you want to load. Currently, sleepDanalyzer can read files saved in the following formats (.edf (European Data Format), .set (EEGLAB native format), .vhdr (BrainVision Recorder hearder file), .mat)
- **Load sleep stages**: Load an existing score file that has been scored using sleepDanalyzer (must be a .mat file). See here for instructions of how to import various kinds of score files from other software/formats
- **Load events**: An events file, also sometimes called a notations or annotations file, is a file that contains key events that happened during a recording (e.g. lights off/on times, biocalibrations, impedence checks etc.). Events files can be .mat, .csv, or .vmrk (BrainVision events file).
- **Load ar**: AR stands for **A**rtifact **R**ejection (must be a .mat file) and contains information regarding bad channel and/or segments of data.

If you are scoring a new record, you will likely only want to load data and an events file. After selecting all the various types of file you wish to load, click OK to load the data (this may take a while depending on the size of the data file). When all of the data has been loaded, a new window will appear. This window will let you enter the recording start time, lights off time, and lights on time If you loaded a correctly formatted events file, these fields will automatically be filled if the events file contained the relevant events. if you don't have an events file, you can enter lights off and lights on times manually.

The epoch length field specifies the epoch size you wish to use for scoring, and defaults to 30 seconds. You can produce a spectogram on a specific channel by entering the name of the channel in the spectogram field. Use the scorer initial field to identify the individual who scored the record. When everything is correct, click Confirm to pull the data into the GUI. If you have computed a spectogram, it will take some time to complete. If everything went well, your data will appear something like this:

![danalyzer_full](../img/danalyzer_full.png)

## danalyzer file types

Danalyzer has a strict format for how sleep scores, events, and artifact rejection information needs to be stored. The sections below detail in depth the structure of the key file types used by danalyzer. This section will be particularly useful for people trying to import data from another system/software package, and also for using danalyzer data files in downstream analysis.

### PSG file

When data is loaded into danalyzer, it is stored as a psg structure. If you export/import PSG data as a .mat file, this is is the format which that data will follow:

```matlab
psg = 

  struct with fields:

    data: [9×6664000 single]
    hdr: [1×1 struct]
    chans: [9×1 struct]
```

-**data**: The data itself, stored as channels x timepoints
-**hdr**: A header file which contains the following fields: (srate: sampling rate in Hz, samples: The number of samples in the data, recStart: The start date/time of the original recording)
-**chans**: Channel information (names, type, position), stored in the same way as EEGLAB

### Score file

Files that are scored in danalyzer are written as .mat files with the variable name *sleepstages*. This variable is a struct with the following fields:

```matlab

sleepstages = 

  struct with fields:

    stages: [1112×1 double]
       hdr: [1×1 struct]


```

- **stages**: This field contains the sleep stages themselves. Each row is an epoch, and the number corresponds to a certain sleep stage as follows (0 = Wake, 1-4 = N1-N4, 5 = REM, 6 = Movement, 7 = Unstaged)
- **hdr**: This field contains another structure containing additional information about the record. These fields are as follows:

```matlab

sleepstages.hdr

ans = 

  struct with fields:

  	srate: 200
  	win: 30
    recStart: '00:02:33.00'
    lOff: '00:09:07.85'
    lOn: '08:39:05.65'
    onsets: [1112×1 double]
    stageTime: [1×1112 double]
    notes: ''
    scorer: 'DD'

```

- **srate**: The sampling rate of the data (in Hz)
- **win**: The size of scored epochs (in seconds)
- **recStart**: The recording start time
- **lOff**: Lights off time
- **lOn**: Lights on time
- **onsets**: The onset time of each epoch in samples (epoch 1 = 1)
- **stageTime**: The onset time of each epoch in seconds (epoch 1 = 0)
- **notes**: Any notes made about the record during scoring
- **scorer**: The person who scored the record

### Events file

Events files are tables (can be either a MATLAB table variable or a spreadsheet e.g. csv). The table must contain two columns. Column 1 is the clock time of the event, and column 2 is the event label. Note that danalyzer can also import BrainVision event files (.vmrk) that have their own organization structure.

### AR files

Any artifact rejection that is carried out in sleepDanalyzer is saved into an ar struct, saved as a .mat file with the variable name *ar*. The structure contains the following fields:

```matlab
ar = 

  struct with fields:

       badchans: [9×1 double]
      badepochs: [1110×1 logical]
    badsegments: []
```

- **badchans**: An n x 1 vector where n = the number of channels in the data. If the channel has been marked as bad it is indicated as a 1 , otherwise it is zero.
- **badepochs**: An n x 1 vector where n = the number of epochs in the data. If the epoch has been marked as bad it is indicated as a 1, otherwise it is zero.
- **badsegments**: The bad segments field is populated when artifactual periods of data have been detected as continuous segments, rather than as an entire epoch. Bad segment arrays have an n x 9 size, where n = the total number of bad segments. Each column contains the following information (The epoch the segment was marked in, the sleep stage of that epoch, the type of marking (1, 2, 3), start time (s), end time (s), duration(s), start time (sample), end time (sample), duration (sample)).

## Importing data from other sources

Danalyzer contains limited functionality for importing data in different formats to the ones described above. Such a scenario may arise where you want to load a file scored in a different software. To import externally scored files, first load the PSG file using File --> Open, but do not use the load sleep stages option here. Instead, load the PSG file by itself, and then navigate to File --> Import --> Sleep scores. You will then see a list of options for importing different types of sleep scores. Currently, danalyzer can automatically import files scored using Hume, Luna, and TWin. It can also attempt to load generic .txt and .csv files, where each row corresponds to a scored epoch of sleep. If using this option, a dialog box will appear asking you how each sleep stage is identified in your data (e.g. what is wake, N1, N2 etc coded as). If your external file does not correspond to any of the above options, then you will need to convert it manually to danalyzer format using a custom script.

**There are currently no way to import events and ar files that do not conform to the specifications described above.**