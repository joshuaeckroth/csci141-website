---
title: Homework 7
layout: default
---

Skills needed to complete this assignment:

- [Classes](/lecture/classes.html)

Note: Each class needs to be in its own file. Eclipse will do this for you if you use the menus to create a new class.

## Task 1

(1) Identify the constructor in this code, and list its parameters:

{% highlight java %}
public class Video
{
  private int length;
  private String creator;

  public void play() { ... }
  public void pause() { ... }
  public void rewind() { ... }
  public Video(int l, String c) { ... }
  public int getLength() { ... }
  public String getCreator() { ... }
  public void setCreator(String c) { ... }
}
{% endhighlight %}

(2) Identify the "fields" of the above class (give their types and names).

(3) Write code for the "getters" and "setters", i.e., `getLength`, `getCreator`, and `setCreator`.

## Task 2

Create a class to represent a student. This class should not be your main class (not the class with the `main` method). It should contain this information:

- First name and last name (separately).
- 800-number ID.
- Birthdate. Use a variable of type `Calendar` and set it equal to something like this: `birthdate = GregorianCalendar.getInstance()`, and then in your constructor or "setter" method change the calendar date like so: `birthdate.set(1990, 12, 31)` for 12/31/1990.

That information should be `private` in the class. Create "getters" and "setters" for the data. Create a constructor that initializes the data with arguments given to the constructor.

Create a `toString` method to print the student info in a friendly format. You can convert the birth date into a string using the following technique (assuming your `birthdate` variable has type `Calendar`):

{% highlight java %}
SimpleDateFormat birthdateFormat = new SimpleDateFormat("yyyy-MM-dd");
String birthdateString = birthdateFormat.format(birthdate.getTime());
{% endhighlight %}

You can choose other formats if you don't like `yyyy-MM-dd` (e.g., "1990-12-31"). See the [SimpleDateFormat docs](http://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html) for details.

Test each method in your class. Create some fake student data, use the getters and setters, print the student data in a friendly format. Use the `main` function in your main class for these tests.

## Task 3

Create a bank account class that has the following functionality:

- You can create a bank account with a certain initial balance (i.e., the constructor has a parameter that sets the initial balance).
- You can deposit money into the account. Obviously, this action modifies the balance.
- You can withdraw money from the account, but only if it will not cause the balance to go negative. If the balance would go negative, the withdrawal doesn't actually occur.
- You can get the current balance, but not set the balance (except by using `withdraw` and `deposit`, as described).
- You can print the bank account in a friendly readable format (e.g., using just `System.out.println(b)` in your `main`, where `b` is a bank account object). This is accomplished by creating a `toString` method in the bank account class.
