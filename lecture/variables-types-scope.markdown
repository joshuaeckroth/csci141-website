---
title: Variables, types, scope
layout: default
---

## Variables

Variables are containers for values. Every (interesting) program you write will use variables. Here is an example of a variable:

{% highlight java %}
int x = 5;
{% endhighlight %}

That code sets up `x` (we can choose its name) to be a variable with type `int` (integer), and to have the value `5`. We can change the value later:

{% highlight java %}
x = 6;
{% endhighlight %}

And we can get the value back out of the variable and, for example, print this value:

{% highlight java %}
System.out.println(x);
{% endhighlight %}

When a variable is on the left-hand side of an `=` sign, we call it an `LVALUE`. Only a single variable can be an `LVALUE`. The right-hand side of the `=` is the `RVALUE` and can be anything you want.

{% highlight java %}
x        =  (y+3)*2;
^LVALUE     ^^^^^^^RVALUE
{% endhighlight %}

## Types

Every variable has a type. You cannot create a variable without explicitly giving it a type.

There are two categories of types. One is the "primitive" types. These are types that are simple values, not collections of values. The others are "class" types, which are complex structures composed of other class types and/or primitive types.

Every value in your code also has a type. For example, if you write `52` in your code, it will be an `int` type of value. If you write `52.0`, it will be a `double` type of value (see below). This is called the "literal syntax" of a small subset of types (the primitive types plus the `String` type).

### Primitive types

| Type | Size | Range | Literal syntax |
|------|------|-------|----------------|
| `byte` | 8 bits | -128, 127 | none |
| `short` | 16 bits | -32768, 32767 | none |
| `int` | 32 bits | -2<sup>31</sup>, 2<sup>31</sup>-1 | `52` |
| `long` | 64 bits | -2<sup>63</sup>, 2<sup>63</sup>-1 | `52L` |
| `float` | 32 bits | (complex; but less precise than `double`) | `52.0f` or `5.2e2f` |
| `double` | 64 bits | (complex; but more precise than `float`) | `52.0` or `5.2e2` |
| `boolean` | 1 bit | `true` or `false` | `true` or `false` |
| `char` | 16 bits | any of 65535 symbols | `x` or [`\u2665`](http://unicode-table.com/en/2665/) |

Summary:

- Use `int` for integer values
- Use `double` for decimal values
- Use `boolean` for true/false values
- Use `char` to represent single symbols

### Arithmetic and String operators

| Operator | Left type | Right type | Explanation |
|---
| `+`, `-`, `*` | `int` | `int` | Adds, subtracts, multiplies as **integers**; result is `int` |
| `/` | `int` | `int` | Produces the "quotient"; see notes below; result is `int` |
| `%` | `int` | `int` | Produces the "remainder"; see notes below; result is `int` |
| `+`, `-`, `*`, `/` | `int` | `double` | Adds, subtracts, multiplies, divides as **doubles**; the left side is converted to a `double` first; result is `double` |
| `+`, `-`, `*`, `/` | `double` | `int` | Adds, subtracts, multiplies, divides as **doubles**; the right side is converted to a `double `first; result is `double` |
| `+`, `-`, `*`, `/` | `double` | `double` | Adds, subtracts, multiplies, divides as **doubles**; result is `double` |
| `+` | `String` | whatever | Concatenates (joins) the left-side string with the right side; the right side is converted to a `String` first; result is `String` |

Notice that `/` on two `int` types produces the "quotient." The quotient, `x / y`, is the number of times (an integer) that `y` goes into `x`. So `7 / 2` is `3`, and `11 / 10` is `1`, and `10 / 22` is `0`.

The `%` gives the "remainder" when applied to two `int` types. The remainder, `x % y`, is what's left over after taking as many `y` amounts out of `x` as you can. Necessarily, `0 <= x % y < y`. So `7 % 2` is `1`, and `11 % 10` is `1`, and `10 % 22` is `10`.

### Common class types

A class type always starts with a capital letter (notice all the primitives are lower-cased). A class type, or just "class," is a complex structure containing other class types and/or primitive types.

When we create variables of class types, we usually call them "objects" (not variables).

`String` is a common class. We can create an object of this type:

{% highlight java %}
String s;
{% endhighlight %}

We can give it a value as well.

{% highlight java %}
String s = "foo bar";
{% endhighlight %}

We see that the `String` class has a literal syntax (double-quotes). Anything typed in double-quotes is a `String` type of value.

All the other class types do not have a literal syntax. To create values of other classes, you must use the `new` keyword:

{% highlight java %}
FooBar f = new FooBar();
{% endhighlight %}

Here are some common class types:

| Class | Purpose | `import` | Example |
|-------|---------|----------|---------|
| `String` | for `"strings"` | no import needed | `String s = "foo bar";` |
| `Scanner` | for reading input | `import java.util.Scanner;` | `Scanner x = new Scanner(System.in);` |
| `Calendar` | for dates | `import java.util.Calendar;` | `Calendar now = Calendar.getInstance();` |


Some classes require that you indicate the kinds of classes to be used internally. For example, the `HashMap` class is a container that associates keys with values (one key for one value). It can use any type as the key and any type as the value. You must tell it which type is the key and which is the value. For example, below we'll make a `HashMap` with `String` keys and `int` values:

{% highlight java %}
HashMap<String, int> mymap = new HashMap<String, int>();
// put some stuff in the map
mymap.put("apple", 3);
mymap.put("banana", 0);
{% endhighlight %}

This feature is called "generics," because the `HashMap` class is generic, it can work with any two types.

## Type conversion

You can convert some types to others using a "cast", which is written in parentheses:

{% highlight java %}
float x = 5.2;
double y = (double)x; // converts x from float to double

int p = 52;
double q = (double)p; // converts p from int to dobule
{% endhighlight %}

Casts are important when you want to divide two integers and get a `double` value in return:

{% highlight java %}
int x = 15;
if((double)x / 2 > 7.0)
{
  // ...
}
{% endhighlight %}

## Constant ("final") variables

You can add the keyword `final` when declaring a variable to indicate that its value may never change. For example:

{% highlight java %}
final int SPECIAL_VALUE = 5;
{% endhighlight %}

By convention, we name such constant variables in all-caps.

## Scope

Every variable has a specific "scope," which means the areas in your code where that variable is accessible or "visible." Scope is defined according to blocks.

A block is a collection of code between `{` and `}`.

```
{  <-- start a block
   blah blah blah
   {  <-- start inside (nested) block
      blah blah blah
   }  <-- end inside block
   blah blah blah
}  <-- end outside block
```

Generally, a variable is visible in the code after its creation until its own block ends. It is also visible inside deeper blocks. Here is an example:

{% highlight java %}
int a;
{
  int b;    // visible: a, b
  {
    int c;  // visible: a, b, c
  }
  int d;    // visible: a, b, d
}
...         // visible: a
{% endhighlight %}

Once a variable goes out of scope, it is destroyed (removed from memory, its value is lost). Java uses "garbage collection" to figure out which variables can be destroyed. As we start using "classes", later in the course, we will see how garbage collection can get very complicated, though the underlying system takes care of it for us.