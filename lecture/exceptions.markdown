---
title: Exceptions
layout: default
---

So far, we have avoided handling most errors our programs could encounter. Instead, we just let the program crash. Here are some examples of errors.

## Examples of errors

### `Scanner` inputs: wrong input format

E.g., suppose you have a `Scanner` like so:

{% highlight java %}
Scanner in = new Scanner(System.in);
{% endhighlight %}

And you ask the user for an integer:

{% highlight java %}
System.out.println("Enter a number: ");
int n = in.nextInt();
{% endhighlight %}

If the user does not type a number, the program will crash.

### Creating an array with a bogus (negative) size

This code crashes your program:

{% highlight java %}
double[] vals = new double[-5];
{% endhighlight %}

### Using an invalid array index

This code crashes your program:

{% highlight java %}
double[] vals = new vals[10];
vals[22] = 5.5;  // 22 is a bad array position
{% endhighlight %}

### Dividing by zero (integers)

This code crashes your program:

{% highlight java %}
int x = 5;
int y = 10 / (x-5);  // that's 10/0 !!
{% endhighlight %}

### Custom functions

We also defined some functions that handled errors very poorly. For example, `sumArrays` from [Test 2 (Spring 2015)](/CSCI 141 Test 2 - Spring 2015.pdf) was supposed to print a message if the two arrays were not equal length.

{% highlight java %}
public static double[] sumArrays(double[] xs, double[] ys)
{
  if(xs.length != ys.length)
  {
    System.out.println("Error: unequal lengths.");
    return xs;  // return something silly, because we have to
  }
  else
  { ... }
}
{% endhighlight %}

Note, we were still required to return an array value since our function promised it would. But we really didn't want to.

Also, our bank account class in [Homework 8](/homework/homework-8.html) (task 3) was not supposed to allow negative withdrawals or deposits, and was not supposed to allow withdrawing more money than exists in the account. Rather than "doing nothing" in these situations, which was our solution at the time, we really should produce a kind of error that other could would be forced to handle.

## Exceptions are for handling errors

