---
title: Homework 10
layout: default
---

Skills needed to complete this assignment:

- [Exceptions](/lecture/exceptions.html)
- [Files](/lecture/files.html)

## Task 1

Create a music playing program. It will read a song script from a file and set up a series of timers for playing each instrument at the right time.

### Input file format

Each line in the input file is either blank or has two things:

  - an integer, representing the delay from the previous line, in milliseconds
  - a string, representing the instrument filename (without `.wav` at the end)

Here is an example. Download the slightly longer [song1.txt](/song1.txt) for testing. Also download this [ZIP of instruments](https://dl.dropboxusercontent.com/u/8041382/hw-sounds.zip).


```
250 kick
250 hat
250 kick-light
0 snare-rimshot
250 hat-2
250 kick
250 hat
250 kick-light
0 snare-rimshot
0 ride-bell-loud
```

:point_right: **Please consider making new songs, and sharing with all of us (email me).** I would really like to have better examples. You can use new instruments, too. :two_hearts:

### Java code

In your `main` function, first create a `Timer` object:

{% highlight java %}
Timer t = new Timer();
{% endhighlight %}

Next, open the file and read it. You can ask the user for the filename if you want, or just open the same file every time (e.g., "song1.txt"). Make sure to handle all appropriate exceptions (file not found, file can't be opened, etc.). Print a message if an exception occurs and then quit the program.

For each line in the file, get the first number (an integer) and then the instrument name (a string with no spaces). With this information, call the `schedule` method on your `Timer` object. Give this method a new `ClipPlayer` object (see below) and the correct delay (calculated from the beginning of the program; note the file specifies delays from the prior instrument, which is not the same thing).

You'll need a `ClipPlayer` class in addition to your main class. This class is responsible for loading the instrument file in the constructor and playing it when the timer goes off (that's the `run` method). Use this template.

{% highlight java %}
public class ClipPlayer extends TimerTask {
  private Clip clip; // leave this as-is; you don't need more fields
	
  // Here is the constructor. It is given a name like "snare",
  // and it opens a file called "snare.wav"; be sure to fill in
  // the "throws" part since it could throw many kinds of exceptions
  ClipPlayer(String instrument) throws ... (TODO)
  {
    // TODO: open instrument (.wav) as buffered input stream bis
    
    // Keep the code below to set up a clip object that can be played
    clip = AudioSystem.getClip();
    AudioInputStream inputStream = AudioSystem.getAudioInputStream(bis); // bis is used here
    clip.open(inputStream);
  }
  
  // leave this as-is; when the timer goes off, this method is executed
  @Override
  public void run() {
    clip.start();
  }
}
{% endhighlight %}

When you're reading the file and scheduling the timer, each time you execute `schedule` on your `Timer` object you want to give it a `new ClipPlayer(...)` for its first argument, and the correct delay for its second argument.

## Extra credit

Modify the file format so it support looping an instrument a specified number of times. In your code, modify to `ClipPlayer` so it can loop the clip:

{% highlight java %}
clip.loop(count);
{% endhighlight %}

You can use `clip.loop(0)` to just play it once, and thereby remove the need for `clip.start()`.

AND/OR:

Modify the file format so it supports volume. Look up (on the web) how to control the volume in Java using something like the `javax.sound.sampled.Control` class.
