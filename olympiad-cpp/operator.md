+++
title = "Operators"
template = "lesson.html"
description = "Performing operations on literals and variables."
+++

In C++, operators are special symbols that perform operations on one or more operands (variables or literals). Think of them as verbs in a sentence, telling the program what action to take with your data.

For example, in `x = 5 + 3`, `+` is an operator that performs addition, and `=` is an operator that performs assignment. `x`, `5`, and `3` are the operands.

## Arithmetic Operators

These operators perform basic mathematical calculations.

| Operator | Name           | Example     | Result (if `a=10, b=3`) |
| :------- | :------------- | :---------- | :---------------------- |
| `+`      | Addition       | `a + b`     | 13                      |
| `-`      | Subtraction    | `a - b`     | 7                       |
| `*`      | Multiplication | `a * b`     | 30                      |
| `/`      | Division       | `a / b`     | 3 (integer division)    |
| `%`      | Modulo         | `a % b`     | 1 (remainder)           |

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int a = 10;
    int b = 3;

    cout << "a + b = " << a + b << endl; // 13
    cout << "a - b = " << a - b << endl; // 7
    cout << "a * b = " << a * b << endl; // 30

    // Integer Division vs. Floating-point Division (Using Type Cast)
    cout << "a / b (int) = " << a / b << endl; // 3 (truncates decimal part)
    cout << "a / b ('a' casted to double) = " << (double)a / b << endl; // 3.333...

    // Modulo Operator: gives the remainder of a division
    cout << "a % b = " << a % b << endl; // 1 (10 divided by 3 is 3 with remainder 1)
    cout << "12 % 5 = " << 12 % 5 << endl; // 2

    return 0;
}
```

####  Important Note on Division:

- When both operands of `/` are integers, C++ performs **integer division**, which truncates any decimal part (it does not round). For example, `10 / 3` is `3`, not `3.33`. `7 / 2` is `3`, not `3.5`.
- If at least one operand is a floating-point type (e.g., `double` or `float`), then **floating-point division** is performed, and the result will include the decimal part.

## Assignment Operators

Assignment operators are used to assign a value to a variable. The most basic one is the simple assignment operator `=`. 

```cpp
int x = 5; // Assigns the value 5 to x
x = 10;    // Assigns the value 10 to x (overwriting 5)
```

### Compound Assignment Operators
These are shorthand operators that perform an arithmetic operation and an assignment in one step.

| Operator | Example   | Equivalent to |
| :------- | :-------- | :------------ |
| `+=`     | `x += y`  | `x = x + y`   |
| `-=`     | `x -= y`  | `x = x - y`   |
| `*=`     | `x *= y`  | `x = x * y`   |
| `/=`     | `x /= y`  | `x = x / y`   |
| `%=`     | `x %= y`  | `x = x % y`   |

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int score = 100;
    cout << "Initial score: " << score << endl; // 100

    score += 50; // score = score + 50; -> score is now 150
    cout << "Score after += 50: " << score << endl; // 150

    score *= 2;  // score = score * 2;  -> score is now 300
    cout << "Score after *= 2: " << score << endl; // 300

    return 0;
}
```

## Increment and Decrement Operators

These unary operators (`++` and `--`) are used to increase or decrease the value of a variable by 1. They are very common in loops.

| Operator | Name        | Effect       |
| :------- | :---------- | :----------- |
| `++`     | Increment   | Adds 1       |
| `--`     | Decrement   | Subtracts 1  |

There are two forms:

#### Pre-increment/decrement (`++variable` or `--variable`)
- The variable is modified **first**, then its new value is used in the expression.

#### Post-increment/decrement (`variable++` or `variable--`)
- The variable's **original value** is used in the expression **first**, then the variable is modified.

This distinction is a common source of bugs if not understood properly.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int count = 5;
    cout << "Initial count: " << count << endl; // 5

    // Pre-increment
    cout << "Pre-increment (++count): " << ++count << endl; // count becomes 6, then 6 is printed
    cout << "Count after pre-increment: " << count << endl; // 6

    // Reset count
    count = 5;

    // Post-increment
    cout << "Post-increment (count++): " << count++ << endl; // 5 is printed, then count becomes 6
    cout << "Count after post-increment: " << count << endl; // 6

    return 0;
}
```

## Operator Precedence

Just like in mathematics, operators in C++ have a specific order of execution, called **precedence**. For example, multiplication and division have higher precedence than addition and subtraction.

```cpp
int result = 5 + 3 * 2; // Multiplication (3 * 2) happens first
// result will be 5 + 6 = 11, not (5 + 3) * 2 = 16
cout << "Result: " << result << endl; // Output: 11
```

To explicitly control the order of operations or to make your code clearer, always use **parentheses `()`**.

```cpp
int result_clear = (5 + 3) * 2; // Parentheses force addition first
cout << "Result with parentheses: " << result_clear << endl; // Output: 16
```

**Rule of Thumb:** When in doubt about operator precedence, use parentheses. They make your code's intent clear and prevent unexpected results.