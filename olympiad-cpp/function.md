+++
title = "Functions"
template = "lesson.html"
description = "Defining and calling functions to organize code."
+++

Imagine you're writing a program and find yourself writing the exact same lines of code in multiple places. It feels repetitive, right? In programming, we have a principle called **DRY (Don't Repeat Yourself)**, and functions are one of the most powerful tools to achieve it.

A function is a named block of code that performs a specific task. Think of it like a recipe: you define the recipe once, and then you can use it (or "call" it) whenever you want to cook that dish without rewriting the instructions every time.

Using functions helps you:
- **Organize Code:** Break down a large, complex problem into smaller, manageable, and logical pieces.
- **Improve Readability:** Give a descriptive name to a block of code, making it obvious what that code does.
- **Reuse Code:** Write a piece of logic once and use it from multiple places in your program.

## Defining Functions

To create a function, you need to **define** it. The definition tells the compiler what the function is called, what kind of input it needs, and what kind of output it produces.

The basic syntax for a function definition is:

```cpp
return_type function_name(parameter1_type parameter1_name, parameter2_type parameter2_name, ...) {
    // Code that performs the task (the function body)
    return value;  // A value of the specified 'return_type'
}
```

Let's break that down:
- **`return_type`**: The data type of the value the function will send back after it's done. This could be `int`, `double`, `long long`, etc.
- **`function_name`**: A descriptive name you give to the function.
- **`parameters`**: A (possible empty) list of variables that the function accepts as input. These are the "ingredients" for your recipe.
- **`return value`**: The `return` keyword sends a value back to whoever called the function and terminates the function. **This statement is mandatory.** Not returning something won't cause compiler error, but it is an undefined behavior and will lead to various unpredicatable bugs that are extremely difficult to resolve.

Let's define a simple function that takes two integers and returns their sum.

```cpp
// This function takes two integers, a and b, and returns their sum.
int calculate_sum(int a, int b) {
    int sum = a + b;
    return sum;
}
```

This code defines a function named `calculate_sum`, but it doesn't run it. To run it, we need to call it.

## Using Functions

To use a function, you **call** it by its name and provide the required input values, which are called **arguments**.

Let's call our `calculate_sum` function from inside `main`.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Function definition
int calculate_sum(int a, int b) {
    int sum = a + b;
    return sum;
}

int main() {
    // Call the function with arguments 5 and 3
    // The returned value (8) is stored in the 'result' variable
    int result = calculate_sum(5, 3);

    cout << "The sum is: " << result << endl; // Output: The sum is: 8

    // You can also call it again with different arguments
    result = calculate_sum(100, 50);
    cout << "The new sum is: " << result << endl; // Output: The new sum is: 150

    return 0;
}
```

## Functions That Return Nothing

What if a function's job is just to *do* something, like print a message, without needing to send a value back? For this, we use a special return type: `void`.

A `void` function performs an action and doesn't use the `return` keyword to send back a value. But you can still use `return` without any value to terminate the function.

```cpp
#include <bits/stdc++.h>
using namespace std;

// This function just prints a number. It doesn't return any value.
void print_number(int number) {
    if (number == 0)
    {
        cout << "I hate zero!" << endl;
        return;
    }
    cout << "The number is " << number << "!" << endl;
    // return;  // We can skip it because it's a void function
}

int main() {
    print_number(42); // Output: The number is 42!
    print_number(0);  // Output: I hate zero!
    return 0;
}
```

## The `main` Function

Remember the `int main() { ... }` block from our "Hello, World!" lesson? `main` is actually a very special function!

It's a very special function for one reason: **it's the entry point of your program**. When you run your C++ program, the operating system calls the `main` function, and the execution begins from the first line inside it.

And what about `return 0;`? Since `main` is declared with a return type of `int` (`int main()`), it is expected to return an integer. However, specifically for `main` function, this return statement is optional. If you don't `return 0;` explicitly, the compiler will automatically put `return 0;` itself.

By convention, returning `0` from `main` tells the operating system that the program ran successfully without any errors. Any value other than `0` tells the operating system that the program failed.
