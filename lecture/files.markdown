---
title: Files
layout: default
---

## `FileInputStream` and `BufferedInputStream`

{% highlight java %}
FileInputStream is = new FileInputStream("filename.txt");
{% endhighlight %}

Possible exceptions:

- `FileNotFoundException`
- `SecurityException` -- if you're not allowed to read the file
- `IOException` -- some other problem reading the file

{% highlight java %}
BufferedInputStream bis = new BufferedInputStream(is); // FileInputStream 'is' from above
{% endhighlight java %}

## `Scanner` for file input

{% highlight java %}
Scanner fin = new Scanner(is); // FileInputStream 'is' from above
int n = fin.nextInt(); // usual Scanner methods
{% endhighlight %}


