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

{% highlight java %}
public class ClipPlayer extends TimerTask {
  private Clip clip;
	
  ClipPlayer(String instrument)
  {
    // TODO: open instrument (.wav) as buffered input stream bis
    
    clip = AudioSystem.getClip();
    AudioInputStream inputStream = AudioSystem.getAudioInputStream(bis); // bis is used here
    clip.open(inputStream);
  }
  
  // leave this as-is
  @Override
  public void run() {
    clip.start();
  }
}
{% endhighlight %}

## Extra credit

Modify the file format so it support looping an instrument a specified number of times. In your code, modify to `ClipPlayer` so it can loop the clip:

{% highlight java %}
clip.loop(count);
{% endhighlight %}

You can use `clip.loop(0)` to just play it once, and thereby remove the need for `clip.start()`.

