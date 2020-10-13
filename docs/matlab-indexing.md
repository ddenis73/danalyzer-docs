# Indexing

When you have very large arrays, you are often only going to want to access a part of it. Indexing is the way to this, and is a critical skill to learn. This section will show you the basics of indexing the various kinds of variables we learned about previously. We will also introduce the concept of *logical indexing* and how it can be used to find parts of a variable that meet a certain criteria. 

The best way to get a complete feel of how indexing works is to practice, practice, practice!

## The colon operator

To start, we will create a large array:

```matlab

% Create a large array

bigArray = 1:2:200;

```

Before we learn about indexing, we should talk briefly about the colon operator. The colon operator essentially acts as automatic number calculator:

```matlab

1:10

```

If you run that in the command window, you will see the use of the colon has counted from 1 to 10 in steps of 1. You can count in steps other than 1:

```matlab

1:2:10

```

By adding the middle number, this tells MATLAB what to count in i.e. count from 1 to 10 in steps of 2. Notice how when you do this, the output stops at 9 and not 11. You can concatenate numbers defined using the colon operator and single values by enclosing them in square brackets to form an array:

```matlab

[1:2:5 8 1:1:10]

```

As we will see below, the colon operator comes in very handy when indexing multiple elements

## Indexing numeric variables

Indexing lets us access specific parts of a variable. In the case of *bigArray* which we defined at the top, let's say we want to know the value of the number in the tenth position. We simply do this using parentheses *()*:

```matlab

% Index the tenth element of bigArray

bigArray(10)
```

In the command window, MATLAB prints out the value. If we wanted to store that output, we could assign the output of the indexing to a new variable:

```matlab

resultOfIndex = bigArray(10);

```

By using square brackets inside the parentheses you can index multiple elements:

```matlab

bigArray([1 2 3 4 5 10 17 24])
```

We can save ourselves a bit of work here and use the colon operator to specify element 1:5, rather than typing each number out separately:

```matlab

bigArray([1:5 10 17 24])

```
When you are working with multidimensional arrays, use a comma to separate each dimension. For example, if you wanted to index the first row and tenth column of a 2D matrix:

```matlab

% Make a 2D matrix

biggerArray = [1:2:100; 1:1:100];

biggerArray(1, 10)

```

!!! tip
	If you index just one dimension of a matrix, MATLAB will always start from row 1. So:

	```
	biggerArray(1)
	```

	will index row 1, column 1. If you were to write:

	```
	biggerArray(2)
	```

	MATLAB will index row 2 column 1. When a single dimension is indexed in a 2D matrix, MATLAB will move through each row first, before advancing to the next column. This same principle applies when working with higher dimensions matrices as well.

If you type just a colon by itself, the result would be to index every element in that dimension:

```matlab

% Index every element in the first row

biggerArray(1, :)

```

If you index a position that is outside of the dimensions of the variable, MATLAB gets upset and throws an error:

```matlab

% Index element 1 in row 3

biggerArray(3, 1)

```
```matlab

Index exceeds array bounds.

```

This is a common error to see as you start writing more and more complex scripts. These errors often arrive when a variable you are creating is not the size you expect to be.

## Indexing character variables

You can index a character array in the exact same way you index numeric variables:

```matlab

charArray = 'The quick brown fox jumped over the lazy dog';

% Index the 5th-9th characters

charArray(5:9)

% Use square brackets to access multiple elements

charArray([1:3 5:9 42:44])


``` 

!!! question
	Try assigning "the quick brown fox jumped over the lazy dog" as a string array instead of a character array. Then try to index elements 5:9. What happens? What does this tell you about the difference between character and string arrays?


## Indexing cell arrays

The same concept applies to indexing cell arrays, but there is an important difference between using parentheses *()* and curley brackets *{}*:

```matlab

% Make a 2D cell

bigCell = {[2 3 4 1] [1 2 7 6 5] 'words'; [1 2 0] [6 5 7 1 3 6] 1};

% Index using parentheses

bigCell(1)

% Index using curly brackets

bigCell{1}

```
``` matlab

bigCell(1)

ans =

  1×1 cell array

    {1×4 double}

bigCell{1}

ans =

     2     3     4     1

```

This clearly gives us quite different results. What is going on here? When you use the the parentheses, it is giving you the element present in position 1. In this case that is a cell containing a numeric array. That is why the output is a 1x1 cell array containing a 1x4 numeric array.

If we want to access the contents of the cell in position 1, we need to use the curly brackets to get at what is inside the cell. Once we are inside the cell, we can then index the numeric variable inside:

