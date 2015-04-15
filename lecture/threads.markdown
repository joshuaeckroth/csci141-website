---
title: Threads
layout: default
---

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

{% highlight java %}
mythread.start();
mythread.stop();
{% endhighlight %}

{% highlight java %}
try {
	Thread.sleep(20);
} catch (InterruptedException e) {
	e.printStackTrace();
}
{% endhighlight %}
