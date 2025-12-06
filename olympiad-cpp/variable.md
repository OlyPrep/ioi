+++
title = "Variables"
template = "lesson.html"
description = "Learn how to store and manage data using variables in C++."
+++

## What is a Variable?

Think of a variable as a labeled box in your computer's memory where you can store a piece of information. The **label** on the box is the variable's name, and the **information** you put inside is its value. You can look at the value, which in C++ terms we say _accessing the variable_; and you can also change it by putting something new in the box. This operation of "putting something new" is called _assigning to a variable_, or simply _assignment_.

## Declaring a Variable

To create a variable in C++, you must **declare** it. This tells the computer what type of data the variable will hold and what its name will be. When you declare it, you can also give it an initial value.

```cpp
int score = 10;
```

Here's the breakdown:

- `int`: This is the **type**. `int` stands for integer, meaning this variable will store a whole number. [Built-in Types](@/ioi/olympiad-cpp/builtin-type.md) discusses in detail about the available data types and their properties.
- `score`: This is the **name** we've given our variable.
- `=`: This is the **assignment operator**. It takes the value on the right and puts it into the variable on the left.
- `10`: This is an _integer literal_, the **initial value** we are storing in the `score` variable.
- `;`: The semicolon marks the end of the statement.

You can also declare a variable without giving it an initial value right away.

```cpp
int temperature;
```

This creates a variable named `temperature` that is meant to hold an integer, but we haven't put anything inside it yet.

> **Warning: Uninitialized Variables**
>
> Accessing a variable that you haven't assigned a value to is a common source of a class of bugs called undefined behavior.
>
> Undefined behavior is a run-time error, but how the program will behave on this error is not defined, or in other words, the program is may do whatever random things (like crashing, appearing to run as normal, making your whole computer crash). Due to its unpredicatable nature, finding these type of bugs is incredibly time-consuming and frustrating.
>
> Therefore it's a good practice to declare variable with their initial value. **Always make sure you assign a value to a variable before you try to access it.**

### Choosing a Name

Coming up with a good name for a variable is an important skill. There are hard rules set by the C++ language, and also style conventions that make code easier to read.

#### Naming Rules (The "Musts")

These are the rules you must follow, or your code will not compile:

- Names can only contain letters (`a-z`, `A-Z`), digits (`0-9`), and underscores (`_`).
- Names cannot start with a digit. `1st_place` is invalid, but `first_place` is fine.
- Names are case-sensitive. `score`, `Score`, and `SCORE` are three different variables.
- Names cannot be a C++ keyword. You cannot name a variable `int`, `char`, `for`, `if`, `while`, etc.

#### Naming Suggestions (The "Shoulds")

These are conventions that make your code better, especially in competitive programming.

- **Pick Something Brief That Makes Sense To You:** In competitive programming, speed is important, so names should be short but still clear to you for the time you are writing the program and solving the problem.

- **Follow Common Conventions:** You will see certain variable names used over and over in competitive programming. It's a good idea to learn and use them:
    - `i`, `j`, `k` are almost always used for loop counters.
    - `n`, `m` are often used for sizes, like the number of elements in an array or nodes in a graph.
    - `t` is commonly used for the number of test cases.
    - `x`, `y`, `z` are often used for coordinates or temporary values.

- **Be Consistent:** Pick a style and stick with it. The two most common styles are:
    - `snake_case`: Words are separated by an underscore. (e.g., `my_score`, `first_place`). This is very common in C++.
    - `camelCase`: The first word is lowercase, and subsequent words are capitalized. (e.g., `myScore`, `firstPlace`).

## Try It

Let's see how variables work inside a full program. We will declare a variable, print its value, then assign a new value and print it again.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int score = 100;
    cout << "The initial score is: " << score << endl;

    score = 150;
    cout << "The updated score is: " << score << endl;

    return 0;
}
```

Compile and run it, it should give the following output:

```text
The initial score is: 100
The updated score is: 150
```

As you can see, the value stored in the `score` variable was updated after we assigned a new value to it.
