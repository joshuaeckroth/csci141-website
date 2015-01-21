---
title: Loops
layout: default
---

## `while` loop

The `while` loop is the simplest loop there is. In the `()` after `while`, you write some kind of expression that evaluates to a boolean (`true` or `false`). The expression may be just a (boolean) variable, or something more complicated. The body of the loop, which exists between the `{` and `}`, will execute over-and-over until the expression in the `()` turns out to be `false`. The boolean expression may be `false` before the loop even begins, in which case it will not loop at all. If the expression starts `true` but never turns `false`, the loop will repeat forever (unless there is a `break` inside).

{% highlight java %}
while(...some boolean expression...)
{
  // dooo stuff
}
{% endhighlight %}

Here is a loop that prints the numbers 1 through 15.

{% highlight java %}
int x = 1;
while(x <= 15)
{
    System.out.println(x);
    x++;
}
{% endhighlight %}

Usually, the body of the loop will manipulate some variable so that, eventually, the boolean expression in the `()` will finally turn out to be `false`.

Here is a loop that never finishes:

{% highlight java %}
// bogus loop! it never ends
int x = 1;
while(x > 0)
{
    System.out.println(x);
    x++;
}
{% endhighlight %}

Here is another bad loop:

{% highlight java %}
// bogus loop! it never ends
int x = 1;
while(x <= 15)
{
    System.out.println(x);
}
{% endhighlight %}

## Breaking a loop with `break`

You can break (stop) the current loop with the `break` statement:

{% highlight java %}
while(true)
{
    // do stuff
    break;  // get out of here!
}
{% endhighlight %}

Often, we put a `break` in an `if` to determine when exactly the loop should break:

{% highlight java %}
Scanner in = new Scanner(System.in);
String s;
while(true)
{
    s = in.next();
    if(s == "quit")
    {
        break;
    }

    // do stuff when s != quit
}
{% endhighlight %}

## `do/while` loop

A `while` loop checks its condition (the boolean expression) before iterating the first time. If the expression is `false`, it never loops. A `do/while` loop, on the other hand, always loops once, and checks the condition second. If the condition is true, the `do/while` loop repeats, until the condition is false.

In summary, use `do/while` if you want the loop code to happen *at least once*. Use `while` if you want it to be possible that the loop code *never happens at all*.

{% highlight java %}
do
{
    // do stuff
}
while(condition...);
{% endhighlight %}

## `for` loop