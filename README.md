# Pair programming club - 6th October 2022

The file `grades.txt` contains the grades (out of 100) obtained by 300 students on a course, on 4 different assignments. Your task this week is to read this data into a NumPy array, to plot some useful visualisations, and to write a short `.txt` file to report some interesting statistics about the class.

As usual, the **driver** starts by sharing their screen, creating the team repo on GitHub, and cloning the repo. Don't forget to **switch roles every 15 minutes or so**, or whenever you complete a sub-task if that feels more natural. **Both of you should take on the driver role at least once.**

This week, you will need to **consult the documentation** to find out how to do some of the tasks -- this is a great job for the **navigator**.

## Task 1: read the data into a NumPy array

Your first job is to read the data from the file `grades.txt` into a NumPy array -- to do this, we can actually use one of NumPy's functions, `loadtxt`.

There are already a couple of lines of code in `analyse_grades.py`, but if you try to run it, you'll see an error. Debug it together! Here are some clues:

- Look inside the text file. What does the data look like?
- Read the error trace. What is the type of the error? What does the error message suggest?
- Look at the [documentation for the `loadtxt` function](https://numpy.org/doc/stable/reference/generated/numpy.loadtxt.html?highlight=loadtxt#numpy.loadtxt). Is there something you can use there to fix the bug?

## Task 2: make some plots!

Now, all the grades should be in a NumPy array, with each row corresponding to a student and each column to an assignment. To get a general view of the class' results, for example, we could plot some histograms.

- Search the matplotlib documentation to find out how to plot histograms -- it's available at [matplotlib.org](https://matplotlib.org/). Remember that you can use your favourite search engine to search the documentation -- for example, you could search Google for `histogram site:matplotlib.org`.
- Plot a histogram of the grades for **each** assignment (each column in the data). This will tell you how many students in the class got a certain grade, for all 4 assignments.
    - You will need to produce 4 histograms. Search for "subplot" in the documentation for how to do this.
    - Your bins (the x-axis) should start at 0 and end at 100.
    - You could choose to plot this either by grade band (that is, every bin has width 10, for example group students who got between 60 and 69) or by individual grade (one bin per integer between 0 and 100).

### Hints:

```python
# Get the entire third column of the "grades" array
grades[:, 2]

# Get the entire 50th row of the "grades" array
grades[49, :]
```

## Task 3: write a report

Finally, have a look at [NumPy's statistics functions](https://numpy.org/doc/stable/reference/routines.statistics.html), and compute some useful statistics for your class. Again, some suggestions -- but feel free to go further if you have time:

- What are the average and median grades for each assignment?
- How many students got an A for each assignment (grade 70 or greater)? 
- How many students got an A for **all 4 assignments**?

Then, report these statistics by writing them to a `.txt` file called `stats.txt`, using the function `open()`. As for everything else, if you don't know how to use it, you can consult the documentation.

You can use **f-strings** ([documentation](https://docs.python.org/3/tutorial/inputoutput.html#tut-f-strings)) to format your results and make the report more readable. For example, if you've stored the average grades for each assignment in a list `averages`, you could create a string to write in your file:

```python
average_report = f'The average grade for Assignment 1 was {averages[0]:.1f}.'
```
and use `.write()` to write that line in your file. (Don't forget `\n` where necessary!)

### Hints:

This is a minimum working example which creates a file `my_new_file.txt` in the current folder, and writes 2 lines of text inside it. Try it!

```python
name = 'Charlotte'
age = 78

with open('my_new_file.txt', 'w') as myfile:
    myfile.write(f'My name is {name}.')
    myfile.write(f'I am {age} years old.')
```

## Some extra questions, if you have time...

- Find a way to display the 4 histograms on 1 graph, with 4 different bars for each bin, each bar with a different colour. Add a legend to indicate which colour corresponds to which assignment.

- If you can think of other ways to display this data, which would give you more information, try it! (matplotlib can do boxplots, for example.)

- How many students have passed the course (grade 50 or greater overall)? How many students got a distinction (grade 70 or higher)? How many students will be allowed to take a resit exam (grade between 30 and 49)? The weights for each assignment are as follows:
    - Assignment 1 counts for 10% of the grade.
    - Assignment 2 counts for 25% of the grade.
    - Assignment 3 counts for 15% of the grade.
    - Assignment 4 counts for 50% of the grade.
