---
title: Programming languages
layout: default
---

What follows is a short and imprecise history of the development of programming languages. Only the super interesting bits are discussed.

## Early programming: Get 'er done

The early languages imitated exactly how the computer works. The central processor starts executing a program from the first instruction (at the top of the diagrams below), and simply executes each following instruction, one at a time, until it runs out.

We can call this linear execution, because it just goes top to bottom.

![Linear execution](/images/execution-styles-linear.png)

Of course, few programs are linear. Most programs need to ask questions about data or about the world and do one thing or another depending. We can call this conditional execution. It means we might skip some code in certain situations. To skip code, the processor will need to "jump" over it, which we can cause with a `goto` statement and labels written `L1:` and similar.

![Conditional execution](/images/execution-styles-conditional.png)

Now that we have `goto` and labels, we can program looping behavior. Loops are like conditionals except that there is a backwards (non-conditional) jump as well (`goto L1` in the diagram below).

![Looping execution](/images/execution-styles-looping.png)

With these basic linear/conditional/looping execution techniques, we can create any program we want.

## Structured programming: A revolution

In large programs, all those `goto`'s produce really confusing code. We call it "spaghetti code," because if you look at any single line of code, you'll have a hard time figuring out under what circumstances that line of code is executed. (This is like spaghetti, really: pick a spot in the middle of some noodle and try to trace back to the noodle's beginning or end.)

The advent of "structured" languages like Pascal, C, C++, Java, etc. make `goto` unnecessary. (Some people required a lot of convincing that `goto` is unnecessary. [Dijkstra famously settled the case.](http://www.u.arizona.edu/~rubinson/copyright_violations/Go_To_Considered_Harmful.html))

In fact, it was eventually considered a faux pas to use `goto` in your code.

<div style="text-align: center"><a href="http://xkcd.com/292/"><img src="/images/xkcd-goto.png" alt="xkcd: goto"/></a></div>

### Rewriting without `goto`

The linear execution example stays the same (it did not use `goto`).

The conditional execution example is rewritten as shown.

![Structured conditional execution](/images/execution-styles-structured-conditional.png)

The looping execution example is rewritten as shown.

![Structured looping execution](/images/execution-styles-structured-looping.png)

Structured code uses "blocks" (which are indicated by `{` and `}`). Rather than using labels and `goto`'s, blocks indicate what code should be subject to a condition or iterated in a loop.

In most structured languages, code also lives in "functions." A function is another block, but this time with a name and, possibly, parameters. Here is a function in Java. I am assuming `stepA()` through `stepG()` are also functions, and they are executed in turn.

{% highlight java %}
void myfunction()
{
    stepA();
    stepB();
    int x = 1;
    while(x <= 10)
    {
        stepC();
        stepD();
        x = x + 1;
    }
    stepE();
    stepF();
    stepG();
}
{% endhighlight %}

## Object-orientation: The next frontier

While structured programming eliminated `goto`'s by creating nested blocks, contained in functions, many in the software industry felt that nested blocks inside functions was just not enough nesting. So they devised a way to gather several functions together, plus some data, into "classes." In Java, they went even further and added access restrictions to specify which functions and data in a class were accessible to other parts of code ("public") and which were not ("private").

![Functions and classes](/images/functions-classes.png)