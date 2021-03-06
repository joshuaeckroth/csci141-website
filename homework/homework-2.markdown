---
title: Homework 2
layout: default
---

Skills needed to complete this assignment:

- [Variables, types, scope](/lecture/variables-types-scope.html)
- [Simple input/output](/lecture/simple-io.html)
- [Conditionals](/lecture/conditionals.html)
- [Loops](/lecture/loops.html)

## Task 1

This task is borrowed from [Project Euler Problem 5](https://projecteuler.net/problem=5)

2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder ("evenly divided").

Create a program that prints the smallest positive number that is **evenly** divisible by all of the numbers from 1 to 20.

Note: You can check your answer on the Project Euler site if you make a free account.

## Task 2

Write a program that scores a blackjack hand, repeatedly, until the user types 0. In blackjack, a player receives from two to five cards. The cards 2 through 10 are scored as 2 through 10 points each. The face cards - jack, queen, and king - are scored as 10 points. The goal is to come as close to a score of 21 as possible without going over 21. Hence, any score over 21 is called "busted." The ace can count as either 1 or 11, whichever is better for the user. For example, an ace and a 10 can be scored as either 11 or 21. Since 21 is a better score, this hand is scored as 21. An ace and two 8s can be scored as either 17 or 27. Since 27 is a "busted" score, this hand is scored as 17.

The user is asked how many cards she or he has, and the user responds with one of the integers 0, 2, 3, 4, or 5. If the user types 0, the program quits. Otherwise, the user is then asked for the card values. Card values are 2 through 10, jack, queen, king, and ace. A good way to handle input is to use the type `String` so that the card input 2, for example, is read as `"2"`, rather than as the number 2. Input the values 2 through 9 as the strings `"2"` through `"9"`. Input the values 10, jack, queen, king, and ace as the strings `"t"`, `"j"`, `"q"`, `"k"`, and `"a"`. (Of course, the user does not type the quotes.) Be sure to allow upper as well as lowercase letters as input. You can assume the user provides correct input (so you do not have to check for bogus inputs like `"z"` or whatever).

After reading in the values, the program should convert them from character values to numeric card scores, taking special care for aces. The output is either a number between 2 and 21 (inclusive) or the word "Busted." Then the program repeats and asks the user for the number of cards again.

I suggest you use a `switch` statement for the various conditions, e.g.,

{% highlight java %}
String s;
// get symbol from user, save into s
switch(s)
{
    case "t": case "T":
        score += 10;
        break;
    case "2":
        score += 2;
        break;
    // etc.
}
{% endhighlight %}

## Extra credit

This task is borrowed from [Project Euler](https://projecteuler.net/problem=12).

The sequence of triangle numbers is generated by adding the natural numbers. So the 7th triangle number would be 1 + 2 + 3 + 4 + 5 + 6 + 7 = 28. The first ten terms would be:

```
1, 3, 6, 10, 15, 21, 28, 36, 45, 55, ...
```

Let us list the factors of the first seven triangle numbers:

```
 1: 1
 3: 1,3
 6: 1,2,3,6
10: 1,2,5,10
15: 1,3,5,15
21: 1,3,7,21
28: 1,2,4,7,14,28
```

We can see that 28 is the first triangle number to have over five divisors.

Create a program that calculates and prints the value of the first triangle number to have over five hundred divisors.