# Importing/exporting

In theory, MATLAB can work with almost any kind of input data, so long as you are able to figure out how to import it. We will talk specifically about importing EEG data in a later tutorial, but for now we will cover some basic principles about importing/exporting that will be important for your own MATLAB skills

## Loading and saving .mat files

A .mat file is the native MATLAB data format, and so is by far the easiest type of data to import:

```matlab

load matlabData.mat

```

This line will load the contents of the .mat file into MATLAB. A single .mat file can hold multiple variables. Don't forget that if the .mat file is not on the path, you will need to provide the full directory.

!!!question
	Use the whos command to figure out the number, size, and types of the variables that were just loaded

You can assign the contents of a .mat file to a variable of your own choosing:

```matlab

d = load(matlabData.mat);

```

In cases, such as this, where the .mat file holds multiple variables, those variables will become fields of a structure called d. Assigning data to variables this way will help to prevent data being overwritten if you load multiple .mat files containing the same variable names (for example if you are loading data from multiple participants). 

You can save variables in the MATLAB workspace to disk using the *save* command. if you simply type *save* into the Command Window, matlab will save the entire contents of the workspace to a variable called matlab.mat. Usually you want to be more selectively than that:

```matlab

save('output_filename.mat', 'var1', 'var2', 'var3')

```

This code will save a .mat file called output_filename, and in that .mat file will be the variables *var1*, *var2*, *var3*. Note that both the file name and all of the variables you wish to save must be inside single quotation marks. 

It is generally advisable to keep .mat files as small as possible, and within a single analysis/study to use a consistent file naming structure to keep things neat and tidy. When we start working with real data, you will find that sleep scores, artifact rejection information, and spectral analysis output will all be saved as .mat files.

## readtable/writetable

Data in a tabular format (e.g. csv, Excel, and potentially text files) can be easily imported into matlab using the *readtable* function. This function will import the data into a table variable, with the column names corresponding to the column names in the imported file:

```matlab

t = readtable('exampleTable.csv', 'ReadVariableNames', true);

```

Note the input argument 'ReadVariableNames'. This is an example of a *key-value* function input. It works by specififying the type of input you are requesting (i.e. the key, in this example ReadVariableNames), followed by the value for that input argument (i.e. the value). Here we are telling the function to use the first row of the table as variable names.

If you have a table variable, you can easily write it to a .csv or Excel file by using writetable:

```matlab

writetable(t, 'newTable.csv', 'WriteVariableNames', true);

```
The syntax for writetable is very similar to readtable. The first input is the table variable we want to save, and the second input is the name of the table. If you just specify the name, MATLAB will save the table to the current directory. If you want to save it someplace else, you will need to specify the full directory. The key-value input *WriteVariableNames* works how you imagine. This input is instructing MATLAB to include column names on the first row of the exported table.

## Loading text files

The *load* and *readtable* commands work great with clean, easy to import data. For example, if a text file contains only numbers and each row has the same number of columns, the *load* command can handle it no problem:

```matlab

load('easy_text_file.txt')

```

Things are rarely this easy though. If each row contains a different number of columns, or if there is a mixture of numbers and strings, you are going to quickly run into problems. In these kinds of situations, you are going to need to use the *fread* set of functions. This will give you maximum control of your data import, although can have a bit of a steep learning curve. As a first step, open *hard_text_file.txt* to get a sense of what we are dealing with. There are several ways of importing this data, but the easiest thing to do is read it in line-by-line. Below is the code to achieve this:

```matlab

fid = fopen([subList(sub_i).folder filesep subList(sub_i).name]);
d = [];
tline = fgetl(fid);
i = 1;

	while ischar(tline)
		d = strsplit(tline, {'\t' ' '});
        	
        	if length(d) < 12
            	d(length(d)+1:12) = {' '};
        	end
        	
        data(i,:) = d;
        tline = fgetl(fid);
        i = i+1;
    end
    
fclose(fid);
```
