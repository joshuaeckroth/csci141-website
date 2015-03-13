---
title: Classes
layout: default
---

## Methods (functions)

## Fields (variables in the class)

(have whole-class scope)

(usually `private`, thus the need for getters and setters (see below))

### Getters & setters

## Constructors

(set initial values for fields)

## `toString()` method

## Game example from class

### NPC.java

{% highlight java %}

public class NPC {
	private int health;
	private int strength;
	private Location loc;

	public NPC(int newHealth, int newStrength, Location newLoc)
	{
		health = newHealth;
		strength = newStrength;
		loc = newLoc;
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
		other.doDamage(strength);
	}

	private void doDamage(int amount)
	{
		health = health - amount;
	}

	public void setLocation(Location newLoc)
	{
		loc = newLoc;
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

		NPC phil = new NPC(100, 5, loc1);
		NPC sue = new NPC(80, 20, loc2);
		System.out.println("Phil's health: " + phil.getHealth());
		sue.attackOther(phil);
		System.out.println("Phil's health: " + phil.getHealth());

		System.out.println("This is Sue: " + sue);
	}

}
{% endhighlight %}