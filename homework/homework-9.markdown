---
title: Homework 9
layout: default
---

Test 2 covers:

- [Variables, types, scope](/lecture/variables-types-scope.html)
- [Simple input/output](/lecture/simple-io.html)
- [Conditionals](/lecture/conditionals.html)
- [Loops](/lecture/loops.html)
- [Functions](/lecture/functions.html)
- [Arrays](/lecture/arrays.html)
- [Classes](/lecture/classes.html)

## Test 2 review


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
    public void toString()
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
