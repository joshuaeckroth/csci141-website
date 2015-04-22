---
title: Homework 13
layout: default
---

The final exam covers:

- [Functions](/lecture/functions.html)
- [Arrays](/lecture/arrays.html)
- [Classes](/lecture/classes.html)
- [Exceptions](/lecture/exceptions.html)
- [Files](/lecture/files.html)
- [Inheritance](/lecture/inheritance.html)
- [Interfaces](/lecture/interfaces.html)
- [Swing](/lecture/swing.html)

**You may refer to this website and the [Java docs](http://docs.oracle.com/javase/7/docs/api/allclasses-noframe.html) during the Final exam. It is an "open notes" exam.**

## Final review

### Functions

Write a function that takes an integer as input and returns the smallest integer greater than one that divides it.

Make use of the `Math.floor()` method, as described below. Give it an argument such that the return value is `13.0`.

> `public static double floor(double a)`
>
> Returns the largest double value that is less than or equal to the argument and is equal to a mathematical integer. Special case:
> 
> - If the argument value is already equal to a mathematical integer, then the result is the same as the argument. 

### Arrays

Add all the odd values (not odd positions) in an `int` array called `vals`. Print the final sum.

Copy an array `xs` (of type `double`) into an array `ys` (type `double`) in reverse. Both arrays are the same size. The first element if `ys` should be the last of `xs`, etc. *Do not create these arrays; they already exist! You do not know their size. Do not create a function. Just copy the values.*

Create a function that takes a `double` array as input and another `double` value. The function makes a copy of the array and adds the second value to all elements in the copied array, and returns the copied array.

### Classes

Create a class representing rational numbers (fractions), called `Rational`. It should have a numerator and denominator (integers). It should have setters/getters and a constructor. Its `toString` should return a string like `5/2`.

Create the full class for the UML below. Do not create any methods not listed. Use a tax rate of 7%, so that `getPriceWithTax()` returns `price * 1.07`.

![OrderItem](/images/orderitem.png)

### Inheritance

Create a template for each of the classes in this UML diagram:

![Persons, students, etc.](/images/person-faculty-staff.png)

indicate which fields/methods are inherited (from one level)

indicate which fields/methods are inherited (from two levels)

create a new method such that polymorphism works

### Interfaces

write a class template that "implements" some given interface

### Swing

recreate a certain layout

create a button that responds to events

create a custom drawing panel

