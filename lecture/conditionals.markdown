---
title: Conditionals
layout: default
---

## `boolean` operators

For the table below, assume we have:

{% highlight java %}
boolean p = true;
boolean q = false;
{% endhighlight %}

| Operator | Meaning | Example |
|----------|---------|---------|
| `&&` | "and", true outcome requires both sides are true | `p && q` is `false` |
| `\|\|` | "or", true outcome requires either side is true | `p \|\| q` is `true` |
| `==` | "equal", true outcome requires both sides are the same (primitive or `String`) value or same object | `p == q` is `false`, `p == true` is `true`|
| `!=` | "not equal", opposite of `==` | `p != q` is `true`, `p != true` is `false` |
| `!` | "not", just negates a `boolean` value | `!p` is `false`, `!q` is `true` |

### Truth tables

We can figure out the truth of a complicated boolean expression by finding the truth-value of each part. We build a table for this operation because we need to keep track of all the different values that the variables/subexpressions may hold.

For what values of boolean variables `x`, `y`, and `z` make this true? `!(x || (y && !z))`

We break the expression into its variables and subexpressions and put them all in the table.

| `x` | `y` | `z` | `!z` | `y && !z` | `x \|\| (y && !z)` | `!(x \|\| (y && !z))` |
|---
| `true` | `true` | `true` | `false` | `false` | `true` | `false` |
| `true` | `true` | `false` | `true` | `true` | `true` | `false` |
| `true` | `false` | `true` | `false` | `false` | `true` | `false` |
| `true` | `false` | `false` | `true` | `false` | `true` | `false` |
| `false` | 	`true` | 	`true` | 	`false` | 	`false` | 	`false` | 	`true` |
| `false` | 	`true` | 	`false` | 	`true` | 	`true` | 	`true` | 	`false` |
| `false` | 	`false` | 	`true` | 	`false` | 	`false` | 	`false` | 	`true` |
| `false` | 	`false` | 	`false` | 	`true` | 	`false` | 	`false` | 	`true` |


## Arithmetic comparison operators

For the table below, assume we have:

{% highlight java %}
int x = 5;
double y = 5.75;
{% endhighlight %}

| Operator | Meaning | Example |
|----------|---------|---------|
| `>` | "greater than" | `x > y` is `false` |
| `<` | "less than" | `x < y` is `true` |
| `>=` | "greater than or equal" | `x >= y` is `false` |
| `<=` | "less than or equal" | `x <= y` is `true` |

## `if`

{% highlight java %}
if(x > 5)
    System.out.println("yay!");
{% endhighlight %}

Braces are required if you have more than one line of code after the `if`:

{% highlight java %}
if(x > 5)
{
    System.out.println("yay!");
    System.out.println("yay!");
}
{% endhighlight %}

## `if`, `else`

{% highlight java %}
if(x > 5)
{
    System.out.println("It seems x is greater than 5.");
}
else
{
    System.out.println("It seems x is less than or equal to 5.");
}
{% endhighlight %}

## `if`, `else if`, `else if`, etc.

## `switch`

## `? :` ternary operator