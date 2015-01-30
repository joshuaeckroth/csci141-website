---
title: Notes from class
layout: default
---

## Processing example, wrap-around dots

{% highlight java %}
import processing.core.*;

public class TestProcessing extends PApplet {

        private float x;
	private float y;

	public void setup() {
    	size(800, 600);
    	background(255);
    	noStroke();
    	fill(0);
    }

    public void draw() {
    	int n = 33;
    	for(int i = 0; i < n; i++)
    	{
    		int row = i / 10; // how many 10's?
    		int col = i % 10; // how many cols after all 10's are gone?
    		int x = col * 25 + 25;
    		int y = row * 25 + 25;
    		ellipse(x, y, 10, 10);
    	}
    }
    
    public static void main(String[] args) {
        PApplet.main(new String[] { "TestProcessing" });
    }
}
{% endhighlight %}

## Euler problem 2, sum of even Fibonacci numbers

{% highlight java %}
public class Euler2 {

	public static void main(String[] args) {

		// Fibonacci sequence:
		// 1, 2, 3, 5, 8, 13, 21, 34, ...

		int a = 1;
		int b = 2;
		int c = 3;
		int sum = 0;
		while(c < 4e6)
		{
			// check if c is even
			if(c % 2 == 0)
			{
				sum = sum + c;
			}
			c = a + b;
			a = b;
			b = c;
		}
		System.out.println(sum);
	}
}
{% endhighlight %}
