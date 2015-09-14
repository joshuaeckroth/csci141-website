---
title: Homework 10
layout: default
---

Skills needed to complete this assignment:

- [Inheritance](/lecture/inheritance.html)

## Task 1

Create classes that represent this hierarchy:

![Thing, food, armor, etc.](/images/thing-food-armor-etc.png)

Use Eclipse functionality to create constructors and getters/setters for all the fields, as well as `toString` methods. Do not customize the generated methods. Do this for every class.

## Task 2

Describe, in English but referring to Java terminology and examples, how polymorphism works (2-4 sentences).

## Task 3

Create two classes: `Foo` and `Bar`, such that `Bar` is a subclass of `Foo`. Create method in both called `go()` so that the following polymorphism works:

{% highlight java %}
Foo a = new Foo();
a.go();  // prints "Foo go!"
Bar b = new Bar();
b.go();  // prints "Bar go!"
Foo c = new Bar();
c.go();  // prints "Bar go!"
{% endhighlight %}

## Task 4

Suppose you have these two classes:

{% highlight java %}
public class BankAccount {
  private double balance;
  private String owner;
  
  public BankAccount(double balance, String owner) {
    this.balance = balance;
    this.owner = owner;
  }
  
  public String getOwner() {
    return owner;
  }
  
  public double getBalance() {
    return balance;
  }
}

public class JointAccount extends BankAccount {
  private String name1;
  private String name2;
  
  public JointAccount(double balance, String name1, String name2) {
    // TODO ...
  }
  
  public String toString() {
    // TODO ...
  }
}
{% endhighlight %}

Finish the code for `JointAccount` so that the constructor calls the parent's constructor with `owner` equal to `(name1 + "&" + name2)` and so that the `toString()` method prints something like:

```
Joint account for John Doe and Jane Doe. Balance = $55.22.
```

Do not modify `BankAccount` to accomplish this task. Only add code in `JointAccount`, and only in the two methods shown (where the `TODO ...` appears).

## Extra credit

Add more code to the classes in Task 1. Create at least three new methods (which are appropriate for the classes in which they appear), and test each of them in the `main` function. One of these tests must use polymorphism.
