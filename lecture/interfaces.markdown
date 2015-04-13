---
title: Interfaces
layout: default
---

## Anonymous classes

{% highlight java %}
public interface Ball {
    void hit();
}

public class Foo {
    public static void main(String[] args) {
    
        // create an anonymous (nameless) class that implements an interface,
        // and immediately create an instance
        Ball b = new Ball() {
            public void hit() {
                System.out.println("You hit it!");
            }
        };
        b.hit();
    }
}
{% endhighlight %}

