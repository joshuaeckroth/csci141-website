---
title: Notes from class
layout: default
---

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