```matlab

% Index first three elements of the array inside the cell

bigCell{1}(1:3)


```

!!! question
	Based on this, how would you index the second letter of the character array in bigCell?

## Indexing structures

As with other variables, you can index elements of a structure using parentheses. Let's create a structure with three entries, similar to what we might have after detecting sleep spindles:

```matlab

% Create a structure

spindles(1).label = 'Fz';
spindles(1).density = 4.1;
spindles(1).amplitude = 28;

spindles(2).label = 'Cz';
spindles(2).density = 4.8;
spindles(2).amplitude = 24;

spindles(3).label = 'Pz';
spindles(3).density = 5.2;
spindles(3).amplitude = 17;

```

We can access any of the entries in the structure using parentheses like we would for any other variable type:

```matlab

spindles(1)

```
```matlab
ans = 

  struct with fields:

        label: 'Fz'
      density: 4.1000
    amplitude: 28

```

This gives us the content of each field in the first entry. This can easily be extended to retrieve the content of a specific field:

```matlab

spindles(1).density

```
```matlab

ans =

    4.1000

```

So what if you wanted to access multiple entries? If you write:

```matlab

spindles([1 3]).density

```

you will notice that MATLAB returns each element as a separate answer, one for each entry in the strucutre. To concatenate the output of a structure, use square or curly brackets:

```matlab

[spindles([1 3]).density]

```

!!! question
	Try the line above again, this time for the label field. Try using both square and curly brackets to concatenate the output. What are differences? When might one be more useful than the other?


## Indexing tables

There are two different ways to index a table. First, lets start by creating one:

```matlab

bigTable = table(["ppt1"; "ppt2"; "ppt3"], [4.6; 6.1; 2.3], [30; 50; 17],... 
    'VariableNames', {'subid', 'spindles', 'memory'});

```

!!! tip
	What are the meaning of those three dots (ellipsis) at the end of the first line? This is how you can get MATLAB to continue long statements across multiple lines. This comes in very handy when performing particularly long operations.

We can index a specific element or set of values by using parentheses or curly brackets. The difference is conceptually similar to that of cell arrays. Using parentheses will always return a table element, whereas curly brackets will give you what is "inside" that table table element:

```matlab

% Index using parentheses

bigTable(1, 2)

% Index using curly brackets

bigTable{1, 2}

```
```matlab

bigTable(1, 2)

ans =

  table

    spindles
    ________

      4.6   

bigTable{1, 2}

ans =

    4.6000

```

Unlike other kinds of variable, when indexing a table you *must* specify a value for both dimensions of a table (i.e) a row and a column. A second way to index a table is by using the column names and a the period key:

```matlab

bigTable.spindles

```

This looks similar to what we were doing with structure arrays. However, unlike a structure, when you index a table variable it concatenates all of the elements in the output for you. You can index a particular row(s) based on a column name using parentheses:

```matlab

bigTable.spindles(1)

```

This will give you the first row of the column labeled spindles.

## Logical indexing

What if we don't want to access elements in a particular location, but want to access elements that fit a certain set of criteria? By combining our new knoledge of indexing with *logical variables* that we learned about earlier, we can perform logical indexing. Logical indexing works by providing a statement which MATLAB can evaluate for each element in the variable we are indexing, and return only those elements who returned true to the statement. For example:

```matlab

a = 1:5;
a([true true false true false])

```
```
ans =

     1     2     4
```

This returns only elements 1, 2, and 4, because logical indexing accessed those elements. This is what happens when we use logical operators to find elements that fit a critera. For example, if we wanted to all the elements in that array that were greater than 3:

```matlab

a > 3

```
```
ans =

  1×5 logical array

   0   0   0   1   1
```

This statement returns a logical array with the length of a. As expected, only elements 4 and 5 returned true because they were greater than three. So to get those elements directly we would write:

```matlab

a(a > 3)

```
``` matlab
ans =

     4     5

```

This is the logic behind logical indexing. Any operator or function that returns as a logical variable can be used in logical indexing. As you gain more experience with MATLAB, you will start to realize just how creative you can be with logical indexing!

!!! question
	Try experimenting with the other logical operators. How does the operation >= differ from >?

What if you wanted to only index elements that fitted two criteria. It is possible to combine different logical operations using two new commands, the & and | operators. The & operator is used when you want to index elements who return true to *all* the logical operators. The | works as an or operator. Use this when you want to index elements who return true to any of the logical operators.

```matlab

% Index elements who are greater than 2 AND less than 4

a(a > 2 & a < 4)

% Index elements who are less than 2 OR greater than 4

a(a < 2 | a > 4)

```

