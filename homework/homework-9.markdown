---
title: Homework 9
layout: default
---

Test 2 covers:

- [Arrays](/lecture/arrays.html)
- [Classes](/lecture/classes.html)

## Test 2 review

### Arrays

Create an array of three integers. Fill it with arbitrary non-zero values.

Suppose you have an integer `n`. Create an array of `double` values, size `n`, and make every element equal to 5.0.

Given an array `ws`, print its size in one line of code (`System.out.println(...)`).

Write a function that computes and returns the following sum, for two `double` arrays of equal length `n`:

<div>
$$
s = \sum_i^n (x_i - 2y_i)
$$
</div>

Write a function that returns a new integer array of a given size (the size is a parameter), and fills it with zeros.

Assuming the function below exists, write one line of code that uses it properly (saves the returned array, gives appropriate arguments):

{% highlight java %}
String[] foo(int a, double b, char c, int[] d) { ... }
{% endhighlight %}

### Classes

Create an `Ellipse` class with a "major axis" field, "minor axis" field, and "area" method, calculated as `pi*major_axis*minor_axis`. Include a constructor that lets you set major/minor axis.

Assuming the class below exists and is fully defined, create a new instance of the class using the constructor (and arbitrary arguments), then execute the `bar` method on that new instance, and also print the instance.

{% highlight java %}
public class Foo {
    // ... private fields

    public Foo(int a, String b)
    { ... }

    public void bar()
    { ... }

    public String toString()
    { ... }
}
{% endhighlight %}

In the following class definition, label/list these features: the constructor, all methods (not including the constructor), all fields.

{% highlight java %}
public class Weapon {
    private int damage;
    private String name;

    public Weapon(int newDamage, String newName)
    {
        damage = newDamage;
        name = newName;
    }

    public int getDamage()
    {
        return damage;
    }

    public String getName()
    {
        return name;
    }

    public void setDamage(int newDamage)
    {
        damage = newDamage;
    }

    public void setName(String newName)
    {
        name = newName;
    }
    public String toString()
    {
        return "Weapon: " + name;
    }
}
{% endhighlight %}

Create a very simple class definition so that this line of code works (note, there are many possible answers):

{% highlight java %}
Vehicle myBabysHonda = new Vehicle("Honda", "Accord", 2014, 20414.00);
{% endhighlight java %}

Write a class definition (but no code in the methods) that satisfies this UML diagram:

![File UML](/images/file-uml.png)
