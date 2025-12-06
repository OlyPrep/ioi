+++
title = "Switch Statement"
template = "lesson.html"
description = "Switch: Specialized Conditional Syntax for Testing a Value."
+++

You just learned `if`-`else` statements to handle conditional logic. C++ provides one more tool for this job: the `switch` statement. A `switch` statement is a specialized conditional that is used to test a single variable against a list of possible constant values.

## Why It's Different?

So, if we already have `if`-`else`, why do we need `switch`?

Think of a situation where you have a single variable, and you want to do a different thing for each specific value it might have. You could write a long `if`-`else if`-`else` chain:

```cpp
if (day == 6) {
    cout << "Friday :D";
} else if (day == 7) {
    cout << "Saturday :D";
} else if (day == 1) {
    cout << "Sunday, school day :((";
} else {
    cout << "Some other school day :(";
}
```

This works, but it's a bit repetitive. A `switch` statement can make this kind of logic cleaner and easier to read.

However, `switch` has important limitations that `if`-`else` does not:

1. It can only check for equality (`==`). It cannot handle other comparisons like `>` or `<`.
2. It only works with integral types, like `int`, `char`, `long long` (but not `float` or `double`).
3. The values in each `case` must be **known at compile-time** or _compile-time constants_, for example integer or character literals (e.g., `5`, `'A'`). You cannot use a variable as a case value.

## Syntax

The basic syntax looks like this:

```cpp
switch (expression) {
    case constant_1:
        // Code to execute if variable == constant_value_1
        break;
    case constant_2:
        // Code to execute if variable == constant_value_2
        break;
    // ... more cases
    default:
        // Code to execute if variable matches none of the cases
}
```

### `case`

Each `case` is a label for a specific value. If the `expression` you are switching on matches the `constant_value` of a `case`, the program will jump to that point and start executing the code.

### `default` Case

The `default` case is optional. It should be placed as the very last case of a `switch`. It acts like the final `else` in an `if`-`else if`-`else` chain. If the `expression`'s value doesn't match any of the other `case` labels, the code inside the `default` block will be executed.

## Trying It Out

Let's write a program using `switch` to print the day of the week. We'll intentionally leave something out to see what happens.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int day = 7;

    switch (day) {
        case 6:
            cout << "Friday :D";
        case 7:
            cout << "Saturday :D";
        case 1:
            cout << "Sunday, school day :((";
        default:
            cout << "Some other school day :(";
    }
    cout << endl;
    return 0;
}
```

Let's compile run this.

```text
Saturday :DSunday, school day :((Some other school day :(
```

Wait, why did it print all of that? This is because `switch` statements in C++ have a behavior called **"fall-through"**. When a matching `case` is found, the program executes the code from that point downwards, including the code in all the subsequent cases!

To prevent this, we need another keyword.

## The `break` Keyword

The `break` keyword tells the program to immediately "break out" of the `switch` block. When a `break` is encountered, the program jumps to the very end of the `switch` statement and continues on.

You will need to add a `break` to the end of almost every `case` to prevent unwanted fall-through. Since the `default` case is typically the last block in the statement, it doesn't need a `break`.

## Trying Again

Let's fix our program by adding `break` statements.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int day = 7;

    switch (day) {
        case 6:
            cout << "Friday :D";
            break;
        case 7:
            cout << "Saturday :D";
            break; // Now it will exit after this case
        case 1:
            cout << "Sunday, school day :((";
            break;
        default:
            cout << "Some other school day :(";
            // No break needed here as it's the last one
    }
    cout << endl;
    return 0;
}
```

Now let's run this code:

```text
Saturday :D
```

## Nested `switch`

Just like `if` statements, `switch` statements can also be nested inside one another. This is not a very common pattern, but it is possible.

A key point to remember is that the `break` keyword will only exit from the **innermost** `switch` statement it is in.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    char plan = 'A';
    int tier = 2;

    switch (plan) {
        case 'A':
            cout << "Plan A, ";
            // Nested switch
            switch (tier) {
                case 1:
                    cout << "Tier 1 selected.";
                    break; // This break only exits the inner switch
                case 2:
                    cout << "Tier 2 selected.";
                    break; // This break also only exits the inner switch
            }
            // Execution continues here after inner break
            cout << " (End of Plan A)";
            break; // This break exits the outer switch

        case 'B':
            cout << "Plan B selected.";
            break;
    }
    cout << endl;
    return 0;
}
```
The output shows how the `break` only exits the inner `switch`, allowing the outer `case` to continue executing code after it.
```text
Plan A, Tier 2 selected. (End of Plan A)
```
