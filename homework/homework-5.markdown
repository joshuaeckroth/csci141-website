---
title: Homework 5
layout: default
---

Skills needed to complete this assignment:

- [Loops](/lecture/loops.html)

## Task 1

Your task is to use for() loops and shapes and colors to **recreate
one of the following textures**. (**Recreate both for extra credit.**)
You must recreate them exactly (within a few pixels); use the colors
specified. You can use a different window size, if you want, but make
it big enough for the texture to repeat a few times. Colors are shown
in RGB values.

Background color can be drawn with `background(r, g, b)`, triangles
can be drawn with `triangle(x1, y1, x2, y2, x3, y3)`, ellipses can be
drawn with `ellipse(x, y, w, h)`, fill color can be set with `fill(r,
g, b)`, stroke (outline) color can be set with `stroke(r, g, b)`, and
stroke weight (thickness) can be set with `strokeWeight(n)`.

### Texture 1

<div style="text-align: center">
<img src="/images/texture-1.png" />
<br/>
</div>

Colors: green = (15, 243, 168), orange = (255, 186, 3), yellow = (255,
254, 3), other yellow = (255, 223, 94), red = (254, 58, 0), creamy
white = (255, 255, 219).

This pattern is just rows and columns of two triangles, facing
opposite directions. It is difficult to position the triangles
correctly. The color pattern is also difficult to get right; ask me
for advice on this if you get stuck (note, use modulo %). Your color
pattern need not exactly match the image, but they should be
"scattered" (but not random).

### Texture 2

<div style="text-align: center">
<img src="/images/texture-2.png" />
<br/>
</div>

Colors: background = (43, 48, 54), outer stroke = (74, 78, 87), inner
stroke 1 = (111, 115, 144), inner stroke 2 = (148, 143, 199), inner
stroke 3 = (185, 165, 252).

This is easiest if the ellipses are drawn from their centers, using
`ellipseMode(CENTER)`.


