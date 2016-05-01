---
title: Conditionals
layout: default
---

## `boolean` operators

For the table below, assume we have:

```
boolean p = true;
boolean q = false;
```

| Operator | Meaning | Example |
|----------|---------|---------|
| `&&` | "and", true outcome requires both sides are true | `p && q` is `false` |
| `\|\|` | "or", true outcome requires either side is true | `p \|\| q` is `true` |
| `==` | "equal", true outcome requires both sides are the same (primitive or `String`) value or same object | `p == q` is `false`, `p == true` is `true`|
| `!=` | "not equal", opposite of `==` | `p != q` is `true`, `p != true` is `false` |
| `!` | "not", just negates a `boolean` value | `!p` is `false`, `!q` is `true` |

### Truth tables

We can figure out the truth of a complicated boolean expression by finding the truth-value of each part. We build a table for this operation because we need to keep track of all the different values that the variables/subexpressions may hold.

For what values of boolean variables `x`, `y`, and `z` make this true? `!(x || (y && !z))`

We break the expression into its variables and subexpressions and put them all in the table.

| `x` | `y` | `z` | `!z` | `y && !z` | `x \|\| (y && !z)` | `!(x \|\| (y && !z))` |
|---
| `true` | `true` | `true` | `false` | `false` | `true` | `false` |
| `true` | `true` | `false` | `true` | `true` | `true` | `false` |
| `true` | `false` | `true` | `false` | `false` | `true` | `false` |
| `true` | `false` | `false` | `true` | `false` | `true` | `false` |
| `false` | 	`true` | 	`true` | 	`false` | 	`false` | 	`false` | 	`true` |
| `false` | 	`true` | 	`false` | 	`true` | 	`true` | 	`true` | 	`false` |
| `false` | 	`false` | 	`true` | 	`false` | 	`false` | 	`false` | 	`true` |
| `false` | 	`false` | 	`false` | 	`true` | 	`false` | 	`false` | 	`true` |


## Arithmetic comparison operators

For the table below, assume we have:

```
int x = 5;
double y = 5.75;
```

| Operator | Meaning | Example |
|----------|---------|---------|
| `>` | "greater than" | `x > y` is `false` |
| `<` | "less than" | `x < y` is `true` |
| `>=` | "greater than or equal" | `x >= y` is `false` |
| `<=` | "less than or equal" | `x <= y` is `true` |

## `if`

The `if` pattern examines a boolean expression and, should the expression turn out to be `true`, a certain block of code is executed. Otherwise, the block of code is not executed.

```
if(x > 5)
    System.out.println("yay!");
```

Braces are required if you have more than one line of code after the `if`:

```
if(x > 5)
{
    System.out.println("yay!");
    System.out.println("yay!");
}
```

## `if`, `else`

We can attach an `else` to a prior `if` so that a different block of code is executed should the boolean expression turn out to be false. The `else` never has a boolean expression because `else` means "the `if` was false." Thus, `else` must always be attached to an `if` (after the `if`'s block of code).

```
if(x > 5)
{
    System.out.println("It seems x is greater than 5.");
}
else
{
    System.out.println("It seems x is less than or equal to 5.");
}
```

## `if`, `else if`, `else if`, etc.

A common pattern is an `if-else if` chain, which may be used for mutually exclusive options. For example, this `if-else if` chain checks for three possible values of the String variable `s`:

```
if(s == "foo")
{
   // do stuff
}
else if(s == "bar")
{
    // do stuff
}
else if(s == "baz")
{
    // do stuff
}
```

Sometimes, but not always, we put an `else` at the end of the chain to indicate "if the `if` and all the `else if`'s fail, then execute the code in the `else`."

```
if(s == "foo")
{
   // do stuff
}
else if(s == "bar")
{
    // do stuff
}
else if(s == "baz")
{
    // do stuff
}
else
{
    // apparently, s is not foo or bar or baz
    // do stuff
}
```

## `switch`

You can make an `if-else if` chain using `switch` as well, but only for numeric types (`int`, `char`, etc.) and `String`s. It works like this:

```
int x = ...;  // somehow, x gets a value
switch(x)
{
    case 1:
        System.out.println("x = 1");
        break;
    case 2:
        System.out.println("x = 2");
        break;
    default:
        System.out.println("x equals something else");
        break;
}
```

It works on `String`, too (example from [Oracle's Java tutorial](http://docs.oracle.com/javase/tutorial/java/nutsandbolts/switch.html)):

```
int month = 8;
String monthString;
switch (month) {
    case 1:  monthString = "January";
             break;
    case 2:  monthString = "February";
             break;
    case 3:  monthString = "March";
             break;
    case 4:  monthString = "April";
             break;
    case 5:  monthString = "May";
             break;
    case 6:  monthString = "June";
             break;
    case 7:  monthString = "July";
             break;
    case 8:  monthString = "August";
             break;
    case 9:  monthString = "September";
             break;
    case 10: monthString = "October";
             break;
    case 11: monthString = "November";
             break;
    case 12: monthString = "December";
             break;
    default: monthString = "Invalid month";
             break;
}
System.out.println(monthString);
```

That last example is the same as this `if-else if` chain:

```
int month = 8;
if (month == 1) {
    System.out.println("January");
} else if (month == 2) {
    System.out.println("February");
}
...  // and so on
```

If you don't include a `break` after a `case`, then the next `case` will execute as well. It will "fall into" the next `case`. Here is an example, again from [Oracle's Java tutorial](http://docs.oracle.com/javase/tutorial/java/nutsandbolts/switch.html). It determines the number of days in a particular month specified by the variable `month`. Notice that cases 1, 3, 5, 7, 8, 10, 12 (for January, March, May, etc.) are all treated as the same case.

```
int month = 2;
int year = 2000;
int numDays = 0;

switch (month) {
    case 1: case 3: case 5:
    case 7: case 8: case 10:
    case 12:
        numDays = 31;
        break;
    case 4: case 6:
    case 9: case 11:
        numDays = 30;
        break;
    case 2:
        if (((year % 4 == 0) && !(year % 100 == 0)) || (year % 400 == 0))
            numDays = 29;
        else
            numDays = 28;
        break;
    default:
        System.out.println("Invalid month.");
        break;
}
System.out.println("Number of Days = " + numDays);
```

## `? :` ternary operator

The final kind of conditional pattern is the ternary operator, named because it has three parts to it:

```
boolean_expression ? expresssion_when_true : expression_when_false;
```

You can only put expressions in those three parts, which limits you to mathematical expressions, function calls, and such, but no `if`'s or loops.

Here is an example that finds which of `a` or `b` is smaller:

```
(a < b) ? a : b;
```

You might want to save the smaller value:

```
int minval = (a < b) ? a : b;
```

Here is another example, for printing "Mr." or "Ms." depending on a person's gender:

```
System.out.println("Thank you " + (gender == "male" ? "Mr. " : "Ms. ") + lastName + ".");
```
