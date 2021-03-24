# Scorer reliability

Inter-rater reliability of two sleep scorers can be calculate within the GUI. Both scorers must have scored the record independently in danalyzer, and each saved a score file. Typically there will be the scorer file of the new scorer (the trainee) whose sleep staging needs to be compared to a expert scorer. To begin, load the datafile and the score file *of the trainee* into danalyzer.

With these loaded, we are then going to overlay the master score file, and calculate reliability between the two. To overlay the master file, go File --> Import --> Sleep scores --> danalyzer. Navigate to the master score file and click Open. Then a dialog box will open asking if you want to Overlay the two score files, or Replace the existing score file with the new one. Make sure to click the Overlay option.

You should now see the two hypnograms overlaid on top of each other in the hypnogram window. In this view, you can jump to epochs where the two score files don't align to discuss discrepencies. You caclulate reliability, navigate to Sleep Statistics --> Compare scorers. Enter a name for the reliability file, and click Save. A reliability report will automatically appear, which displays the two hypnograms overlaid on each other, as well as an agreement table, percent agreement for each sleep stage, and an overall kappa rating.

!!!tip
	Scorer reliability can be performed using the function *fun_scorer_reliability* in a MATLAB script