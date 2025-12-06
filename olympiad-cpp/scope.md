+++
title = "Scope"
template = "lesson.html"
description = "Understanding variable scope in C++."
+++

In C++, a variable's _scope_ is the region of the code where it is **alive** and can be accessed. Think of your program as a house and each set of curly braces `{}` as a different room. A variable is like a person in a room: you can only interact with them if you are in the same room.

## Local Scope

When you declare a variable inside a set of curly braces `{}`, it has **local scope** (or _block scope_). It is born when the block begins and dies when the block ends. It cannot be seen or used from outside that block.

This is true for `if` statements, loops, or even just a standalone pair of braces.

Here is an example with an `if` statement:

```cpp
int x = 10;

if (x == 10) {
    int y = 20; // y is created here
    cout << "x is " << x << endl; // Works, x is in scope
    cout << "y is " << y << endl; // Works, y is in scope
} // y is destroyed here

cout << "x is still " << x << endl; // Works, x is still in scope
// cout << "y is now " << y << endl; // ERROR! y is not in scope here
```

It's the same for loops. The loop counter `i` is only alive inside the loop:

```cpp
for (int i = 0; i < 5; i++) {
    cout << i << endl; // Works, i is in scope
} // i is destroyed here

// cout << i << endl; // ERROR! i is not in scope here
```

You can even create a scope with just curly braces:

```cpp
{
    int temporary_variable = 100;
} // temporary_variable is destroyed here

// cout << temporary_variable << endl; // ERROR!
```

## Global Scope

Variables can also be declared outside of the main function. These variables are said to have **global scope**.

Global variables are accessible from *anywhere* in the file after they are declared, including inside `main` and other blocks. To use our analogy, they are in the main hallway of the house, visible from every room.

```cpp
#include <bits/stdc++.h>
using namespace std;

int global_x = 100; // This is a global variable

int main() {
    cout << "Global x from main: " << global_x << endl;

    if (true) {
        cout << "Global x from an if block: " << global_x << endl;
        global_x = 50; // We can modify it
    }

    cout << "Global x after modification: " << global_x << endl;
    return 0;
}
```

> **Note:**
>
> While global variables may seem convenient, they should be used with caution. Since they can be modified from anywhere, it can become very difficult to track down bugs if they are changed unexpectedly.

## Variable Shadowing

What happens if you declare a local variable with the same name as a global variable? The local variable **shadows** (or hides) the global one. Inside the local scope, the name will refer to the local variable, and the global variable will be inaccessible by that name.

```cpp
#include <bits/stdc++.h>
using namespace std;

int x = 100; // Global variable

int main() {
    cout << "Global x before shadowing: " << x << endl; // Prints 100

    int x = 5; // Local variable, shadows the global x

    cout << "Local x: " << x << endl; // Prints 5

    return 0;
}
```

Shadowing can also happen between two local variables in nested scopes:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int x = 10; // Outer local variable

    cout << "Outer x before inner scope: " << x << endl; // Prints 10

    {
        int x = 5; // Inner local variable, shadows the outer x
        cout << "Inner x: " << x << endl; // Prints 5
    } // Inner x is destroyed here

    cout << "Outer x after inner scope: " << x << endl; // Prints 10

    return 0;
}
```

In this example, the `x` declared inside the inner curly braces `{}` only exists within that block. It temporarily hides the outer `x`. Once the block ends, the inner `x` is destroyed, and the name `x` refers to the outer variable again.
