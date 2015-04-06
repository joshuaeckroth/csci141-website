---
title: Inheritance
layout: default
---

The classes we have learned about so far have been rather simple: a class was just a collection of fields (variables) and methods (functions), plus a special "constructor" method.

But classes can also have relations to other classes through "inheritance" or "subclassing." Consider these shape-related classes:

![Shapes](/images/shapes-uml.png)

This diagram indicates that `Shape` is a parent class and each of `Ellipse`, `Rectangle`, and `Triangle` are subclasses. The way this is written in code is with `extends`:

{% highlight java %}
class Shape {
  // ...
}

class Ellipse extends Shape {
  // ...
}

class Rectangle extends Shape {
  // ...
}

class Triangle extends Shape {
  // ...
}
{% endhighlight %}

Because `Ellipse extends Shape`, every `Ellipse` object is also a `Shape` object, and the `Ellipse` class has an `x` and `y` and `getX()` and so forth, for all the things inside the `Shape` class.

So, if you create an `Ellipse` object like so:

{% highlight java %}
Ellipse e = new Ellipse();
{% endhighlight %}

...then you can access `Ellipse` public methods as well as `Shape` public methods:

{% highlight java %}
e.setX(5.0);         // Shape public method (inherited)
e.setMajorAxis(2.2); // Ellipse public method
{% endhighlight %}

## public, private, protected

All fields and methods that are `private` in `Shape` are not directly accessible to `Ellipse` or any other subclasses or any other classes at all. Even though `Ellipse` is a subclass of `Shape`, it cannot access `Shape`'s `private` stuff.

Within `Ellipse` and other subclasses, you will be required to use `Shape`'s `getX()`, `setX()`, etc. methods to read/modify private data.

Besides `public` and `private`, there is one more option: `protected`. A `protected` field or method means that it is `private` (inaccessible) as far as all other code is concerned, *except* for subclasses. Any subclass can access `protected` members of its parent class. In summary: `protected` looks like `private` to outside code, but subclasses can access `protected` members.

## Calling your parent's constructor

Since `x` and `y` are `private` in `Shape`, the `Ellipse` class and other subclasses cannot directly set those values. Thus, the `Ellipse` constructor cannot set those values. However, we want it to. The solution is to use `super()`, which calls the parent constructor:

{% highlight java %}
public Rectangle(double newX, double newY, double newWidth, double newHeight) {
    super(newX, newY);  // call Shape's constructor, which sets x and y
    width = newWidth;   // set Ellipse field
    height = newHeight; // set Ellipse field
}
{% endhighlight %}

## Eclipse assistance

### Generate getters/setters

In the "Source" menu, you'll see the menu item "Generate Getters and Setters..." After you set up some `private` fields in your class, use this option to generate all the getter/setter methods.

![Generate getters/setters](/images/eclipse-generate-getters-setters.png)

### Generate a constructor

In the "Source" menu, you'll see two items: "Generate Constructor using Fields..." and "Generate Constructors from Superclass..." (superclass = parent class).

The first creates a full constructor that sets subclass fields and calls the superclass constructor. The second just calls the superclass constructor. So, the first option is more useful. It generates this (for `Ellipse`):

{% highlight java %}
public Rectangle(double newX, double newY, double height, double width) {
	super(newX, newY);
	this.height = height;
	this.width = width;
}
{% endhighlight %}

### Detect private parent fields

When you try to access your parent's `private` fields, Eclipse gives the following message (this is in the `Ellipse` class):

![Private parent field](/images/eclipse-private-parent-field.png)

Your options are:

- "Change visibility of 'x' to 'protected'" --- `x` is currently `private` in the parent `Shape` class, so it is inaccessible ("not visible") to `Ellipse`. If `x` is changed to `protected`, it will be accessible to `Ellipse`, but still not accessible to other code. (This is a less dramatic change than making `x` `public`, which Eclipse does not even suggest.)

- "Replace x with getter" --- in other words, use `getX()` from the parent class, which is a `public` method.

- "Create local variable 'x'" --- create a variable inside this method, and use that; this is not at all what we want, since that local variable won't be the `x` we actually want to access

- "Create field 'x'", etc. --- again, we don't want a new `x` field, we want the one that already exists in the parent class, so these options don't apply
