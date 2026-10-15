# Week 13: Robotics Simulation

## Overview

Welcome to Week 13! This is where everything comes together. You'll apply all your Python skills to build and control a virtual robot—no hardware required!

## Watch: Robotics: Sense, Decide, Act

:::{iframe} https://tdbowman.github.io/426python.github.io/videos/week13.html
:width: 100%
:label: week13-animation

**Week 13 animation (0:58).** A virtual robot that reads its sensors and chooses what to do. Watch the code on the left, and what Python stores and prints on the right. Pause anytime.
:::

:::{dropdown} Text version of the animation
**Set the scene**

- GridWorld, Robot, and GRID come from this week's textbook code. Our robot starts at row 0, col 0, heading east, among bookshelves (▥), with a goal (★).

**The loop**

- Each tick: sense the world, decide with if/else, then act. The # comments label each part.

**Run it**

- Tick 0: not at the goal, no obstacle ahead, so the else branch runs: move forward.
- Tick 1: still clear. Move again.
- Tick 2: `obstacle_ahead()` senses a shelf. The robot decides to turn right, and now heads south.
- Tick 3: the way south is clear. Move.
- Tick 4: move onto the goal square.
- Tick 5: `at_goal()` is True, so break ends the loop early. `range(12)` was only a safety limit.
- Five actions to reach the goal, all chosen by the robot itself.

**Key idea:** Robots sense, decide, and act, over and over. Each pass through the loop reads the sensors, picks an action with if/else, and changes the robot's state. A limit like `range(12)` keeps a confused robot from looping forever.
:::

## Learning Objectives

By the end of this week, you will be able to:

- Design and implement a virtual robot using OOP
- Create a grid-based simulation environment
- Implement robot sensors (distance, obstacle detection)
- Program decision-making algorithms
- Use the sense-think-act control loop
- Navigate a robot from start to goal
- Log and analyze robot behavior
- Debug autonomous systems

## Topics Covered

1. **Robotics Fundamentals**
   - What is robotics? (Sensing + Deciding + Acting)
   - Why simulation matters
   - Real-world applications

2. **Virtual Environment**
   - Grid-based worlds
   - Coordinates and positions
   - Obstacles and goals
   - Visualization

3. **Robot Design (OOP)**
   - Robot class structure
   - State (position, direction, status)
   - Methods (move, turn, sense)
   - Inheritance for different robot types

4. **Sensors**
   - Virtual distance sensors
   - Obstacle detection
   - Goal detection
   - Sensor data processing

5. **Decision-Making**
   - Sense-think-act loop
   - Conditional logic for navigation
   - Path planning basics
   - Handling stuck situations

6. **Control Systems**
   - Autonomous behavior
   - Manual vs automatic control
   - Event-driven programming
   - Error handling

## Assignments This Week

```{note}
This week focuses on building the foundation for your final capstone project
```

- **No formal assignment** - Focus on learning robotics concepts
- **Prepare for Week 14** - Start planning your capstone robot
- **Experiment** - Try different robot behaviors
- **Weekly Discussion** - Share robot ideas

## Key Concepts

```{important}
**Robotics = Sensing + Deciding + Acting**

This is the core loop:
1. **Sense** - Get information about the environment
2. **Decide** - Process data and choose action
3. **Act** - Execute the action
4. **Repeat** - Loop continuously
```


## Readings

**Required:**
- TBD

**Recommended**
- [RobotPy Documentation](https://robotpy.readthedocs.io/en/stable/)
- [Webots - Robotics Simulation Services](https://cyberbotics.com/)
- [Robot Framework](https://robotframework.org/)
   - [A New Python API for Webots Robotics Simulations. July 22, 2022.](https://proceedings.scipy.org/articles/majora-212e5952-016) 


---

Let's start with [Robotics Fundamentals](robotics-basics.md)!
