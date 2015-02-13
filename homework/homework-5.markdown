---
title: Homework 5
layout: default
---

Skills needed to complete this assignment:

- [Functions](/lecture/functions.html)

## Task 1

Write a function that prints one line of the bottles-of-beer song, and code in the `main()` function to use the beer function to print the whole song. The beer function should have an integer parameter indicating the number of bottles on the wall. Be sure to handle the last line of the song correctly.

## Task 2

Write a function that determines if a given number is a prime number, and returns true/false. The number to check on should be a parameter. Then write code in `main()` that asks the user for a number, and tells the user if it is prime or not, using the prime function you created.

## Task 3

Write a function that calculates the number of days in a given month. Use the code from the [conditionals](/lecture/conditionals.html) notes (search for "numDays"). Also, in the `main()` function, write a loop that prints the number of days for each month 1-12, using your function.

## Task 4

Write a function that computes PI using this sequence:

```
PI = 4 * (1 - 1/3 + 1/5 - 1/7 + 1/9 - 1/11 + 1/13 - 1/15 + ...)
```

The function should have one parameter that indicates how far to go in the sequence (if you stop at 1/15, that's 8 steps). Your function should return the result.

Then, in your `main()` function, execute this function and show the user the output. Also show the user the builtin value `Math.PI`, so the user can visually compare the two estimates.