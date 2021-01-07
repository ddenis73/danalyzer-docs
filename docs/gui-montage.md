# Montages

It is likely that you will want to change some details about how the data look for the purposes of sleep scoring. All of these alternations are commanded through a montage file, a MATLAB script that controls how the data are presented. To select a montage, click on the montage list and select which montage you want to use. The display will update accordingly:

![danalyzer_with_montage](..img/danalyzer_montage_applied.png)

*In this example, applying the montag added scale lines around channel F3. It also re-colored EOG and EMG channels blue and red respectively.*

## Editing a montage

You can edit a montage on-the-fly by navigating to Montage → Edit montage (or by pressing the m key), which brings up a dialog window. You can specify any of the following changes:

- **Scale**: Integer specifying a new scale for all channels
- **Scale channel**: The channel that you wish the scale lines to be displayed around. Leaving this blank will remove scale lines entirely
- **Scale values**: A value indicating where to place each scale line
- **Scale color**: A MATLAB RGB triplet indicating the color of the scale lines
- **Hide channels**: A list of channels you want to hide (i.e. remove from the display)
- **Channel order**: The order in which the channels are displayed. If you specify channels to hide, ensure that they are not listed in the channel order.
- **EEG color**: The color of all EEG channels
- **EOG color**: The color of all EOG channels
- **EMG color**: The color of all EMG channels
- **ECG color**: The color of all ECG channels
- **Other color**: The color of all other channels

Click OK to adopt these new settings. You can always revert back to a predefined montage by selecting it from the montage list. You can also clear the montage entirely by navigating to Montage → Clear montage

When you are happy with your montage settings, we can begin browsing the data and sleep scoring!
