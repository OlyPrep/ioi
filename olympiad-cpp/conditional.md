+++
title = "Conditionals"
template = "lesson.html"
description = "Making decisions in your program."
+++

In life, we make decisions all the time: "_If_ it is raining, I will take an umbrella. _Otherwise_, I will wear sunglasses." Programs also need to make decisions to perform different actions based on different situations. This is called _conditional logic_.

In C++, we use conditional statements to control which blocks of code get executed.

## The `if` Statement

The `if` statement is the most fundamental tool for decision-making. It runs a block of code only if a certain condition is true. Its basic structure looks like this:

```cpp
if (condition) {
    // Code to execute if the condition is true
}
```

Here is a simple example:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int score = 100;

    if (score > 60) {
        cout << "You passed!" << endl;
    }

    return 0;
}
```

Let's break down how it works:

- The `if` keyword starts the statement.
- The `condition` part is the question being asked. In our example, the condition is `score > 60`. This expression evaluates to either `true` or `false`.
- The `{ ... }` block contains the code that will only run if the condition is `true`.

## What is a Condition?

A condition is an expression that results in a boolean value (`true` or `false`). The most common way to create conditions is by using **relational operators** to compare values.

| Operator | Name                     | Example      | Result (if `a=5, b=10`) |
| :------- | :----------------------- | :----------- | :---------------------- |
| `==`     | Equal to                 | `a == b`     | `false`                 |
| `!=`     | Not equal to             | `a != b`     | `true`                  |
| `>`      | Greater than             | `a > b`      | `false`                 |
| `<`      | Less than                | `a < b`      | `true`                  |
| `>=`     | Greater than or equal to | `a >= b`     | `false`                 |
| `<=`     | Less than or equal to    | `a <= b`     | `true`                  |

> **Warning:** A very common bug is to mix up the assignment operator (`=`) with the equality operator (`==`).
> - `if (x = 5)` **assigns** the value 5 to `x`.
> - `if (x == 5)` **compares** `x` to 5 and checks if they are equal.

## Combining Conditions

You can combine multiple conditions using **logical operators**.

| Operator | Name        | Example    | Result (if `a=true, b=false`) |
|:---------|:------------|:-----------|:------------------------------|
| `&&`     | Logical AND | `a && b`   | `false`                       |
| `\|\|`   | Logical OR  | `a \|\| b` | `true`                        |
| `!`      | Logical NOT | `!a`       | `false`                       |

- `&&` (AND) is `true` only if **both** conditions are `true`.
- `||` (OR) is `true` if **at least one** condition is `true`.
- `!` (NOT) inverts the value (`true` becomes `false`, `false` becomes `true`).

```cpp
int age = 25;
if (age >= 18 && age <= 60) {
    cout << "You are of working age." << endl;
}
```

## The `else` Statement

The `else` statement provides an alternative block of code to run when the `if` condition is `false`.

```cpp
int score = 32;

if (score >= 33) {
    // Above condition fails, so this line is skipped and execution jumps to the 'else' block
    cout << "You passed!" << endl;
} else {
    cout << "You did not pass. Better luck next time!" << endl;  // This is printed on screen
}
```

## The `else if` Statement

To check a multiple conditions one after another, you can use `else if`. As soon as one condition in the chain is met, its code block runs, and the rest of the chain is skipped.

```cpp
int score = 79;

if (score >= 80) {                // Condition fails, jump to the next condition check
    cout << "Grade: A+" << endl;  // Skipped
} else if (score >= 70) {         // Condition succeeds, run the code
    cout << "Grade: A" << endl;   // This will be printed, and jump to the end of last "else" block
} else if (score >= 60) {         // Skipped...
    cout << "Grade: A-" << endl;
} else {
    cout << "Grade: Too Bad, Barely Pass" << endl;
}
// Jumps to here after any code block is executed
```

## Nested Conditionals

You can put any kind of code inside a conditional statement, including another conditional statements. This is called _nesting_.

Nesting is very useful for checking a second condition only if the first condition is already true.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int num = 10;

    if (num > 0) {
        cout << "The number is positive." << endl;

        // This is a nested if statement
        if (num % 2 == 0) {
            cout << "And it is also even." << endl;
        } else {
            cout << "And it is also odd." << endl;
        }

    } else if (num < 0) {
        cout << "The number is negative." << endl;
    } else {
        cout << "The number is zero." << endl;
    }

    return 0;
}
```

In this example, the check for whether the number is even or odd (the inner `if`-`else`) only happens after we have already established that the number is positive (the outer `if`).

## The `bool` Type: Storing `true` and `false`

As you have learned, the result of any condition (like `age >= 18`) is a special value that is either `true` or `false`, called a _boolean value_. In C++, there is a specific builtin data type for storing these values: `bool`.

The `bool` type can only hold one of two values: `true` or `false`. These are called boolean literals.

You can declare a `bool` variable and assign a value to it just like any other builtin type:

```cpp
bool is_raining = true;       // Initialize with a boolean literal
bool is_sunny = !is_raining;  // Initialize with a condition
```

You can store the result of a condition in a `bool` variable to reuse it, and also to make your `if` statements cleaner and more readable. For example:

```cpp
int age = 20;
bool can_vote = (age >= 18); // The condition (age >= 18) evaluates to true, so can_vote becomes true

if (can_vote) {
    cout << "You are eligible to vote. Vote for your favorite Akib!" << endl;
} else {
    cout << "You are not yet eligible to vote. But soon you'll be!" << endl;
}

if (can_vote && age == 18) {
    cout << "Woah, new voter? Feeling excited? You should be!" << endl;
}
```
