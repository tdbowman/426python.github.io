# Week 5: Loops

## Overview

Welcome to Week 5! Loops allow you to repeat code multiple times - essential for processing collections of data, automating repetitive tasks, and building powerful programs.

## Watch: Loops & Accumulators

:::{iframe} https://tdbowman.github.io/426python.github.io/videos/week05.html
:width: 100%
:label: week05-animation

**Week 5 animation (1:21).** Repeating the same steps for every item in a list. Watch the code on the left, and what Python stores and prints on the right. Pause anytime.
:::

:::{dropdown} Text version of the animation
**Add them up**

- A reading log: pages read on three days. A for loop runs the indented line once for each item in the list.
- total starts at 0. It's an accumulator: it builds up the answer as the loop runs.
- Pass 1: p is the first item, 40. total = total + p, so 0 + 40 = 40.
- Pass 2: p is 12. 40 + 12 = 52.
- Pass 3: p is 25. 52 + 25 = 77.
- No items left, so the loop ends and Python moves on to print.

**Find the minimum**

- Now find the slowest day, with the same pattern. But starting fewest at 0 is a trap.
- fewest starts at 0.
- Is 40 < 0? No. Is 12 < 0? No. Is 25 < 0? No. Line 5 never runs, so fewest never changes.
- No day had 0 pages! Python raised no error, but the answer is wrong: 0 beat every real value before the loop began.

**Start with real data**

- The fix: start with a real value from the list. `pages[0]` is the first item.
- fewest starts at 40.
- Pass 1 compares 40 with itself, so nothing happens. Pass 2: 12 < 40 is True, so fewest becomes 12.
- Pass 3: 25 isn't smaller, so fewest stays 12. Now the answer is right.

**Key idea:** A loop repeats the same steps for every item. An accumulator carries a result from one pass to the next. Start it with a value that can't win by accident: 0 for a total, but the first item (not 0) for a minimum or maximum.
:::

## Learning Objectives

By the end of this week, you will be able to:

- Use `for` loops to iterate over sequences
- Use `while` loops for conditional repetition
- Understand when to use each type of loop
- Use `range()` to generate sequences
- Control loop flow with `break` and `continue`
- Nest loops within loops
- Combine loops with functions

## Topics Covered

1. **For Loops**
   - Iterating over lists, strings, ranges
   - Loop variables
   - `range()` function
   - Looping with indices using `enumerate()`

2. **While Loops**
   - Condition-based looping
   - Avoiding infinite loops
   - Common while loop patterns
   - User input loops

3. **Loop Control**
   - `break` - Exit loop early
   - `continue` - Skip to next iteration
   - `else` clause with loops

4. **Nested Loops**
   - Loops within loops
   - Processing multi-dimensional data
   - Performance considerations

5. **Practical Applications**
   - Processing data collections
   - Accumulating values
   - Finding items
   - Validating input

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Exercise 4** - Loop the Loop (assigned this week)
- **Exercise 3** - Due this week
- **Weekly Discussion** - Participate in forum

## Readings

**Required:**
- Speight - Chapters 9, 10
   - Mastrodomenico, R. (2022) - Chapter 11 (Loops)
   - Parker - Chapter 2
   - Review course materials on loops

**Recommended:**
- [W3Schools - Python For Loops](https://www.w3schools.com/python/python_for_loops.asp)
- [W3Schools - Python While Loops](https://www.w3schools.com/python/python_while_loops.asp)
- [Real Python - For Loops](https://realpython.com/python-for-loop/)

## Key Concepts

```{important}
**Loops automate repetition.** Instead of writing the same code 100 times, write it once in a loop that runs 100 times.
```

### For vs While

**Use FOR when:**
- You know how many times to loop
- You're iterating over a collection
- You're using a counter/range

**Use WHILE when:**
- Looping until a condition is met
- You don't know how many iterations needed
- Getting user input until valid

## What You'll Build

This week you'll create programs that:
- Process lists of data
- Calculate totals and averages
- Find maximum/minimum values
- Validate user input repeatedly
- Generate patterns and sequences

## Tips for Success

1. **Start simple** - Single loops before nested ones
2. **Test small** - Use small datasets while learning
3. **Watch for infinite loops** - Make sure while conditions can become False
4. **Use descriptive loop variables** - Not just `i`, but `student`, `item`, etc.
5. **Print debug info** - See what's happening each iteration

---

Let's start with [For Loops](for-loops.md)!
