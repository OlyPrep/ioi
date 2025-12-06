+++
title = "Loops"
template = "lesson.html"
description = "Running some code repeatedly."
+++

Imagine you need to print "Hello, World!" five times. You could write the `cout` statement five times, but what if you needed to do it 500 times? That would be tedious! Loops are a fundamental concept in programming that allow you to execute a block of code repeatedly as long as a certain condition is met.

## The `while` Loop

The `while` loop is the simplest type of loop. It repeatedly executes a block of code—the _loop body_—as long as its condition remains `true`. The condition is checked **before** each iteration.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int i = 5;

    while (i > 0) {
        cout << "Countdown: " << i << endl;
        i--; // Decrease i by 1
    }

    cout << "Liftoff!" << endl;
    return 0;
}
```

This code will print a countdown from 5 down to 1. As soon as `i` becomes 0, the condition `i > 0` becomes `false`, and the loop terminates.

## Controlling Loop Flow

Sometimes you need more control over your loop than just the main condition. C++ gives us two keywords to handle this: `break` and `continue`.

### `break`

The `break` keyword immediately **terminates** the loop, and the program continues executing at the line of code right after the loop.

```cpp
// Find the first number divisible by 7
int i = 100;
while (true) { // An infinite loop, on purpose!
    if (i % 7 == 0) {
        cout << "Found it! The number is: " << i << endl;
        break; // Exit the loop
    }
    i++;
}
```

### `continue`

The `continue` keyword **skips** the rest of the current iteration and immediately jumps to the beginning of the next iteration, where the condition is checked again.

```cpp
// Print only the odd numbers from 1 to 10
int i = 0;
while (i < 10) {
    i++;
    if (i % 2 == 0) { // If i is even
        continue;   // Skip the rest of this iteration
    }
    cout << i << " "; // This line is skipped for even numbers
}
// Output: 1 3 5 7 9
```

## The `do-while` Loop

The `do-while` loop is a variant of the `while` loop. The key difference is that the condition is checked **after** the loop body is executed. This means a `do-while` loop is guaranteed to run **at least once**.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int choice = 0;

    do {
        cout << "Enter a number (0 to exit): ";
        cin >> choice;
        cout << "You entered: " << choice << endl;
    } while (choice != 0);

    cout << "Exiting program." << endl;
    return 0;
}
```

Notice how the code inside the `do` block runs once even while `choice` is set to zero, this proves that the block is run once before the condition `choice != 0` is ever checked.

## The `for` Loop

The `for` loop is often used when you know in advance how many times you want to repeat the code. It's more compact and often cleaner than a `while` loop because it combines the three essential parts of a loop into a single line:

1.  **Initialization:** A optional statement that runs once before the loop begins.
2.  **Condition:** An expression that is checked before each iteration. The loop continues as long as this is `true`. This expression is also optional, but leaving it out will result in an infinite loop (similar to `while (true)`) unless the loop body `break`s the loop eventually.
3.  **Update:** A optional statement that runs at the end of each iteration.

```cpp
for (initialization; condition; update) {
    // Code to execute
}
```

Let's try it out:

```cpp
// Print numbers from 1 to 5
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}
// Output: 1 2 3 4 5
```

## Nested Loops

Just like you can nest conditional statements, you can also put a loop inside another loop! This is called a _nested loop_. This is a fundamental technique used for working with grids, tables, or any multi-dimensional data.

Think of it like the hands of a clock: for every single hour that the hour hand passes, the minute hand must complete a full 60-minute cycle.

In a nested loop, the inner loop completes **all** of its iterations for **each single** iteration of the outer loop.

Here is an example that prints a 4x5 rectangle of asterisks:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int rows = 4;
    int columns = 6;

    // The outer loop iterates through the rows (from 0 to 3)
    for (int i = 0; i < rows; i++) {
        // The inner loop iterates through the columns (from 0 to 5)
        for (int j = 0; j < columns; j++) {
            cout << "* ";
        }
        // After the inner loop is done, we print a newline to move to the next row.
        cout << endl;
    }
    return 0;
}
```

Run it, and you should see:

```text
* * * * * * 
* * * * * * 
* * * * * * 
* * * * * * 
```

Try playing with various `rows` and `columns` values!

### `break` and `continue` in Nested Loops

A crucial point to understand is that `break` and `continue` **only affect the innermost loop they are in**. They do not break out of outer loops.

#### `break` in a Nested Loop

Imagine you are searching for a specific coordinate in a grid. Once you find it, you might want to stop searching in that row. A `break` will exit the inner loop (the columns), but the outer loop (the rows) will continue as normal.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    for (int i = 0; i < 3; i++) {
        cout << "Row " << i << ": ";
        for (int j = 0; j < 5; j++) {
            if (i == 1 && j == 3) {
                cout << "Target found! ";
                break; // Exits the inner j-loop ONLY
            }
            cout << "(" << i << "," << j << ") ";
        }
        // This code is still executed after the inner loop breaks
        cout << "<- End of Row" << endl;
    }
    return 0;
}
```

Notice the output for `Row 1`. The `break` stops the inner loop when `j` is 3, but the outer loop continues, printing "<- End of Row" and then proceeding to `Row 2`.

```text
Row 0: (0,0) (0,1) (0,2) (0,3) (0,4) <- End of Row
Row 1: (1,0) (1,1) (1,2) Target found! <- End of Row
Row 2: (2,0) (2,1) (2,2) (2,3) (2,4) <- End of Row
```

#### `continue` in a Nested Loop

Similarly, `continue` will only skip to the next iteration of the inner loop.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    for (int i = 0; i < 2; i++) {
        cout << "Row " << i << ": ";
        for (int j = 0; j < 4; j++) {
            if (j == 2) {
                continue; // Skips the rest of the inner loop's current iteration
            }
            cout << "(" << i << "," << j << ") ";
        }
        cout << endl;
    }
    return 0;
}
```

In the output, you can see that the coordinate `(i, 2)` is skipped in each row, but the loop continues perfectly otherwise.

```text
Row 0: (0,0) (0,1) (0,3) 
Row 1: (1,0) (1,1) (1,3) 
```
