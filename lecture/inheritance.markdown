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

## Polymorphism

Java lets you create an object of a subclass type but save it into a variable with ancestor-class type (could be direct parent, or parent's parent, etc.). For example:

{% highlight java %}
Shape s = new Rectangle(5, 2, 10, 11);
{% endhighlight %}

Notice the shape `s` is really a `Rectangle` but we're saving it as a `Shape` type of object. It does not "change" into a `Shape` when we do this; it's still a `Rectangle`. However, now we can only execute `Shape` methods on `s`. So this fails:

{% highlight java %}
// this FAILS; cannot call Rectangle methods since the type of s is Shape
System.out.println(s.getWidth());

// but this works, since getX() is a Shape method
System.out.println(s.getX());
{% endhighlight %}

However, suppose we define a method in `Shape` that is redefined (overridden) in `Rectangle`. Then Java will use the more specific method when it exists.

{% highlight java %}
public class Shape {
  public double area() {
    return -1.0; // no meaningful "area" of a generic shape
  }
}

public class Rectangle extends Shape {
  public double area() {
    return width * height;
  }
}

public class Ellipse extends Shape {
  public double area() {
    return Math.PI * majorAxis * minorAxis;
  }
}
{% endhighlight %}

Now if we have a `Rectangle` or `Ellipse`, and we execute the `area` method, it will use the right method even when we use a generic `Shape` variable:

{% highlight java %}
Shape s1 = new Rectangle(5, 2, 10, 11);
Shape s2 = new Ellipse(5, 2, 9.2, 3.3);

// This actually executes Rectangle's area() method
System.out.println("s1 area = " + s1.area());

// This actually executes Ellipse's area() method
System.out.println("s2 area = " + s2.area());

// Now let's make a truly generic shape
Shape s3 = new Shape(5, 2);

// This actually executes Shape's area() method (which returns -1.0)
System.out.println("s3 area = " + s3.area());
{% endhighlight %}

What's the benefit of saving a true `Rectangle` into a generic `Shape` variable? Remember how arrays can only store one type of value? If you want to mix rectangles, ellipses, and triangles in a single array, you're stuck... unless you call them all "shapes" and only put "shapes" in the array:

{% highlight java %}
Shape[] myShapes = new Shape[3];
myShapes[0] = new Rectangle(5, 2, 10, 11);
myShapes[1] = new Ellipse(5, 2, 9.2, 3.3);
myShapes[2] = new Triangle(5, 2, 18, 22, 0.58);

// Let's print all of their areas. Note, the specific Rectangle/Ellipse/Triangle
// area() methods will be executed when appropriate!
for(int i = 0; i < myShapes.length; i++)
{
  System.out.println("Area of shape " + (i+1) + " is = " + myShapes[i].area());
}
{% endhighlight %}

Another case where you'd use this technique is functions. Suppose your function can work with any shape:

{% highlight java %}
public void describeSingleShape(Shape someShape)
{
  System.out.println("I have a shape.");
  System.out.println("It is located at x = " + someShape.getX() + " and y = " + someShape.getY());
  System.out.println("It is a beautiful shape (surely).");
  System.out.println("Its true type is " + someShape.getClass());
  System.out.println("And its area is " + someShape.area());
  System.out.println("What a phenomenal shape, indeed.");
}
{% endhighlight %}

Here is an example output from that function:

```
I have a shape.
It is located at x = 5.0 and y = 2.0
It is a beautiful shape (surely).
Its true type is class Rectangle
And its area is 110.0
What a phenomenal shape, indeed.
```

The technique described in this section is called "polymorphism" because objects are acting like different kinds of things in different situations. In the array above, rectangles, ellipses, and triangles are acting as generic shapes. But they're not really generic shapes, and Java knows that, so the appropriate `area()` methods are executed.

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
