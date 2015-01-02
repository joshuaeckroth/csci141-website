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
{% endhighlight %}`

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