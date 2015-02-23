---
title: Homework 7
layout: default
---

Skills needed to complete this assignment:

- [Arrays](/lecture/arrays.html)

## Task 1

Create a x/y scatter plot program, using Processing and a small library I wrote called `CSVReader`.

### Initial step

Download [CSVReader.jar](/CSVReader.jar) and add as an "External JAR" to your project's "Java Build Path", just like we did with processing.jar in the [Processing notes](/lecture/processing-library.html). Use `import csci141.CSVReader;` at the top of your file.

Data for plotting will come from a CSV file (comma-separated values). You can download two example files: [sine.csv](/homework/sine.csv) and [faithful.csv](/homework/faithful.csv). You can edit these files in Microsoft Excel or Notepad or Eclipse.

### Requirements

The program should work as follows:

- In `setup()`, ask for user input, like shown:

```
Enter CSV filename: sine.csv
Enter x column name: radians
Enter y column name: sine
```

- Then read data in the file with the following code, using my `CSVReader` library:

{% highlight java %}
CSVReader.readCSV(filename);
xs = CSVReader.getColumn(xcol);
ys = CSVReader.getColumn(ycol);
{% endhighlight %}

`filename` and `xcol` and `ycol` should be `String` variables (with values obtained from the user). `xs` and `ys` should be `float` arrays, declared at the top of the "class".

- In `draw()`, plot the data points (see example below). You should show all the points within a box shown on the screen. Obviously, the actual data from the CSV file may have big or small or even negative values. You need to scale these values and shown them all within the box.

- Also add the `xcol` column name on the left and the `ycol` column name on the bottom.

- Also show the min value and max value for the x and y axes.

### Example display

#### sine.csv

![Plotter sine](/images/plotter-sine.png)

#### faithful.csv

![Plotter faithful](/images/plotter-faithful.png)

## Extra credit 1

Create a histogram for just the `xcol` column. Of course, you can specify any column from the CSV file to be the `xcol`. Ask the user for the number of bars to show. Determine the size of each bar by dividing the total range of values by the number of bars.

## Extra credit 2

Create a 3D scatterplot for x, y, z columns. Even better: allow the user to rotate the plot.
