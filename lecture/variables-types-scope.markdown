---
title: Variables, types, scope
layout: default
---

Variables are containers for values. Every (interesting) program you write will use variables. Here is an example of a variable:

```java
int x = 5;
```

That code sets up `x` (we can choose its name) to be a variable with type `int` (integer), and to have the value `5`. We can change the value later:

```java
x = 6;
```

And we can get the value back out of the variable and, for example, print this value:

```java
System.out.println(x);
```

When a variable is on the left-hand side of an `=` sign, we call it an `LVALUE`. Only a single variable can be an `LVALUE`. The right-hand side of the `=` is the `RVALUE` and can be anything you want.

```java
x        =  (y+3)*2;
^LVALUE     ^^^^^^^RVALUE
```

## Types

Every variable has a type. You cannot create a variable without explicitly giving it a type.

There are two categories of types. One is the "primitive" types. These are types that are simple values, not collections of values. The others are "class" types, which are complex structures composed of other class types and/or primitive types.

Every value in your code also has a type. For example, if you write `52` in your code, it will be an `int` type of value. If you write `52.0`, it will be a `double` type of value (see below). This is called the "literal syntax" of a small subset of types (the primitive types plus the `String` type).

### Primitive types

| Type | Size | Range | Literal syntax |
|------|------|-------|----------------|
| `byte` | 8 bits | -128, 127 | none |
| `short` | 16 bits | -32768, 32767 | none |
| `int` | 32 bits | -2<sup>31</sup>, 2<sup>31</sup>-1 | `52` |
| `long` | 64 bits | -2<sup>63</sup>, 2<sup>63</sup>-1 | `52L` |
| `float` | 32 bits | (complex; but less precise than `double`) | `52.0f` or `5.2e2f` |
| `double` | 64 bits | (complex; but more precise than `float`) | `52.0` or `5.2e2` |
| `boolean` | 1 bit | `true` or `false` | `true` or `false` |
| `char` | 16 bits | any of 65535 symbols | `x` or [`\u2665`](http://unicode-table.com/en/2665/) |

Summary:

- Use `int` for integer values
- Use `double` for decimal values
- Use `boolean` for true/false values
- Use `char` to represent single symbols

### Common class types

A class type always starts with a capital letter (notice all the primitives are lower-cased). A class type, or just "class," is a complex structure containing other class types and/or primitive types.

When we create variables of class types, we usually call them "objects" (not variables).

`String` is a common class. We can create an object of this type:

```java
String s;
```

We can give it a value as well.

```java
String s = "foo bar";
```

We see that the `String` class has a literal syntax (double-quotes). Anything typed in double-quotes is a `String` type of value.

All the other class types do not have a literal syntax. To create values of other classes, you must use the `new` keyword:

```java
FooBar f = new FooBar();
```

Here are some common class types:

| Class | Purpose | `import` | Example |
|-------|---------|----------|---------|
| `String` | for `"strings"` | no import needed | `String s = "foo bar";` |
| `Scanner` | for reading input | `import java.util.Scanner;` | `Scanner x = new Scanner(System.in);` |
| `Calendar` | for dates | `import java.util.Calendar;` | `Calendar now = Calendar.getInstance();` |


Some classes require that you indicate the kinds of classes to be used internally. For example, the `HashMap` class is a container that associates keys with values (one key for one value). It can use any type as the key and any type as the value. You must tell it which type is the key and which is the value. For example, below we'll make a `HashMap` with `String` keys and `int` values:

```java
HashMap<String, int> mymap = new HashMap<String, int>();
// put some stuff in the map
mymap.put("apple", 3);
mymap.put("banana", 0);
```

This feature is called "generics," because the `HashMap` class is generic, it can work with any two types.

### Arrays

## Scope

## Lifetime