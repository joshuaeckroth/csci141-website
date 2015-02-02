---
title: Homework 4 (Test 1 review)
layout: default
---

Test 1 covers:

- [Variables, types, scope](/lecture/variables-types-scope.html)
- [Simple input/output](/lecture/simple-io.html)
- [Conditionals](/lecture/conditionals.html)
- [Loops](/lecture/loops.html)

## Variables, types, scope

What variable type or types are appropriate for the following kinds of data? You only need to name one type for each example; try to name the most appropriate type. Use correct capitalization of the type name.

1. The year of your birth.
2. The name of the U.S. President.
3. A smiley face: `:-)`
4. A fancy Unicode smiley face: `☺`
5. The symbol `&`
6. The balance of your checking account.
7. A "flag" variable indicating if a user is logged in or not.

8\. Put a comment `// HERE` at the end of every line of code below where the variable `x` is in scope. Do not mark lines of code that are just `{` or `}` or function/class headers like `public class Foo` or `public static int myfunc(...)`.

{% highlight java %}
public class Foo
{
    private static int y;

    public static int myfunc(int x, int z)
    {
        System.out.println(z);
        return x * z;
    }

    public static void main(String[] args)
    {
        int z = 55;
        if(z < 100)
        {
            int w = myfunc(z, z);
            System.out.println(w);
        }
    }
}
{% endhighlight %}

9\. Do the same for this code, again with respect to `x`:

{% highlight java %}
public class Foo
{
    private static int x = 8;
    private static int y = 10;

    public static void main(String[] args)
    {
        for(int i = 0; i < 100; i++)
        {
            System.out.println(i);
            x = x + 1;
        }
        System.out.println(x);
    }
}
{% endhighlight %}

## Boolean expressions

Build truth tables for the following boolean expressions. You can use T and F for `true` and `false`.

- 10\. `a || b || !c`
- 11\. `(a && !b) || c`

What values for the variables `p`, `q`, and `x` make the following expressions true?

- 12\. `p || x < 10`
- 13\. `!(p && x >= 0) && q`

Translate these English sentences into boolean expressions:

- 14\. X is larger than both Y and Z.
- 15\. X is between Y and Z (inclusive)
- 16\. Either P is true or Q is true, but not both.

17\. Given that `int x = 4, y = 3` and `double z = 1.1`, is the following expression true or false?

{% highlight java %}
((x >= y) && !(x/y > z)) || (x%y < z)
{% endhighlight %}

## Conditionals

18\. In the following code, for what values of `z` (an integer) make the message "Burp" (and no other message) appear only once on the screen?

{% highlight java %}
if(z < 0)
{
    if(z < 3)
    {
        System.out.println("Belch");
    }
    if(z < 4)
    {
        System.out.println("Burp");
    }
    else
    {
        System.out.println("Belch");
    }
}
else if(z == 0)
{
    System.out.println("Burp");
}
else
{
    if(z == -1)
    {
        System.out.println("Belch");
    }
    else
    {
        System.out.println("Burp");
    }
}
{% endhighlight %}

## Loops

19\. Convert this `for()` loop into an equivalent `while()` loop:

{% highlight java %}
int j;
for(j = 15; j > -15; j = j - 2)
{
    System.out.println(j);
}
{% endhighlight %}

20\. Convert this `while()` loop into an equivalent `for()` loop:

{% highlight java %}
Scanner in = new Scanner(System.in);
int i = 0;
while(i != -1)
{
    System.out.println(i);
    i = in.nextInt();
}
{% endhighlight %}

21\. Convert this double-`for()` loop into an equivalent double-`while()` loop:

{% highlight java %}
int i;
for(i = 0; i < 100; i++)
{
    int j;
    for(j = i; j < 100;)
    {
        System.out.println(i * j);
        j = j + 2;
    }
}
{% endhighlight %}

22\. Given that `int a = 5, b = 6`, how many times is the conditional `a < b` in the following loop checked?

{% highlight java %}
while(a < b)
{
    a = a % (b - a);
    a = a + 1;
    b = b - 1;
    a = a / b;
}
{% endhighlight %}

23\. In the loop above, after it finishes, what are the final values of `a` and `b`?

24\. Write a program that repeatedly asks a user for positive integers. When the user types a number <= 0, the program prints the largest number ever entered and then quits.

25\. Write a program that asks the user for a single integer `n` and computes (and prints) `n*(n-1)*(n-2)*...*3*2`. For example, if the user types `6`, the program should print `720`. You can assume the user will type a number >= 2.


