# Sleep statistics

Sleep statistics can be calculated within the GUI. This will save the data to a file, and will also automatically produce a basic sleep report in .html format. See an example report [here]('../docs/example_sleep_report.html').

!!!tip
	In general, it is better to calculate sleep statistics by calling the *fun_sleep_statistics* command as part of a batch MATLAB script to process multiple score files at once

When you get to the end of a record, click on Sleep Statistics --> Calculate sleep statistics. This will open up a dialogue box where you can set the rule for determining sleep onset. If you want to add a spectogram to the report, you can enter the name of a channel you wish to use. Choose where to save the data by either typing in a directory or pressing the push button next to Save location. If you use the push button, this will let you select a destination and name for the sleep statistics file. Navigate to the folder you wish to save to, and give the file a name. Then click save. Then, in the Sleep statistics dialogue, click the green Save button to produce the report and save the sleep statistics.

!!!bug
	When creating the spectogram, if the last epoch of data is very short (shorter than 5 seconds), danalyzer will throw an error. This is because the length of the data in the final epoch is shorter than the length of the Hamming window used to create the spectogram. This bug will be fixed in a later version. For now, spectograms can be made using a MATLAB script.
