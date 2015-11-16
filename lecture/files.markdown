---
title: Files
layout: default
---

## File input

Use `FileInputStream` and `BufferedInputStream`

{% highlight java %}
FileInputStream is = new FileInputStream("filename.txt");
{% endhighlight %}

Possible exceptions:

- `FileNotFoundException`
- `SecurityException` -- if you're not allowed to read the file
- `IOException` -- some other problem reading the file

### `Scanner` for file input

{% highlight java %}
Scanner fin = new Scanner(is); // FileInputStream 'is' from above
int n = fin.nextInt(); // usual Scanner methods
{% endhighlight %}

## File output

Use a `PrintWriter` for text files.

{% highlight java %}
PrintWriter writer = new PrintWriter("filename.txt");
writer.println("Some text...");
writer.print(55); // print a number
writer.println(); // move to next line
writer.close();
{% endhighlight %}

Possible exceptions:

- `FileNotFoundException`
- `SecurityException` -- if you're not allowed to read the file
