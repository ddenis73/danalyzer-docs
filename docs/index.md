# danalyzer

This site provides documentation and tutorials on visualizing and analyzing polysomnography (PSG) data in MATLAB using **the danalyzer**

## What is the danalyzer?

danalyzer is a toolbox for MATLAB for visualizing and analyzing sleep signals. The toolbox is primarily a graphical user interface (GUI) for visualizing and scoring PSG data. The motivation for writing it was to replace obsolete propriatary sleep scoring software, and to allow a common program for viewing data, sleep scoring etc. across labs using different systems. It is publically released in case it is something other might find useful.

After installing, follow the [Quickstart](/gui-tutorial/) to get started. 

## Installation

### 1. Download danalyzer

- The most up-to-date version can be downloaded [here](https://github.com/ddenis73/danalyzer)
	- Click Code --> Download ZIP
- Move the zipped folder to somewhere on your computer where you can find it again
- Unzip the folder (on PC: right click and choose "Extract All", on Mac: double click the file)

### 2. Download EEGLAB

danalyzer relies on EEGLAB functions to help with importing different types of data. If you already have EEGLAB downloaded you can skip this step

- Download EEGLAB [here](https://sccn.ucsd.edu/eeglab/download.php)
- Unzip the eeglab.zip folder and move it somewhere on your computer where you can find it again

### 3. Add danalyzer to MATLAB

!!!Warning
	Make sure you have administrator privilages for running MATLAB, or else you may run into problems saving the updated MATLAB path.

- Open MATLAB
- In the "Current Folder" section of the MATLAB window navigate to the EEGLAB folder (you should be inside this folder and see a file called eeglab.m)
- In the "Command Winow" section of the MATLAB window type *eeglab* and press Enter
- It should pop up a blue/purple window
	- **To read EDF files**: Download the biosig extension. Within the EEGLAB window, click File --> Manage EEGLAB Extensions --> Find and click on Biosig --> Click Install/Update --> Click Yes
	- **To read BrainVision files**: Download the bva-io extension. Within the EEGLAB window, click File --> Manage EEGLAB Extensions --> Find and click on bva-io --> Click Install/Update --> Click Yes
- Navigate back to the main MATLAB window and click on the Home tab (at the top of the MATLAB window)
- Click on the "Set Path" icon. A new smaller window will pop up
- Click on "Add with Subfolders"
- Within the new window that pops up, navigate to the folder where you put the unzipped danalyzer-main folder. Then click on the danalyzer-main folder to select it, and press the "Select folder" button
- This should take you back to the "Add path" window. Click on "Save"

To see if it worked, in the Command Window section of MATLAB type *sleepDanalyzer* and press Enter. If everything installed correctly, you should now see the main danalyzer window:

![danalyzer_blank](../img/danalyzer_empty.png)

## License

danalyzer is open source and released under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html) license and comes with absolutely no warrenty; without even the implied warrenty of merchantability or fitness for a particular purpose. danalyzer is intended for research purposes only. Any commercial or medical use of this software is prohibited. The authors accept to responsibility for its use in this manner.