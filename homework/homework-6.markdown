---
title: Homework 6
layout: default
---

Skills needed to complete this assignment:

- [Arrays](/lecture/arrays.html)

Practice using arrays by completing the following tasks. Create one class and one `main` function. Your `main` function must have code that tests all your other functions.

## Task 1

Write a loop in your `main` function that asks the user for a list of cities (100 or fewer). The user types a blank line (just presses enter) when done entering cities. Then print out all the cities entered, in the order entered. Only print the values they entered, and not the blank value(s).

## Task 2

Write a loop in your `main` function that asks the user for a list of positive integers (100 or fewer). The user types 0 when done entering integers. Then ask the user to type another integer. Finally, print "Found" if that last integer was among those entered previously, or "Not found" if not.

Use a function from the `Arrays` class to perform the search.

## Task 3

Create a function called `median` that finds and returns the median value of an array of `double`. The median is the middle value, after sorting the array. If there are an even number of elements in the array, it's the average (mean) of the two middle values.

Add a test case to your `main` function that computes the median of some array.

Use a function from the `Arrays` class to sort the array.

## Task 4

Create a function called `correlation` that finds and returns the statistical correlation between two arrays `xs` and `ys` of type `double`. Assume each array has the same number of values. Use this formula to calculate the correlation:

```
cor = sum[ (xi - mean(xs))*(yi - mean(ys)) ] / ((n - 1) * sd(xs) * sd(ys))
```

where `xi` means the value in `xs` at index `i` (in Java: `xs[i]`), the `mean` and `sd` (standard deviation) functions are defined in the [array notes](/lecture/arrays.html), and `n` is the number of values in the arrays (they have the same number of values).

The correlation of two arrays is the general agreement in their values. Correlations are between -1 and 1. A correlation near -1 means as x-values increase, y-values decrease (inverse correlation). A correlation of about 0 means the x and y values seem to have no relation. A correlation near 1 means as x-values increase, y-values increase likewise (positive correlation).

For example, consider the relation between amount of wind in New York City in miles-per-hour, and temperature in degrees F:

```
double[] wind = {7.4, 8.0, 12.6, 11.5, 14.3, 14.9, 8.6, 13.8, 20.1, 8.6,
                 6.9, 9.7, 9.2, 10.9, 13.2, 11.5, 12.0, 18.4 11.5, 9.7};

double[] temp = {67, 72, 74, 62, 66, 65, 59, 61, 74, 69, 66, 68, 58, 64,
                 66, 57, 68, 62, 59, 73};
```

Their correlation should be about -0.63, meaning if there is more wind, the temperature generally decreases.

This is what the points look like, if you're curious:

![Plot of airquality](/images/plot-airquality.png)

