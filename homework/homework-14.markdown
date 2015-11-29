---
title: Homework 14
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

Make use of the `Math.floor()` method, as described below. You do not need to import Math, you can just refer to the method directly. Give it an argument such that the return value is `13.0`.

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

Create a template for each of the classes in the UML diagram below. Use Eclipse to generate getters/setters/toString and constructors for each class.

![Persons, students, etc.](/images/person-faculty-staff.png)

Given these classes, list the private and public fields and methods in the class `Baz` (take note of which public fields/methods are inherited).

{% highlight java %}
public class Foo {
  public int x;
  private int y;
  public void a();
  private void b();
}

public class Bar extends Foo {
  public int z;   private void c();
}

public class Baz extends Bar {
  private int w;
  private int v;
  public int u;
  public void d();
  private void e();
}
{% endhighlight %}

Given the code below, what happens when `x.speak()` is executed? Take note of polymorphism.

{% highlight java %}
public class A {
  public void speak() {
    System.out.println("Waaah");
  }
}

public class B extends A {
  public void speak() {
    System.out.println("Hello dear.");
  }
}

public class Main {
  public static void main(String[] args) {
    A x = new B();
    x.speak();
  }
}
{% endhighlight %}

### Interfaces

Given the interface below, create a class template (just an outline, no code for any methods) that implements the interface.

{% highlight java %}
public interface Collection {
  void add();
  void remove();
  boolean hasItem(Object item);
}
{% endhighlight %}

### Swing

Recreate this layout:

![Swing layout](/images/swing-layout-final-review.png)

Create a simple GUI with a single button that changes the button text (to whatever, using `setText()`) when it's clicked.

### Exceptions

Write a chunk of code that creates a `Scanner` and calls `nextInt()`, but which also handles the possible `InputMismatchException`. If the exception occurs, the code should print "Invalid integer."

Write a static `getInput()` method that can throw a new exception when the input is invalid. Use a `Scanner` in the method. Ask the user for question using `nextLine()`. Throw an exception if the user input does not contain a question mark. Use the condition `if(mystr.indexOf("?") == -1)` to check if the string `mystr` does not contain a question mark.

### Files

Write a static method `boolean saveArray(Object[] arr, String filename)` that saves every value in the array `arr` to a file indicated by `filename`. Since every value in the array is an `Object` (which is the parent class of every other Java class), you can use `toString()` on each value. Separate the values in the file by a newline. Return `true` if the process worked (no exceptions), return `false` otherwise. Do not allow exceptions to be thrown out of the function.

Write a static method `int[] readIntegers(String filename)` that reads a list of integers from a file. The first number in the file will be the number of integers that follow. Integers in the file are separated by spaces or newlines, so the `nextInt()` function on `Scanner` will suffice. Return an array containing the integers. Do not allow exceptions to be thrown out of the method.

