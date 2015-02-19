---
title: Arrays
layout: default
---

Arrays are one way to store *many values of the same type in one variable*. An array can be of any size. If an array is of size `n`, then the *elements* (values) of the array can be accessed with indices `0` through `n-1`. Here is an example of how we create arrays, and give them their values:

![Create an array](/images/array-1_0.png "Create an array")

{% highlight java %}
// "int[] arr" means create an integer array
int[] arr = {4,8,3,6,6,0};
System.out.println(arr.length); // prints 6 (count of items)
System.out.println(arr[0]);     // prints 4
System.out.println(arr[1]);     // prints 8
System.out.println(arr[5]);     // prints 0
{% endhighlight %}

We can change the values of an array in the same way:

![Modify an array](/images/array-2_0.png "Modify an array")

{% highlight java %}
arr[1] = 9;
System.out.println(arr[0]);     // prints 4
System.out.println(arr[1]);     // prints 9 (different than above)
System.out.println(arr[5]);     // prints 0
{% endhighlight %}

Sometimes, we want to add values later. We can create an array with all default values (typically 0) like so:

{% highlight java %}
int[] vals = new int[100]; // reserve space for 100 integers
{% endhighlight %}

## Assigning values

We can assign the values to an array with a loop if we don't want to type all the values individually. In this case, the array is created by specifying a size but the values are missing. Inside a `for()` loop we will set the values:

{% highlight java %}
int[] vals = new int[100];
for(int i = 0; i < 100; i++)
{
    vals[i] = i*i*i + 10;  // assign each element some silly value
}
{% endhighlight %}

## Arrays of "variable" size

The size of an array cannot change once it is created. But we can decide how many elements we want by whatever means, such as asking the user:

{% highlight java %}
Scanner in = new Scanner(System.in);
System.out.print("How many values? ");
int count = in.nextInt();

// make an array of the right size
double[] vals = new double[count];

// ... fill it up, possibly with input from the user ...
{% endhighlight %}

## Passing arrays to functions

## Returning arrays from functions

## Example functions

### Print an array

{% highlight java %}
public static void prDoubleArr(double[] vals)
{
    System.out.print("{ ");
    for(int i = 0; i < vals.length; i++)
    {
        System.out.print(vals[i]);
        if(i < (vals.length - 1))
        {
            System.out.print(", ");
        }
        else
        {
            System.out.print(" ");
        }
    }
    System.out.println("}");
}
{% endhighlight %}

### Min

### Max

### Sum

<div>
$$
\text{sum} = \sum_i^n x_i,
$$
</div>

<p>
where $x_i$ is the i'th value in the array and $n$ is the length of the array.
</p>


{% highlight java %}
public static double sum(double[] xs)
{
    double sum = 0;
    for(int i = 0; i < xs.length; i++)
    {
        sum = sum + xs[i];
    }
    return sum;
}
{% endhighlight %}

### Mean

<p>
Often known as $\overline{x}$ for an array $x$:
</p>

<div>
$$
\overline{x} = \frac{\sum_i^n x_i}{n},
$$
</div>

<p>
where $x_i$ is the i'th value in the array and $n$ is the length of the array.
</p>

{% highlight java %}
public static double mean(double[] xs)
{
    return sum(xs) / xs.length;
}
{% endhighlight %}

### Variance

<p>
Often known as $s^2$:
</p>

<div>
$$
s^2 = \frac{\sum_i^n (x_i - \overline{x})^2}{n-1},
$$
</div>

<p>
where $x_i$ is the i'th value in the array, $\overline{x}$ is the mean of the array, and $n$ is the length of the array.
</p>

{% highlight java %}
public static double variance(double[] xs)
{
    double m = mean(xs);
    double s = 0.0;
    for(int i = 0; i < xs.length; i++)
    {
        s = s + (xs[i] - m)*(xs[i] - m);
    }
    return s / (xs.length - 1);
}
{% endhighlight %}
