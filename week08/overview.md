# Week 8: Modules

## Overview

Welcome to Week 8! Modules let you organize code into reusable files and access Python's vast standard library. You'll learn to import existing modules and create your own.

## Watch: Modules

:::{iframe} https://tdbowman.github.io/426python.github.io/videos/week08.html
:width: 100%
:label: week08-animation

**Week 8 animation (1:01).** Splitting a program across files, and reusing code with import. Watch the code on the left, and what Python stores and prints on the right. Pause anytime.
:::

:::{dropdown} Text version of the animation
**Write a module**

- Any .py file can be a module. Here's fines.py: a daily rate, a maximum fine, and a function that calculates a late fine.

**Import it**

- In a separate file, main.py, import fines loads that module so we can use it.
- import runs fines.py once and keeps everything it defined inside a module object named fines.
- fines.calculate means “calculate, from inside fines.” 6 days × 0.25 = 1.5.
- 60 days would be 15.0, but `min()` caps it at MAX_FINE: 10.0.

**Common slip**

- A common slip: leaving off the module name.
- calculate lives inside fines, not in main.py, so Python can't find it on its own.

**from … import**

- Or import just the name you need. from fines import calculate lets you call it directly.
- Same results. Now calculate is a name in main.py itself.

**Key idea:** A module is just a .py file you can import. Use module.name to reach what's inside, or from module import name to bring one name in. Your own files and Python's standard library (math, datetime, …) work the same way.
:::

## Learning Objectives

By the end of this week, you will be able to:

- Understand what modules are and why they're useful
- Import and use Python's standard library modules
- Use different import syntax (import, from...import, as)
- Create your own modules
- Organize code across multiple files
- Use the `dir()` and `help()` functions
- Understand module search paths

## Topics Covered

1. **Module Basics**
   - What are modules?
   - Why use modules?
   - The import statement

2. **Standard Library Modules**
   - `math` - Mathematical functions
   - `random` - Random number generation
   - `datetime` - Date and time handling
   - `os` - Operating system interface
   - `sys` - System-specific parameters

3. **Import Variations**
   - `import module`
   - `from module import function`
   - `import module as alias`
   - `from module import *` (avoid!)

4. **Creating Your Own Modules**
   - Writing a module file
   - Using your modules
   - `if __name__ == "__main__":`
   - Module best practices

5. **Packages**
   - What are packages?
   - Package structure
   - `__init__.py` files

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Assignment 2** - Assigned this week
- **Exercise 5** - Due this week (from Week 7)
- **Weekly Discussion** - Participate in forum

## Readings

**Required:**
- Speight - Chapter 13
- Mastrodomenico - Chapter 16
   - Review course materials on modules

**Recommended:**
- [Python Docs - Modules](https://docs.python.org/3/tutorial/modules.html)
- [Python Docs - Standard Library](https://docs.python.org/3/library/)
- [RealPython - Modules/Packages](https://realpython.com/python-modules-packages/)

## Key Concepts

```{important}
** Modules are Python files.** Any `.py` file can be imported as a module.
** This lets you organize large programs into manageable pieces.
```

### Why Modules Matter

- **Code Reuse** - Write once, use everywhere
- **Organization** - Break large programs into files
- **Namespaces** - Avoid name conflicts
- **Standard Library** - Access thousands of pre-built functions
- **Third-party Packages** - Use code from the community

---

Let's start with [Module Basics](modules-basics.md)!
