---
title: Functions
layout: default
---

The purpose of a function is to give a "name" to a chunk of code. Now that the code has a name, it can be executed just by referring to its name. We can avoid copy-pasting code to different parts of a program by using functions and referring to the same chunk of code in different situations, just by using its name.

A function may or may not give back, or **return** a value. If it does, it can only return one value, though, that single value could be a container holding many values.

A function may or may not have **parameters**. An example of a parameter may be found in the `sqrt` function (square root). It is defined to find the square root of any number `x`. So `x` would be its parameter. To use a function that has one or more parameters, these parameters must be given values. The values are called **arguments**. In this usage, `sqrt(52)`, the `52` is the argument for the `x` parameter.

Note, functions are also called **methods** and certain kinds of functions (**void** functions) are sometimes called **procedures**.

## Function template

Every function looks like this:

```
public static [void/int/double/...] functionname(int x, double y, ...)
```

- The `public` part will sometimes be `private` in our future programs.

- We will not always use `static`, but for now we will.

- The `[void/int/double/...]` is the return type. Choose `void` or `int` or whatever.

- The `functionname` can be any name you like, as long as it does not have spaces or weird symbols, and does not start with a number.

- The `int x, double y, ...` can be any list of parameters (with types), or empty (just empty parens: `functionname()`).

## Void functions ("procedures")

Void functions, or procedures, do not return any value. They are typically used to print or draw something on the screen, or to update a variable.

Here is an example:

```
public static void printHelloWorld()
{
    System.out.println("Hello, world!");
}
```

## Non-void functions

Non-void functions return some type of value. The type of value must be specified before the function name. Also, inside the function, you must have `return ...` where the `...` is a value (or variable) of the right type. You may have multiple `return` statements, but every time the function is executed, it must reach one of these `return` statements. Once a `return` statement is reached, the function quits (and gives back the returned value).

Here is an example of a function that returns an `int`:

```
public static int generate42()
{
    return 42;
}
```

When calling a function that returns, you almost always want to save or otherwise use the value it returns:

```
int mynumber = generate42();
```

## Functions with arguments

Most functions require arguments to be useful. Here is an example of a function that returns the Euclidean distance between two x,y pairs:

```
public static double euclideanDistance(double x1, double y1, double x2, double y2)
{
    double sum = (x2-x1)*(x2-x1) + (y2-y1)*(y2-y1);
    return sqrt(sum);
}
```

That function might be used like so:

```
double a = 2.2;
double b = 1.4;
double dist = euclideanDistance(a, b, 3.5, 7.0);
```

Note, if you use variables for arguments (like `a` and `b` above), the names of these variables do not need to match the parameter names. Only the function knows the parameter names. The parameters are local variables, their scope is limited to the function itself.

Here is a void function that prints a log message:

```
public static void log(String source, String msg)
{
    System.out.println("Message from " + source + ": " + msg);
}
```

That function might be used like so:

```
log("nuclear_reactor", "All systems nominal.");
```

## Arbitrary number of arguments

A function can receive an arbitrary number of arguments by using the special syntax `...` in its parameter list. The actual values are received in an array. Although we have not learned about arrays yet, you may still be curious how this works.

Here is an example of finding the maximum number among a list of arguments:

```
public static int maxNumber(int... nums)
{
    if(nums.length > 0)
    {
        int max = nums[0];
        for(int i = 0; i < nums.length; i++)
        {
            if(nums[i] > max)
            {
                max = nums[i];
            }
        }
        return max;
    }
    else
    {
        System.out.println("Can't find max of zero arguments.");
        return -1;
    }
}
```

Here are a few uses of this function:

```
int max1 = maxNumber(3, 2, 6, 4);
int max2 = maxNumber(77);
int max3 = maxNumber(); // error case, returns -1
```

## Overloading functions

You can create different versions of a function but use the same name, as long as you change the parameters. Depending on the arguments you give, a matching version of the function will be used.

Here is an example from [Oracle's tutorial](http://docs.oracle.com/javase/tutorial/java/javaOO/methods.html).

```
public void draw(String s) {
    ...
}
public void draw(int i) {
    ...
}
public void draw(double f) {
    ...
}
public void draw(int i, double f) {
    ...
}
```

That tutorial also says,

> You cannot declare more than one method with the same name and the same number and type of arguments, because the compiler cannot tell them apart.

> The compiler does not consider return type when differentiating methods, so you cannot declare two methods with the same signature even if they have a different return type.

