# Week 3: Variables & Data Types (Advanced)

## Overview

Welcome to Week 3! This week we'll dive deeper into working with strings, learn how to get input from users, and master type conversions. You'll build on the foundation from Weeks 1-2 to create more interactive programs.

## Watch: Input Is Always a String

:::{iframe} https://tdbowman.github.io/426python.github.io/videos/week03.html
:width: 100%
:label: week03-animation

**Week 3 animation (1:02).** Getting data from the user, and converting it before you do math. Watch the code on the left, and what Python stores and prints on the right. Pause anytime.
:::

:::{dropdown} Text version of the animation
**Ask the user**

- `input()` shows a prompt, waits for the user to type, and gives back what they typed. Let's ask how many days a book is overdue.
- The user types 3. But look at memory: '3' in quotes, type str. `input()` always returns text, even when you type a number.

**Do the math**

- Late fees are 25 cents a day, so we multiply.
- Python stops: '3' is text, not the number 3. (Text times a whole number repeats it: `'3' * 2` is '33'. Text times 0.25 is an error.)

**Convert it**

- The fix: wrap `input()` in `int()`. `int()` converts the text '3' into the whole number 3.
- Same typing, but now memory holds 3 with no quotes: an int.
- Now the math works: 3 * 0.25 is 0.75.

**Show the result**

- An f-string starts with f before the quote. Each `{name}` inside it is filled in with that variable's value.
- `{fee}` becomes 0.75, and the patron sees their late fee.

**Key idea:** Everything `input()` gives you is a string. Even when the user types a number, you get text. Convert it with `int()` or `float()` before you do math with it.
:::

## Learning Objectives

By the end of this week, you will be able to:

- Use advanced string methods for manipulation
- Get user input with the `input()` function
- Validate and convert user input
- Format strings in multiple ways
- Work with escape characters
- Slice and manipulate strings efficiently
- Combine multiple concepts to solve problems

## Topics Covered

1. **String Methods**
   - `.upper()`, `.lower()`, `.title()`, `.capitalize()`
   - `.strip()`, `.lstrip()`, `.rstrip()`
   - `.replace()`, `.find()`, `.count()`
   - `.split()` and `.join()`
   - `.startswith()` and `.endswith()`

2. **User Input**
   - Using `input()` to get data from users
   - Understanding that all input is a string
   - Converting input to other data types
   - Validating user input
   - Handling common input errors

3. **String Formatting**
   - F-strings (formatted string literals)
   - `.format()` method
   - String concatenation review
   - Formatting numbers (decimals, percentages)

4. **Escape Characters**
   - Newline `\n`
   - Tab `\t`
   - Backslash `\\`
   - Quote marks within strings

5. **String Slicing**
   - Accessing individual characters
   - Slicing substrings
   - Negative indexing
   - Step values in slicing

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Exercise 2** - Due this week (from Week 2)
- **Weekly Discussion** - Participate in forum

## Readings

**Required:**
- Mastrodomenico, R. (2022) - Chapter 12

**Recommended:**
- [Python String Methods](https://www.w3schools.com/python/python_ref_string.asp)
- [Python Input Function](https://www.geeksforgeeks.org/taking-input-in-python/)
- [F-Strings Guide](https://realpython.com/python-f-strings/)

## Key Concepts

```{important}
**All input from users is a STRING!** Even if someone types "42", Python receives it as the string "42", not the integer 42. You must convert it if you need a number.
```

### Why String Manipulation Matters

In real-world programming:
- User input needs cleaning (removing spaces, fixing capitalization)
- Data from files or databases often needs formatting
- Building messages and reports requires string manipulation
- Validation ensures data quality

## What's Different This Week?

**Week 2** introduced basic data types and operations.  
**Week 3** focuses on:
- **Interactive programs** - getting input from users
- **String power** - manipulating text effectively
- **Real validation** - checking that input makes sense
- **Professional formatting** - making output look good

## Tips for Success

1. **Practice with `input()`** - Make every program interactive
2. **Experiment with string methods** - Try chaining multiple methods
3. **Always validate input** - Check types and values
4. **Use f-strings** - They're the modern, clean way to format
5. **Test edge cases** - What if user enters nothing? Or wrong type?

## Common Mistakes to Avoid

```{warning}
**Watch out for:**
- Forgetting to convert `input()` results to numbers
- Not handling empty strings from user input
- Confusing string index positions (remember: starts at 0!)
- Forgetting strings are immutable (can't change in place)
- Not validating user input before using it
```

## Real-World Applications

This week's concepts power:
- **Web forms** - validating user registration
- **Data cleaning** - preparing messy data for analysis
- **Chatbots** - processing user messages
- **Reports** - formatting output professionally
- **File processing** - reading and cleaning text files

## What's Next?

After Week 3, you'll move to Week 4 where you'll learn about **Functions** - how to organize code into reusable blocks that make programs more powerful and maintainable.

---

Let's start with [String Methods](string-methods.md)!
