# Week 9: Files

## Overview

Welcome to Week 9! File handling lets your programs read and write data, making them truly useful for real-world applications.

## Watch: Files

:::{iframe} https://tdbowman.github.io/426python.github.io/videos/week09.html
:width: 100%
:label: week09-animation

**Week 9 animation (1:10).** Saving data so it outlives your program, and reading it back. Watch the code on the left, and what Python stores and prints on the right. Pause anytime.
:::

:::{dropdown} Text version of the animation
**Write a file**

- `open()` connects to a file. "w" means write. The with block closes the file for you when it ends.
- "w" creates loans.txt, empty and ready for writing.
- `write()` hands text to Python, which saves it to the file when it closes. `\n` is the newline character: it ends each line.
- When the with block ends, Python closes the file, and everything is saved to disk.

**"w" starts fresh**

- Later, a new title is checked out, so we run this program to save it.
- "w" empties the file the moment it opens. Dune and Beloved are already gone.
- Only Neuromancer is left. No error, just lost data.

**"a" appends**

- Start again from Dune and Beloved, and open with "a" for append instead.
- "a" keeps what's there and adds to the end.

**Read it back**

- With no mode, `open()` reads. A for loop goes through the file one line at a time.
- Each line arrives as a string that still ends in `\n`. `.strip()` removes it before printing. Even numbers in a file come back as strings.

**Key idea:** Use with `open()` to read and write files. "w" erases the file first, "a" adds to the end, and no mode means read. Everything you read back from a text file is a string.
:::

## Learning Objectives

- Open, read, write, and close files
- Use context managers (`with` statement)
- Handle different file modes
- Work with CSV files
- Process text files line by line
- Handle file errors gracefully

## Topics Covered

1. **File Basics**
   - Opening and closing files
   - File modes (r, w, a, r+, etc.)
   - The `with` statement

2. **Reading Files**
   - `read()` - Read entire file
   - `readline()` - Read one line
   - `readlines()` - Read all lines as list
   - Iterating over files

3. **Writing Files**
   - Writing text
   - Appending to files
   - Writing lists

4. **CSV Files**
   - Reading CSV with csv module
   - Writing CSV files
   - Working with headers

5. **Practical Applications**
   - Log files
   - Data processing
   - Configuration files
   - Reports

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Weekly Discussion** - Participate in forum


## Readings

**Required:**
- Mastrodomenico - Chapter 14
   - Parker - Chapter 5 
   - Review course materials on modules

**Recommended:**
- [Geeks for Geeks - File Handling](https://www.geeksforgeeks.org/python/file-handling-python/)


---

Let's start with [File Operations](files-basics.md)!
