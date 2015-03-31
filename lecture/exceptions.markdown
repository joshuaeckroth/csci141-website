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

<p>
<img src="/images/referee-flag.jpg" align="right" style="margin: 0 0 10px 10px;"> An exception is a kind of error that halts execution and must be dealt with. If an exception is not dealt with, the program crashes. They are like a penalty flag: everything stops, and something must be done about it.
</p>

For example,

{% highlight java %}
Scanner in = new Scanner(System.in);
System.out.println("Enter a number: ");
int n = in.nextInt();
// user enters 'x' (not an integer)
// EXCEPTION THROWN; CODE BELOW NEVER HAPPENS
System.out.println("Thanks for typing the number: " + n);
{% endhighlight %}

## `try`/`catch`

When an exception is thrown, it must be handled, or your program will crash. This is accomplished by a `try/catch` block, where the `catch` indicates which kind of exception is handled:

{% highlight java %}
try {
  Scanner in = new Scanner(System.in);
  System.out.println("Enter a number: ");
  int n = in.nextInt();
  System.out.println("Thanks for typing the number: " + n);
}
catch(InputMismatchException e)
{
  System.out.println("You're bad! You didn't enter an integer!");
}
{% endhighlight %}

You can catch multiple types of exceptions. The first "`catch` block" to match is the one that's executed.

## `throws`, and `throw`'ing your own exceptions

You may choose *not* to handle certain exceptions. In this case, your method must indicate it also `throws` exceptions.

{% highlight java %}
public int askUserForInteger() throws InputMismatchException
{
  // Scanner code as above, except no try/catch
}
{% endhighlight %}

Now, `InputMismatchException` is a "checked" exception that does not need to be explicitly stated in a `throws` statement. However, you can also throw your own exceptions:

{% highlight java %}
public double[] sumArrays(double[] xs, double[] ys) throws Exception
{
  if(xs.length != ys.length)
  {
    throw new Exception("Array lengths not equal!");
  }
  else
  { ... }
}
{% endhighlight %}

An exception will propagate up the various methods that you called until some piece of code "catches" it. If no such code exists, the exception crashes the program.

## Kinds of exceptions

Here is a table of common kinds of exceptions.

| Code | Possible exception types (only likely ones are listed) |
| ---- | ------------------------ |
| `Scanner`: `nextInt`, `nextDouble`, etc. | `InputMismatchException` |
| Array usage | `ArrayIndexOutOfBoundsException`, `NegativeSizeArrayException` |
| String usage | `StringIndexOutOfBoundsException` |
| Object usage | `NullPointerException` |
| Arithmetic | `ArithmeticException` |

Note, you do not have to `catch` every exception separately, you can exploit the exception hierarchy (see image below) and just catch a parent type. The class `Exception` is the ancestor of all exception types; catching `Exception` will catch any exception.


![Exception hierarchy](/images/exception-hierarchy.png)

Image from: [Learning Java, by Patrick Niemeyer 
and Daniel Leuck, 4th edition](http://chimera.labs.oreilly.com/books/1234000001805/ch04.html#learnjava3-CHP-4-SECT-5.3).
