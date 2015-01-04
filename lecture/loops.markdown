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

## `do/while` loop

## `for` loop