---
title: Processing library
layout: default
---

{% highlight java %}
import processing.core.PApplet;

public class HelloWorld extends PApplet {

	public void setup() {

	}

	public void draw() {

	}

	public static void main(String[] args) {
		// or: PApplet.main(new String[] { "--full-screen", "HelloWorld" });
		PApplet.main(new String[] { "HelloWorld" });
	}
}
{% endhighlight %}

## Setup

- `size(int width, int height)` -- set width and height of window

## Shapes

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

## Colors

- [color()](https://processing.org/reference/color_.html) -- note, the Processing.org docs show this function returning a `color` type. In our Java programs, use `int` instead.
- [colorMode()](https://processing.org/reference/colorMode_.html)
- [fill()](https://processing.org/reference/fill_.html)
- [noFill()](https://processing.org/reference/noFill_.html)
- [stroke()](https://processing.org/reference/stroke_.html)
- [noStroke()](https://processing.org/reference/noStroke_.html)
- [background()](https://processing.org/reference/background_.html)

## Images

Images should be saved into `PImage` objects (variables with type `PImage`).

- [loadImage()](https://processing.org/reference/loadImage_.html)
- [image()](https://processing.org/reference/image_.html) -- for actually drawing the image
- [imageMode()](https://processing.org/reference/imageMode_.html)
- [tint()](https://processing.org/reference/tint_.html) -- change the colors of images drawn subsequently
- [noTint()](https://processing.org/reference/noTint_.html) -- turn off the tint for images drawn subsequently

## Text & fonts

- [text()](https://processing.org/reference/text_.html) -- put text on the screen
- [textSize()](https://processing.org/reference/textSize_.html)
- [textFont()](https://processing.org/reference/textFont_.html) -- use a system font, or font created by `createFont()`
- [createFont()](https://processing.org/reference/createFont_.html)
- [loadFont()](https://processing.org/reference/loadFont_.html)

## 2D transformations

- [pushMatrix()](https://processing.org/reference/pushMatrix_.html)
- [popMatrix()](https://processing.org/reference/popMatrix_.html)
- [resetMatrix()](https://processing.org/reference/resetMatrix_.html)
- [translate()](https://processing.org/reference/translate_.html)
- [rotate()](https://processing.org/reference/rotate_.html)
- [scale()](https://processing.org/reference/scale_.html)

## 3D graphics

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