---
title: Processing library
layout: default
---

The [Processing](http://processing.org) platform provides a variety of graphics functions. To use it, you'll first need to download a JAR file that I extracted out of the Processing package. Download [processing-core.jar](/processing-core.jar) and save it somewhere.

## Using Processing in Eclipse

Create a new Java project in Eclipse in the typical way outlined in the [Eclipse notes](/lecture/eclipse.html).

Right-click on the project name on the left pane and click "Properties" (or go to the Project menu and click "Properties"). Choose "Java Build Path" on the left, and then click "Add External JARs".

![Processing 1](/images/processing-1.png)

Add the `processing-core.jar`. You should see it in the list after it's added.

![Processing 2](/images/processing-2.png)

Now create a class file in the usual way. Rewrite all of it to the following (changing `HelloWorld` in all places to whatever you called your class):

{% highlight java %}
import processing.core.*;

public class HelloWorld extends PApplet {

	// put "global" variables here, outside of the functions

	public void setup() {
		size(..., ...);
	}

	public void draw() {

	}

	public static void main(String[] args) {
		PApplet.main(new String[] { "HelloWorld" });
	}
}
{% endhighlight %}

The `main` function (at the bottom) starts Processing. You can use the this line of code instead of the non-commented one if you want it to run in fullscreen mode:

{% highlight java %}
PApplet.main(new String[] { "--full-screen", "HelloWorld" });
{% endhighlight %}

The `"HelloWorld"` part must change to whatever your main class is named.

The `setup()` function must exist and contains any code you want to run just once, before your program really gets going.

The `draw()` function must also exist and contains drawing code that happens every frame. Normally, Processing with execute the `draw()` function 60-times per second, to give your application 60 frames per second.

You can use `noLoop();` inside `setup()` if you don't need any animation, and only want `draw()` to be executed once.

If Eclipse asks how to run your application, choose "Java Application" not "Java Applet".

Here is an example that draws a bouncing ball:

{% highlight java %}
import processing.core.*;

public class BouncyBall extends PApplet {

	// ball x, y, and velocities dx, dy
	int x;
	int y;
	int dx;
	int dy;

	public void setup() {
		size(800, 600);
		x = 400; // initial x position
		y = 400; // initial y position
		dx = 5;  // initial x velocity
		dy = 3;  // initial y velocity
	}

	public void draw() {
		background(255);
		fill(0);
		ellipse(x, y, 50, 50);
		x += dx;
		y += dy;

		// bounce off left/right sides
		if(x > width || x < 0)
		{
			dx = -dx;
		}

		// bounce of top/bottom sides
		if(y > height || y < 0)
		{
			dy = -dy;
		}
	}

	public static void main(String[] args) {
		PApplet.main(new String[] { "BouncyBall" });
	}
}
{% endhighlight %}

## Multiple classes with Processing

If you have just one class, that class can `extend PApplet` and you're good to go, as described above.

If you have more classes, and those other classes need to do drawing as well as the main class, then you need to tell the other classes "where" to draw. There is only one window to draw on, one `PApplet` technically, and the other classes need to know about it.

This is accomplished by sending the other classes a pointer to the `PApplet` main class. Here is an example:

{% highlight java %}
// main class
public class MainClass extends PApplet {
    private BadDude burt;
    
    public void setup()
    {
        // tell BadDude class about 'this', which is a pointer
        // to the MainClass PApplet.
        
        burt = new BadDude(this);
    }
}

// bad dude class; note, it does not "extend PApplet"
public class BadDude {
    private PApplet parent;  // this is where we save the pointer
    
    // the constructor will receive and save the pointer
    public BadDude(PApplet newParent)
    {
        parent = newParent;
    }
    
    // here is a random function in the class that must do drawing
    public void drawSomething()
    {
        // all drawing commands must operate on the 'parent' object
        parent.fill(255, 0, 255);
        parent.ellipse(50, 50, 10, 10);
    }
}
{% endhighlight %}

## Setup functions

These are useful functions to create in `setup()`:

- `size(int width, int height)` -- set width and height of window
- `frameRate(int rate)` -- set the frame rate; default is 60, for 60 frames per second
- `noLoop()` -- indicate that `draw()` should only execute once, not 60 times per second; you can use `noLoop()` in `draw()` as well to stop looping, and `loop()` to start it again

## Drawing functions

Typically, these are used in the `draw()` function:

### Shapes

- [point()](https://processing.org/reference/point_.html)
- [line()](https://processing.org/reference/line_.html)
- [rect()](https://processing.org/reference/rect_.html)
- [triangle()](https://processing.org/reference/triangle_.html)
- [quad()](https://processing.org/reference/quad_.html)
- [ellipse()](https://processing.org/reference/ellipse_.html)
- [arc()](https://processing.org/reference/arc_.html)

Change the way shapes are drawn:

- [rectMode()](https://processing.org/reference/rectMode_.html)
- [ellipseMode()](https://processing.org/reference/ellipseMode_.html)
- [strokeWeight()](https://processing.org/reference/strokeWeight_.html)
- [strokeJoin()](https://processing.org/reference/strokeJoin_.html)
- [strokeCap()](https://processing.org/reference/strokeCap_.html)

### Colors

- [color()](https://processing.org/reference/color_.html) -- note, the Processing.org docs show this function returning a `color` type. In our Java programs, use `int` instead.
- [colorMode()](https://processing.org/reference/colorMode_.html)
- [fill()](https://processing.org/reference/fill_.html) -- set the fill color (for shapes)
- [noFill()](https://processing.org/reference/noFill_.html)
- [stroke()](https://processing.org/reference/stroke_.html) -- set the stroke color (for lines and shapes)
- [noStroke()](https://processing.org/reference/noStroke_.html)
- [background()](https://processing.org/reference/background_.html) -- draw a single color on the whole screen, blanking it out

### Images

Images should be saved into `PImage` objects (variables with type `PImage`).

- [loadImage()](https://processing.org/reference/loadImage_.html)
- [image()](https://processing.org/reference/image_.html) -- for actually drawing the image
- [imageMode()](https://processing.org/reference/imageMode_.html)
- [tint()](https://processing.org/reference/tint_.html) -- change the colors of images drawn subsequently
- [noTint()](https://processing.org/reference/noTint_.html) -- turn off the tint for images drawn subsequently

### Text & fonts

- [text()](https://processing.org/reference/text_.html) -- put text on the screen
- [textSize()](https://processing.org/reference/textSize_.html)
- [textFont()](https://processing.org/reference/textFont_.html) -- use a system font, or font created by `createFont()`
- [createFont()](https://processing.org/reference/createFont_.html)
- [loadFont()](https://processing.org/reference/loadFont_.html)

### 2D transformations

- [pushMatrix()](https://processing.org/reference/pushMatrix_.html)
- [popMatrix()](https://processing.org/reference/popMatrix_.html)
- [resetMatrix()](https://processing.org/reference/resetMatrix_.html)
- [translate()](https://processing.org/reference/translate_.html)
- [rotate()](https://processing.org/reference/rotate_.html)
- [scale()](https://processing.org/reference/scale_.html)

### 3D graphics

- Use `size(w, h, P3D);`
- [box()](https://processing.org/reference/box_.html)
- [sphere()](https://processing.org/reference/sphere_.html)
- [rotateX()](https://processing.org/reference/rotateX_.html), [rotateY()](https://processing.org/reference/rotateY_.html), [rotateZ()](https://processing.org/reference/rotateZ_.html)
- [pointLight()](https://processing.org/reference/pointLight_.html)
- [spotLight()](https://processing.org/reference/spotLight_.html)
- [directionalLight()](https://processing.org/reference/directionalLight_.html)
- [ambient()](https://processing.org/reference/ambient_.html) and [ambientLight()](https://processing.org/reference/ambientLight_.html)
- [specular()](https://processing.org/reference/specular_.html) and [lightSpecular()](https://processing.org/reference/lightSpecular_.html)
- [shininess()](https://processing.org/reference/shininess_.html)
- [emissive()](https://processing.org/reference/emissive_.html)
- [texture()](https://processing.org/reference/texture_.html) and [textureWrap()](https://processing.org/reference/textureWrap_.html)
- [camera()](https://processing.org/reference/camera_.html)

### Math

- [random()](https://www.processing.org/reference/random_.html) -- for generating random `float` type values in a specified range; use `int(random(0, 10))` (where 0 and 10 could be whatever) to force it to yield `int` values
