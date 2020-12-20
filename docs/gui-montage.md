# Montages

It is likely that you will want to change some details about how the data looks for the purposes of sleep scoring. All of these alterations are commanded through a montage file, a MATLAB script that controls how the data are presented. To select a montage, click on the montage list to open a drop-down menu. Click on the montage you wish to use and the display will update accordingly. 

![danalyzer_with_montage](..img/danalyzer_montage_applied.png)

*In this example, applying the montag added scale lines around channel F3. It also re-colored EOG and EMG channels blue and red respectively.*

For your first record with a new system, you will need to create a new montage. See the montage creation section of this guide for full details. It is highly recommeded that you export your sleep scoring file with the correct referecnes and filters already applied. For cases where this is not possible, the next best option is to batch preprocess your data before scoring. It is not suggested that you import unprepared data straight into danalyzer. See the vignettes section for a template script for preparing files for sleeping scoring.

## Editing a montage

You can edit a montage 'on-the-fly' by navigating to Montage --> Edit montage (or by pressing m), which brings up a dialog window. The fields are automatically populated with th current montage settings. You can specify any of the following changes:

- **Scale**: Integer specifying a new default scale for all channels
- **Scale channel**: The channel that you wish the scale lines to be displayed around. Leaving this blank will remove the scale lines entirely.
- **Scale values**: Vector indicating where to place each scale line.
- **Scale color**: A MATLAB [RGB triplet](https://www.mathworks.com/help/matlab/ref/colorspec.html) indicating the color of the scale lines.
- **Hide channels**: A list of channels you wish to hide (i.e. remove from the display)
- **Channel order**: The order in which the channels are displayed. If you specify channels to hide, ensure that they are *not* listed in the channel order.
- **EEG color**: The color of all EEG channels
- **EOG color**: The color of all EOG channels
- **EMG color**: The color of all EMG channels
- **ECG color**: The color of all ECG channels
- **Other colors**: The color of all other channels.

Press OK to adopt the new settings. You can always revert back to a pre-defined montage by selecting it from the montage list. You can also clear the montage entirely by navigating to Montage --> Clear montage.

When you are happy with your montage settings, we can begin scrolling the data and sleep scoring!