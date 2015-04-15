---
title: Homework 13
layout: default
---

Skills needed to complete this assignment:

- [Swing](/lecture/swing.html)

## Task 1

Create a simulation of "termites." A bunch of termites live on a grid that has some sand. You can choose the size of the grid; each pixel (grid x,y) either has a piece of sand (yellow pixel) or doesn't (black pixel). Each termite is looking at a single grid cell, so each termite has an x,y at all times. The termites are drawn larger just to make them visible.

Each termite behaves independently and identically. They do not communicate. They only pickup and drop a piece of sand. When a termite picks up a piece of sand, it is removed from the grid (that pixel turns black). When a piece of sand is dropped, wherever the termite is standing then turns yellow and the grid cell is recorded as having sand.

You must have a "stop" and "start" button. See the notes about [threads](/lecture/threads.html) for some guidance about how that might work.

Termites move according to a speed and angle (in radians). Here is a move method, so you don't need to worry about the trigonometry. This move method also supports wrap around.

{% highlight java %}
// in Termite class, which has private fields 'angle' (double),
// 'x' and 'y' (ints), and 'grid' (from a custom Grid class)
public void move(int speed)
{
	x += (int)(speed * Math.cos(angle));
	y += (int)(speed * Math.sin(angle));
	if(x < 0) { x = grid.getWidth() + x; }
	if(x >= grid.getWidth()) { x = x - grid.getWidth(); }
	if(y < 0) { y = grid.getHeight() + y; }
	if(y >= grid.getHeight()) { y = y - grid.getHeight(); }
}
{% endhighlight %}

The termites behave according to these simple rules, at every time step:

- change angle by a small random amount and move forward a little bit
- if not holding sand, and the grid has sand at this location, pick it up
- if holding sand, and the grid has sand at this location, change status to "looking for a free cell"
- if holding sand and looking for a free cell and the grid does not have sand here, drop the sand, AND keep moving away in a random direction until you find a spot with no sand (get off the sand pile!)


Here is how you use random numbers:

{% highlight java %}
// create a class field:
private Random r;

// create the object in a constructor:
r = new Random();

// later, in some method, use it:
boolean b =  r.nextBoolean(); // get a random true/false
int x = r.nextInt(100); // get a random integer (0-99)
double y = r.nextDouble(); // get a random double (0.0-1.0)
{% endhighlight %}

Here is a video of the termites in action. A termite is drawn as a white circle if it's not currently holding sand, otherwise it is drawn as a green circle (holding sand).

<div style="text-align: center">
<iframe src="https://player.vimeo.com/video/125040847" width="500" height="375" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
</div>
