---
title: Simple input/output
layout: default
---

Before we switch to graphics with the [Processing library](/lecture/processing-library.html), we'll practice the more common console input/output.

## Console output

The console can show a stream of text (and nothing more). It is sometimes referred to as "standard out" or "stdout". In Java, you have two functions that print to stdout: `System.out.print()` and `System.out.println()`.

```
System.out.print("Hello, ");
System.out.print("World!"); // on same line as previous

System.out.println("Hello, ");
System.out.print("World!"); // on next line, since previous added a newline
```

## Formatted output

You can choose how numbers are formatted in your output. Instead of `System.out.println` use `System.out.format`. Type your whole message inside the quotes, using `%d` wherever you want an integer, `%f` wherever you want a floating point value, `%s` wherever you want a String, and `%n` wherever you want a newline. Then, put all the variables you want to show up in place of `%d` etc. after the quotes, separated by commas.

You can choose how many digits to show by including a number before `%d` or `%f`. Add a `0` before that number to pad the number with zeros. If you put a number after a `.` before `%f`, you can choose how many numbers to show after the decimal point.

```
long n = 461012;
System.out.format("%d%n", n);      //  -->  "461012"
System.out.format("%08d%n", n);    //  -->  "00461012"
      
double pi = Math.PI;
System.out.format("%f%n", pi);       // -->  "3.141593"
System.out.format("%.3f%n", pi);     // -->  "3.142"
```

### String manipulation

We have already looked at [variables](/lecture/variables-types-scope.html). You can print a variable's value in the usual way:

```
int x = 2;
System.out.println(x);
```

But due to the way strings work in Java (the `String` type), you can use the `+` operator to concatenate (join) a string and other variable types before printing.

```
String name = "Slim Shady";

String s = "My name is: ";
String s2 = s + n; // s2 equals "My name is: Slim Shady"
System.out.println(s2);

// easier:
System.out.println("My name is: " + name);

// works with integers, doubles, etc.
int x = 2;
System.out.println("The value of x is: " + x);

double pi = 3.14;
System.out.println("PI = " + pi + ", approximately.");
```

## Console (keyboard) input

Input from the console comes from "standard input", a.k.a. "stdin", which in Java is `System.in` (to mirror `System.out` for console output).

Console input usually means keyboard input. You can feed a text file into a program, in which case stdin means "read from the file." But usually, reading from stdin in your code will cause the program to wait for you to type on the keyboard and (typically) press enter.

Reading from stdin is more complicated than writing to stdout. We have to indicate the type of value we're reading in because we'll be saving those values into particular variables (such as `int` variables). Unless we indicate which variable type to convert to, all input looks like a `String`.

### Scanner

A typical technique for reading from stdin is to use a `Scanner` object. You can read from files using `Scanner` as well as stdin, but for now we'll focus on stdin.

Create a new `Scanner` object like so:

```
// requires: import java.util.Scanner;

Scanner in = new Scanner(System.in); // note, you don't have to name your object "in"
```

Now you can use your `in` object to call various functions that read different types of values from stdin.

```
String word = in.next(); // grab input until a space/newline is reached
String line = in.nextLine();
int x = in.nextInt();
double y = in.nextDouble();
```

You can also check if the input contains an integer, or whatever. These examples use [conditionals](/lecture/conditionals.html), which we'll look at soon.

```
// is there anything at all left to read?
if(in.hasNext())
{
    // read something, e.g., a String
    word = in.next();
}

// is there an integer waiting to be read?
if(in.hasNextInt())
{
    x = in.nextInt();
}
```
