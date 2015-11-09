---
title: Homework 11
layout: default
---

Skills needed to complete this assignment:

- [Inheritance](/lecture/inheritance.html) including abstract classes and `private` vs. `protected`

## Task 1

Define `BankAccount`, `CheckingAccount`, and `SavingsAccount` classes as follows:

- `BankAccount` is the parent of both `CheckingAccount` and `SavingsAccount`.
- `BankAccount` has a `protected double balance` field, and the initial balance is set by the constructor.
- `BankAccount` has two abstract methods: `void deposit(double amount)` and `void withdraw(double amount)`.
- `CheckingAccount` implements `deposit` as follows: cannot deposit negative amount; for `withdraw`, cannot withdraw negative amount, but otherwise can withdraw more money than exists in the account (thus making the balance negative).
- `SavingsAccount` implements `deposit` in a different way: cannot deposit negative amount; upon depositing, 2% extra money is deposited (this simulates interest); for `withdraw`, cannot withdraw more money than exists in the account.

Create a `main` function *in a separate class* that tests deposit/withdraw of a checking account and a savings account, **using polymorphism** (so save the accounts in variables with types `BankAccount`).
