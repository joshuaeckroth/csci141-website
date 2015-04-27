---
title: Interfaces
layout: default
---

An interface is similar to a class but differs in the following ways:

- an interface has no fields; it only has methods
- the methods in an interface have no code

Here is an example interface:

{% highlight java %}
public interface Shape {
	public double area();
}
{% endhighlight %}

The purpose of an interface is to provide a guarantee that any class that "implements" the interface will have the methods listed. So, in the `Shape` interface above, any class that `implements Shape` must have an `area()` method. For example,

{% highlight java %}
public class Rectangle implements Shape {
	private double width;
	private double height;

	public Rectangle(double width, double height) {
		this.width = width;
		this.height = height;
	}

	public double area() {
		return width * height;
	}
}
{% endhighlight %}

Just like subclasses, you can collect objects of different types which all implement the same interface. Suppose both `Rectangle` and `Ellipse` implement `Shape`:

{% highlight java %}
Rectangle r = new Rectangle(5, 2);
Ellipse e = new Ellipse(2.2, 6.6);
Shape[] shapes = new Shape[2];
shapes[0] = r;
shapes[1] = e;
for(int i = 0; i < shapes.length; i++)
{
	System.out.println(shapes[i].area());
}
{% endhighlight %}

This is just like polymorphism except with interfaces instead of subclasses.

## Anonymous classes

Sometimes, you want to create an object from a class that only implements some interface. And you don't actually want to create the class separately, because you only need to create one object from it. You can accomplish this by creating an anonymous (unnamed) class that simply implements a particular interface, and immediately create an object of that anonymous class.

{% highlight java %}
public interface Ball {
    void hit();
}

public class Foo {
    public static void main(String[] args) {
    
        // create an anonymous (nameless) class that implements an interface,
        // and immediately create an instance
        Ball b = new Ball() {
            public void hit() {
                System.out.println("You hit it!");
            }
        };
        b.hit();
    }
}
{% endhighlight %}

