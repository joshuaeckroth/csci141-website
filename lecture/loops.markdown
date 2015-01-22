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

A `for` loop is no more powerful than a `while` loop; it just has a different (sometimes more convenient) structure:

{% highlight java %}
for(initialization; conditional; update)
{
    // do stuff...
}
{% endhighlight %}

This is what the three parts inside the parentheses (commonly) mean:

- `initialization` --- create counting variables and set their values

- `conditional` --- a `boolean` expression that determines if the loop should repeat; this conditional usually refers to a variable defined in the initialization

- `update` --- commonly used to change a variable defined in the initialization and referred to in the conditional; changing this variable should eventually cause the conditional to be false, causing the loop to terminate

`for` loops follow this sequence of steps:

1. execute whatever is put in the initialization

2. check the conditional; if it evaluates to `false` then skip the loop; if it evaluates to `true`, continue to the next step

3. execute the stuff inside the block

4. execute the update

5. go to step 2

It's useful to see how a `while` loop can be converted to a `for` loop. In this example, the `while` loop and the `for` loop are (nearly) equivalent:

{% highlight java %}
int i = 0;
while(i < 10)
{
    // do stuff...
    i++;
}

for(int i = 0; i < 10; i++)
{
    // do stuff...
}
{% endhighlight %}

(The two are only "nearly" equivalent for the following reason: in the `while` loop case, the integer `i` is declared outside of the loop, so code that follows the loop block can still refer to `i`; in other words, the [scope](/lecture/variables-type-scope.html) of `i` is less constrained in the `while` loop example. In the `for` loop case, the integer `i` can only be used inside the `for` loop block; it does not exist when the loop is finished, because it is no longer in scope.)

Let's dissect that `for` loop above:

- initialization: `int i = 0`

- conditional: `i < 10`

- update: `i++`

You should be able to see these same three components present in the `while` loop, but the `while` loop does not have special handling of the three components. On the other hand, a `for` loop is specifically designed to have exactly those three components (initialization, conditional, and update).

A `for` loop need not have anything in any of the three components. If none of the components have code in them, it is equivalent to an infinite loop. In other words, these two loops are equivalent:

{% highlight java %}
while(true)
{
    // do stuff forever... (or until "break" is encountered)
}
for(;;)
{
    // do stuff forever... (or until "break" is encountered)
}
{% endhighlight %}

Here is an example of a nested `for` loop that is equivalent to Σ<sup>100</sup><sub>j=1</sub> Σ<sup>100</sup><sub>k=1</sub> (j+k)<sup>2</sub>

{% highlight java %}
int sum = 0;
for(int j = 1; j <= 100; j++)
{
    for(int k = 1; k <= 100; k++)
    {
        sum += (j+k)*(j+k);
    }
}
{% endhighlight %}
