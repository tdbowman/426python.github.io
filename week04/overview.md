# Week 4: Functions

## Overview

Welcome to Week 4! Functions are one of the most important concepts in programming. They let you organize code into reusable blocks, making your programs more efficient, readable, and maintainable.

## Watch: Functions: print vs. return

:::{iframe} https://tdbowman.github.io/426python.github.io/videos/week04.html
:width: 100%
:label: week04-animation

**Week 4 animation (1:18).** Why a function that shows the right answer can still hand back nothing. Watch the code on the left, and what Python stores and prints on the right. Pause anytime.
:::

:::{dropdown} Text version of the animation
**Define it**

- def defines a function: a named set of steps you can reuse. days is a parameter, a placeholder for the value we pass in.
- Running the def line doesn't calculate anything. Python just stores the function under the name late_fee, ready to call.

**Call it**

- Now call it for a book 6 days late, store the answer in fee, and print a message.
- Line 4 calls `late_fee(6)`. Python jumps into the function, and days becomes 6. days is local: it exists only inside the function.
- Line 2 prints 1.5. Looks like it worked…
- …but `print()` only puts a value on the screen. The function has no return, so it hands back None, and None is what fee gets.
- So the message says None. This is the classic print-versus-return mix-up.

**Return it**

- The fix: replace print with return. return sends the value back to the line that called the function.
- Run again. Line 4 calls `late_fee(6)`, and days is 6.
- Line 2 works out 6 * 0.25 and returns 1.5. Nothing prints: the value travels back to line 4 instead.
- fee now holds 1.5. And days is gone: local variables disappear when the function finishes.
- The message has the real fee, and fee is ready to use again later.

**Key idea:** `print()` shows a value. return sends it back. If you need the answer later (to store it, compare it, or print it in a message), the function must return it. A function with no return hands back None.
:::

## Learning Objectives

By the end of this week, you will be able to:

- Define and call functions
- Use parameters and arguments
- Return values from functions
- Understand scope (local vs global variables)
- Write function docstrings
- Use default parameter values
- Create functions that call other functions

## Topics Covered

1. **Function Basics**
   - What are functions and why use them?
   - Defining functions with `def`
   - Calling functions
   - Function naming conventions

2. **Parameters and Arguments**
   - Positional parameters
   - Keyword arguments
   - Default parameter values
   - Multiple parameters

3. **Return Values**
   - Using `return` statement
   - Returning multiple values
   - Functions without return (None)

4. **Scope**
   - Local variables
   - Global variables
   - When to use each

5. **Documentation**
   - Writing docstrings
   - Using `help()` function
   - Professional function documentation

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Assignment 1** - Assigned this week (Data Processing with Lists and Tuples)
- **Exercise 3** - Fun with Functions (assigned this week)
- **Weekly Discussion** - Participate in forum

## Readings

**Required:**
- Speight - Chapter 11
   - Parker, J. R. (2021) - Chapter 4
   - Review course materials on functions

**Recommended:**
- [W3Schools - Python Functions Tutorial](https://www.w3schools.com/python/python_functions.asp)
- [Real Python - Defining Functions](https://realpython.com/defining-your-own-python-function/)
- [Geeks for Geeks - User-Defined Functions](https://www.geeksforgeeks.org/python/python-user-defined-functions/)

## Key Concepts

```{important}
**Functions are reusable code blocks.** Write once, use many times. This follows the DRY principle: **Don't Repeat Yourself**.
```

### Why Functions Matter

- **Organization** - Break complex problems into smaller pieces
- **Reusability** - Write code once, use it many times
- **Testing** - Easier to test small, focused functions
- **Maintenance** - Changes in one place affect all uses
- **Collaboration** - Team members can work on different functions

## What You'll Build

This week you'll create:
- Calculator functions
- Validation functions
- Data processing functions
- Utility functions for common tasks

## Tips for Success

1. **Start simple** - Begin with functions that take no parameters
2. **Name clearly** - Function names should describe what they do
3. **One task** - Each function should do one thing well
4. **Document** - Always write docstrings
5. **Test** - Try your functions with different inputs

---

Let's start with [Function Basics](functions-basics.md)!
