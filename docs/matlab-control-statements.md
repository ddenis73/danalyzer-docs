# Control statements

Control statements are an important part of MATLAB programming that you will use frequently when you are analyzing data. They essentially give you more flexible control over when and how code evaluates. There are only a few control statements, but it very important to have a good handle on how they work. All control statements follow the same basic anatomy:

```
<controltype><conditional>
	<content>
	<alternatives>
end
```
## If-then statements

Sometimes just called if statements, these are probably the easiest to understand of all the control statements. *if* this is the case, *then* do this:

```matlab

if 2 > 1
	disp('Big numbers are the best')
end
```

In an if statement, the conditional must return a single logical variable (i.e. true or false). If it does not, MATLAB will throw an error or *attempt* to inperpret the output of the statement as a logical. If the logical returns true, the *then* part of the statement (all the code between if and end) will be executed. if the logical returns false, no code will be run.

It is common practice to indent code that falls between if and end. If you highlight your code and press CTRL + I, MATLAB will automatically format this for you.

The above example only had one route to follow (is 2 greater than 1). You can add more alternative options using *elseif* and *else*:

```matlab

n = randn; % Randomly generate a single number

if n > 0
	disp('n is greater than 0')
elseif n > 2
	disp('n is greater than 2')
elseif n < 0 && n > -5
	disp('n is quite small')
else
	dip('n is very small')
end

```

The first statement tests whether n is greater than 0. If it is, it will print the statement 'n is greater than 0'. So what if n isn't greater than zero. Then, MATLAB will evaluate each elseif statement **in order**. This is very important, and also means that the code that is evaluated after the first elseif statement will never be evaluated. As soon as any of the if, elseif statements is evaulated true, the rest of the statements are always ignored. Because if n > 2, it will always be true at n > 0.

Let's take a look at the second *elseif* statement. This illurates that the conditional statement can have multiple elements. If you remember back to logical indexing, we used the *&* and *|* symbols for and and or operations. We can use the same here, except whenever we are evaulating a conditional statement, we need to use *&&* or *||*. We can string as many and or or statements as we want. As long as it evaluates to a single logical variable, MATLAB will be happy.

Finally we get the the *else* statement. An else statement just be for the *end* will capture anything that does not agree with any of the other statements. As such, you don't give an *else* statement any conditional to evaluate.

As well as logical operations, there are many functions you can use that return a logical variable that can be used as conditionals in an if-then statement:

```matlab

n = [];

if isempty(n)
	disp('n is empty')
elseif ~isempty(n)
	if n > (str2num(n))
		disp('n is greater than 0')
	else
		disp('n is not greater than 0')
	end
end

```

The funciton is empty returns true if the input variable is empty. Remember, if statements only evaluate if the conditional is true. So what if we wanted to do something if the variable *is not* empry. MATLAB recognises the ~ symbol to mean not, so placing it in front of the function means, in this case that *~isempty* translates as is-not-empty. This piece of code also illusrates how you can next multiple if-then statements within each other.

!!!question
	How else could you write the second conditional, instead of elseif ~isempty(n)?


## For-loop statements

Along with if statements, for-loops are the control statement you are going to be using the most. A for-loop is used to evaluate a piece of code over multiple iterations:

```matlab

for i = 1:10
	disp(num2str(i))
end

```

Here, the variable *i* is called the "looping variable", and it goes from 1 - 10 in integer steps. for loops iterate as many times as there are elements in the looping variable. The looping variable can be whatever you wish, it does not have to start at 1, and it does not need to be in integers. However, this is setup is useful as it is very common to use the looping variable within a for loop to index into matrices (and other variable types). For example:

```matlab

a = 2:2:10;

for i = 1:length(a)

	b(i) = a(i);

end

```

This for loop will loop a number of times = to the length of a. This is a very common setup for for loops. On each iteration of i, we will use the i to index into the ith position of a, and then assign that value to the ith position of b. 

!!! question
	What would happen if you wrote b = a(i); instead of b(i) = a(i)?

When you have this code in the editor you will notice matlab is giving us a warning message. If we hover over the squiggly orange line MATLAB tells us "The variable 'b' appears to change size on every loop iteration (within a script). Consider preallocating for speed". 

In our for loop, we are incrementally increasing the size of the variable b on each iteration. This can cause issues with memory use and processing speed, because MATLAB will need to spend longer sorting out information in memory. Preallocating can improve evaluation time by "reserving" the maximum amount of space for the variable ahead of time. To preallocate (or initialize) a variable, you just create the variable before the loop, setting it to be the size that the variable will be at the end of the loop. Not only does this make MATLAB more efficient, it forces you think more carefully about the expected output of your code ahead of time. For numeric variables, common ways to initialize a variable is to fill the variable with all zeros, or all NaN (not a number):

```matlab

a = 2:2:10;
b = zeros(1, 5); % Initialize with all zeros
b = nan(1, 5); % Initialize with all NaN

for i = 1:length(a)

	b(i) = a(i);

end

```

When writing data analysis scripts, if statements and for loops are going to be used frequently. Here are some general pieces of advice:

* **Avoid** using loops and if statements whenever possible. They are a great source of frustration and error, especially when there are multiple nested statements spanning hundreds of line. For loops are also slow. There are many cases where a for loop could be substituted for vectorized operations.
* Give looping variables an intuitive name. The letter i is often associated with looping variables. If you are looping across participants, calling the looping variable subi or sub_i makes it clear what is happening.
* Add a comment to each end statement to make it clear which statement it is ending.

Although if statements and for loops will be the control statements you use the most, some knowledge of the other three control statements available in MATLAB is valuable, and will be useful in certain situations.

## Try-catch statements

## While statements

## Switch-case statements