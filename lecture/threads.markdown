---
title: Threads
layout: default
---

A thread is a process that runs in parallel with other threads in your program. So far, we have been creating programs with just one thread.

But GUI programs often have two or more threads. One thread is for the GUI, so it can respond to your clicks and update animations, etc. The other threads are for processing. If you had one thread in a GUI application, then whenever heavy processing was taking place, the GUI would be unresponsive.

## `Runnable` interface

You can create a custom class that does its computation in a separate thread. You need to implement the `Runnable` interface, which has one requirement:

- you must implement a `void run()` method that executes the processing for this thread

Sometimes, we put some kind of infinite loop in `run()` so the thread runs continuously. We also sometimes add a `start()` and `stop()` method that starts or stops the thread's infinite loop.

## Example

The class below defines a thread that does something forever. It also has start/stop methods.

(Technically, this class creates a `Thread` object (which also implements `Runnable`) inside as a private field, and tells it to do the work.)

{% highlight java %}
public class MyThread implements Runnable {
    private Thread runner;
    
    public void start()
	{
		if(runner == null)
		{
			runner = new Thread(this);
			runner.start();
		}
	}
	
	@SuppressWarnings("deprecation")
	public void stop()
	{
		if(runner != null)
		{
			runner.stop();
			runner = null;
		}
	}
	
	public void run()
	{
		while(true)
		{
		    // this is how we do... do do do do...
		    
		    // (i.e., do something here, forever and ever)
		}
   }
}
{% endhighlight %}

Elsewhere, you would create a new object:

{% highlight java %}
MyThread mythread = new MyThread();
{% endhighlight %}

And you would call `start()` and `stop()` at the appropriate times.

{% highlight java %}
mythread.start();
mythread.stop();
{% endhighlight %}

## Sleeping

Sometimes you want a thread to pause for a small amount of time before continuing its work. This can be used for animation, to delay each picture before it is changed to the next one. `Thread.sleep()` takes a number of milliseconds as its argument. It also may throw an exception, so you need a `try/catch`. 

{% highlight java %}
try {
	Thread.sleep(20);
} catch (InterruptedException e) {
	e.printStackTrace();
}
{% endhighlight %}

You would put this sleep code in your infinite loop in `run()`.
