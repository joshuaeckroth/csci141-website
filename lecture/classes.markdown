---
title: Classes
layout: default
---

Classes gather variables ("fields") and functions ("methods") all under one name. We usually capitalize the name, such as "Location" or "TextBox".

A class creates a new "type", just like "String" is a type (it's also a class). Thus, once you define the class, you can make new variables of that type (called "objects"). Each object of the same class has its own copy of the fields.

For example, here is a class with two fields and one method:

{% highlight java %}
public class Location {
	public double x;  // field
	public double y;  // field

    // method
	public double distanceToLocation(Location other)
	{
		return Math.sqrt(Math.pow(x-other.x, 2.0) +
				Math.pow(y-other.y, 2.0));
	}
}
{% endhighlight %}

Here are two distinct objects of that class (perhaps in the `main()` function). Remember, the objects have their own copies of the fields (`x` and `y` in this case):

{% highlight java %}
Location loc1 = new Location();
loc1.x = 52;
loc1.y = 17;

Location loc2 = new Location();
loc2.x = 10;
loc2.y = -5;
{% endhighlight %}

Any `Location` object can be used to execute the (public) methods. Note that any fields mentioned in the method will refer to the fields of the object that's doing the method. See below:

{% highlight java %}
// because loc1 is the object that's doing the method distanceToLocation,
// the 'x' and 'y' referred to in that code is going to refer to loc1's x and y.

// loc2 will be referred to as 'other' in that method.

double d = loc1.distanceToLocation(loc2);
{% endhighlight %}

## public vs. private

Each field and method must be designated `public` or `private`.

A `private` field cannot be accessed by code outside of the class. If `x` and `y` were `private`, this would not work:

{% highlight java %}
Location loc1 = new Location();
loc1.x = 52;  // does not work if x is private, only works if x is public
loc1.y = 17;  // does not work if y is private, only works if y is public
{% endhighlight %}

The same goes for methods:

{% highlight java %}
double d = loc1.distanceToLocation(loc2);  // does not work if distanceToLocation is private
{% endhighlight %}

Note, even though we always write `public class Location...`, a class cannot be `private`. (Actually, it can, but only if it's defined inside another, public class. These are known as "inner classes.") A private class would be useless, because no code (outside of the class itself) would be able to use it!

## Methods (functions)

Methods are functions defined in the class. Above, `distanceToLocation` is a method.

Since a method is defined inside a class, it can refer to the class fields (variables). Suppose we add this method to the `Location` class:

{% highlight java %}
public void print()
{
    System.out.println("Location x = " + x + ", y = " + y);
}
{% endhighlight %}

Remember that the `Location` class has `x` and `y` fields. What values for `x` and `y` will be printed when this method is executed? That all depends on which object is doing the method:

{% highlight java %}
Location loc1 = new Location();
loc1.x = 52;
loc1.y = 17;
lco1.print();  // prints: Location x = 52, y = 17

Location loc2 = new Location();
loc2.x = 10;
loc2.y = -5;
loc2.print();  // prints: Location x = 10, y = -5
{% endhighlight %}

The same method may act differently depending on the values of the fields (`x` and `y` in this case) of the object that is doing the method.

## Fields (variables in the class)

Fields are normal variables, but defined at the top of the class. Their scope is the whole class and all methods in the class.

Normally, we make fields `private`. This is mostly convention, but there is also a good reason for it. Normally, classes are quite complicated things, and you don't want any code outside of the class modifying the fields without doing it in the proper way. For example, suppose we have a `Rectangle` class:

{% highlight java %}
public class Rectangle {
    private int width;
    private int height;

    public int area()
    {
        return width * height;
    }
}
{% endhighlight %}

If `width` or `height` were `public`, then other code could change their values to negative numbers, which is totally meaningless. In order to prevent this, all access to the fields must be mediated by methods, which are often called "getters" and "setters" (see next section).

### Getters & setters

In order to protect access to fields, we often make the fields private and create "get" and "set" methods for each variable. Here is an example with a `Rectangle` class:

{% highlight java %}
public class Rectangle {
    private int width;
    private int height;

    public int getWidth()
    {
        return width;
    }

    public void setWidth(int newWidth)
    {
        // prevent setting width to a negative value
        if(newWidth > 0)
        {
            width = newWidth;
        }
    }

    public int getHeight()
    {
        return height;
    }

    public void setHeight(int newHeight)
    {
        // prevent setting height to a negative value
        if(newHeight > 0)
        {
            height = newHeight;
        }
    }

    public int area()
    {
        return width * height;
    }
}
{% endhighlight %}

## Constructors

It's tedious to use "setters" all the time to set values. So, we can make a special method known as the "constructor" to set initial values. A constructor always has the same name as the class, and has no return type (not even `void`).

Here is a constructor for the `Rectangle` class:

{% highlight java %}
public class Rectangle {
    private int width;
    private int height;

    // constructor
    Rectangle(int newWidth, int newHeight)
    {
        if(newWidth > 0)
        {
            width = newWidth;
        }
        else
        {
            width = 1;
        }

        if(newHeight > 0)
        {
            height = newHeight;
        }
        else
        {
            height = 1;
        }
    }

    // ... rest of class methods, as above ...
}
{% endhighlight %}

The constructor is executed when you make a new object:

{% highlight java %}
Rectangle mybox = new Rectangle(5, 5);
Rectangle yourbox = new Rectangle(8, 10);
{% endhighlight %}

## `toString()` method

If you attempt to print an object, it usually looks like bogus data:

{% highlight java %}
Rectangle mybox = new Rectangle(5, 5);
System.out.println(mybox);  // prints something like "Rectangle@38e03f"
{% endhighlight %}

It's often nice to be able to print an object and get a meaningful display. If you create a special method known as `toString()` with a `String` return type, you can decide how it gets printed:

{% highlight java %}
public class Rectangle {
    private int width;
    private int height;

    public String toString()
    {
        return ("A rectangle with width = " + width + " and height " + height.");
    }

    // ... rest of class methods, as above ...
}
{% endhighlight %}

Now it prints like so:

{% highlight java %}
Rectangle mybox = new Rectangle(5, 5);
System.out.println(mybox);  // prints "A rectangle with width = 5 and height = 5."
{% endhighlight %}

The `toString` method is executed whenever your object must turn into a `String`, e.g., even in this situation:

{% highlight java %}
Rectangle mybox = new Rectangle(5, 5);
String msg = "I have a rectangle! Here it is: " + mybox + "... Wow!";
{% endhighlight %}

In that code, the `Rectangle` object `mybox` must be converted to a `String` (with our custom `toString` method) in order to include it in the message.

## Game example from class

![UML](/images/npc-uml.png)

### NPC.java

{% highlight java %}
public class NPC {
	private int health;
	private int strength;
	private Location loc;
	private Weapon weapon;

	public NPC(int newHealth, int newStrength, Location newLoc, Weapon newWeapon)
	{
		health = newHealth;
		strength = newStrength;
		loc = newLoc;
		weapon = newWeapon;
	}

	public int getHealth()
	{
		return health;
	}

	public int getStrength()
	{
		return strength;
	}

	public void attackOther(NPC other)
	{
	    int d = strength * weapon.getDamage();
		other.doDamage(d);
	}

	private void doDamage(int amount)
	{
		health = health - amount;
	}

	public void setLocation(Location newLoc)
	{
		loc = newLoc;
	}

	public void setWeapon(Weapon newWeapon)
	{
	    weapon = newWeapon;
	}

	public void goTowards(Location to)
	{
		// ... start walking
	}

	public String toString()
	{
		return ("This is an NPC with strength: "
				+ strength + " and health: " + health);
	}
}

{% endhighlight %}

### Location.java

{% highlight java %}
public class Location {
	private double x;
	private double y;

	public double getX()
	{
		return x;
	}

	public double getY()
	{
		return y;
	}

	public void setX(double newX)
	{
		x = newX;
	}

	public void setY(double newY)
	{
		y = newY;
	}

	public double distanceToLocation(Location other)
	{
		return Math.sqrt(Math.pow(x-other.getX(), 2.0) +
				Math.pow(y-other.getY(), 2.0));
	}

	public boolean isProximate(Location other)
	{
		return (10 >= distanceToLocation(other));
	}
}
{% endhighlight %}

### Weapon.java

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
}
{% endhighlight %}

### MainClass.java

{% highlight java %}
public class MainClass {

	public static void main(String[] args) {
		Location loc1 = new Location();
		Location loc2 = new Location();

		loc1.setX(50);
		loc1.setY(4);

		loc2.setX(3);
		loc2.setY(8);

		double d = loc1.distanceToLocation(loc2);
		System.out.println("Distance is: " + d);
		System.out.println("Is proximate? " +
				loc1.isProximate(loc2));

	    Weapon sword = new Weapon();
        sword.setName("Excalibur");
        sword.setDamage(10);
        Weapon dagger = new Weapon();
        dagger.setName("Prickler");
        dagger.setDamage(2);

		NPC phil = new NPC(100, 5, loc1, sword);
		NPC sue = new NPC(80, 20, loc2, dagger);
		System.out.println("Phil's health: " + phil.getHealth());
		sue.attackOther(phil);
		System.out.println("Phil's health: " + phil.getHealth());

		System.out.println("This is Sue: " + sue);
	}

}
{% endhighlight %}