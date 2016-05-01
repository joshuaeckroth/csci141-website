---
title: Arrays
layout: default
---

Arrays are one way to store *many values of the same type in one variable*. An array can be of any size. If an array is of size `n`, then the *elements* (values) of the array can be accessed with indices `0` through `n-1`. Here is an example of how we create arrays, and give them their values:

![Create an array](/images/array-1_0.png "Create an array")

```
// "int[] arr" means create an integer array
int[] arr = {4,8,3,6,6,0};
System.out.println(arr.length); // prints 6 (count of items)
System.out.println(arr[0]);     // prints 4
System.out.println(arr[1]);     // prints 8
System.out.println(arr[5]);     // prints 0
```

We can change the values of an array in the same way:

![Modify an array](/images/array-2_0.png "Modify an array")

```
arr[1] = 9;
System.out.println(arr[0]);     // prints 4
System.out.println(arr[1]);     // prints 9 (different than above)
System.out.println(arr[5]);     // prints 0
```

Sometimes, we want to add values later. We can create an array with all default values (typically 0) like so:

```
int[] vals = new int[100]; // reserve space for 100 integers
```

## Assigning values

We can assign the values to an array with a loop if we don't want to type all the values individually. In this case, the array is created by specifying a size but the values are missing. Inside a `for()` loop we will set the values:

```
int[] vals = new int[100];
for(int i = 0; i < 100; i++)
{
    vals[i] = i*i*i + 10;  // assign each element some silly value
}
```

## Arrays of "variable" size

The size of an array cannot change once it is created. But we can decide how many elements we want by whatever means, such as asking the user:

```
Scanner in = new Scanner(System.in);
System.out.print("How many values? ");
int count = in.nextInt();

// make an array of the right size
double[] vals = new double[count];

// ... fill it up, possibly with input from the user ...
```

## Passing arrays to functions

See examples below. It's as simple as specifying an array in the parameter list of the function, e.g.

```
public static void prDoubleArr(double[] vals)
```

## Returning arrays from functions

Here is an example that generates a certain number of random doubles:

```
// requires import java.util.Random;
public static double[] makeRandomArray(int howMany)
{
    Random r = new Random();
    double[] xs = new double[howMany];
    for(int i = 0; i < howMany; i++)
    {
        xs[i] = r.nextDouble();
    }
    return xs;
}
```

Use that function like so:

```
double[] randVals = makeRandomArray(10);
```

## Example functions

### Print an array

```
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
```

### Min

Two approaches: look at every element, or sort the array first.

```
public static double min(double[] xs)
{
    double m = xs[0];
    for(int i = 0; i < xs.length; i++)
    {
        if(xs[i] < m)
        {
            m = xs[i];
        }
    }
    return m;
}

// requires import java.util.Arrays;
public static double min2(double[] xs)
{
    Arrays.sort(xs);
    return xs[0];
}
```

### Max

Two approaches: look at every element, or sort the array first.

```
public static double max2(double[] xs)
{
    Arrays.sort(xs);
    return xs[xs.length-1];
}

// requires import java.util.Arrays;
public static double max(double[] xs)
{
    double m = xs[0];
    for(int i = 0; i < xs.length; i++)
    {
        if(xs[i] > m)
        {
            m = xs[i];
        }
    }
    return m;
}
```

### Sum

<div>
$$
\text{sum} = \sum_i^n x_i,
$$
</div>

<p>
where $x_i$ is the i'th value in the array and $n$ is the length of the array.
</p>


```
public static double sum(double[] xs)
{
    double sum = 0;
    for(int i = 0; i < xs.length; i++)
    {
        sum = sum + xs[i];
    }
    return sum;
}
```

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

```
public static double mean(double[] xs)
{
    return sum(xs) / xs.length;
}
```

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

```
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
```

### Standard deviation

The standard deviation is the square root of variance.

```
public static double sd(double[] xs)
{
    return Math.sqrt(variance(xs));
}
```
