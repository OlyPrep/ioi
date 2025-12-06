+++
title = "Input and Output"
template = "lesson.html"
description = "Learning to interact with your program: taking input and displaying output."
+++

In the "Hello, World!" lesson, you learned how to make your program display a simple message using `cout`. That's one half of interacting with your program: **output**. The other half is **input**, which allows your program to receive data from the user or other sources.

This lesson will dive deeper into both output and input, teaching your programs how to talk to the outside world and listen back.

## Output

You've already met `cout`, the _standard output stream_. It's used to send data to the console. We use the insertion operator `<<` to send data to `cout`.

You can chain multiple `<<` operators to print several things on one line:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int age = 25;
    int month = 3;

    cout << "Hello! You are " << age << " years and " << month << " months old." << endl;
    // Output: Hello! You are 25 years and 3 months old.

    return 0;
}
```

## Input

To get input from the user, we use `cin`, the _standard input stream_, along with the extraction operator `>>`. When `cin` reads input, it typically stops at whitespace (spaces, tabs, newlines).

```cpp
#include <bits/stdc++.h> 
using namespace std;

int main() {
    int number;
    cout << "Enter a number: ";
    cin >> number; // Read an integer from the user

    // Example of reading multiple values
    int a, b;
    cout << "Enter two numbers (separated by space): ";
    cin >> a >> b; // Read two integers
    cout << "You entered: " << a << " and " << b << endl;

    return 0;
}
```

#### Example Interaction:

```text
Enter a number: 42
You entered: 42
Enter two numbers (separated by space): 10 20
You entered: 10 and 20
```

This lesson covers the basics of how your C++ programs can communicate with the user, taking input and providing output. Mastering these operations is fundamental for any interactive program, especially in competitive programming where you'll constantly be reading problem inputs and printing answers.

## `endl` vs `'\n'`

You've seen using `endl` to end a line. There is another way to do this, by using the newline character `'\n'`.

```cpp
cout << "Hello" << endl;
cout << "World" << '\n';
```

Both lines will move the cursor to the next line in the output. So what's the difference?

- **`'\n'` (Newline Character):** This is a simple character that just represents a line break.
- **`endl` (End Line):** This does two things: it inserts a newline character (`'
'`) **and** it **flushes the output buffer**.

An output buffer is a temporary storage area. When you use `cout`, your output might be held and pilled up in this buffer for a short time before being sent to the console. This is done for efficiency, because sending to console each time takes a little bit of time. Flushing the buffer forces the program to write everything in the buffer to the console immediately.

#### Why does this matter for Competitive Programming?

In competitive programming, you often have to print a very large amount of output (e.g., thousands of lines inside a loop). Forcing a flush on every single line with `endl` can be slow and inefficient. Using `'
'` allows the output to be buffered and written in larger, more efficient chunks. This can sometimes be the difference between a program that is "Accepted" and one that gets a "Time Limit Exceeded" error.

#### Rule of Thumb:

- In most competitive programming problems, prefer `'
'` for better performance, especially when printing many lines.
- Use `endl` only when you need to guarantee that the output is displayed on the screen immediately. An example of this is **interactive problems**, where the judge waits for your output before sending the next input, so if don't flush, both your program and the judge program will get stuck in a cycle of waiting for each other, ultimately causing your program to receive "Idleness Limit Exceeded" verdict.
