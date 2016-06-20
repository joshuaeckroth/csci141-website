--
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

```
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
```

Elsewhere, you would create a new object:

```
MyThread mythread = new MyThread();
```

And you would call `start()` and `stop()` at the appropriate times.

```
mythread.start();
mythread.stop();
```

## Sleeping

Sometimes you want a thread to pause for a small amount of time before continuing its work. This can be used for animation, to delay each picture before it is changed to the next one. `Thread.sleep()` takes a number of milliseconds as its argument. It also may throw an exception, so you need a `try/catch`. 

```
try {
	Thread.sleep(20);
} catch (InterruptedException e) {
	e.printStackTrace();
}
```

You would put this sleep code in your infinite loop in `run()`.

## Example with start/stop buttons

Main.java:

```
import java.awt.BorderLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.SwingUtilities;


public class Main {
	public static void gui() {
		final MyThread mythread = new MyThread();
		JFrame frame = new JFrame("My Frame!");
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.setSize(250,250);
		JPanel win = new JPanel(); // or JFrame
		win.setLayout(new BorderLayout());
		// use NORTH or SOUTH or EAST or WEST or CENTER
		JButton startButton = new JButton("start");
		startButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				mythread.start();
			}
		});
		JButton stopButton = new JButton("stop");
		stopButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				mythread.stop();
			}
		});
		win.add(startButton, BorderLayout.WEST);
		win.add(stopButton, BorderLayout.EAST);
		frame.add(win);
		frame.pack();
		frame.setVisible(true);
	}

	public static void main(String[] args)
	{
		SwingUtilities.invokeLater(new Runnable() {
			public void run() {
				gui();
			}
		});
	}
}
```

MyThread.java:

```
public class MyThread implements Runnable {
	private Thread runner;
	private int i = 0;

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
			System.out.println("Iteration " + i);
			i++;
			try {
				Thread.sleep(100);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}
}
```

