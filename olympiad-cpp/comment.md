+++
title = "Comments"
template = "lesson.html"
description = "Putting notes on your code."
+++

Comments are notes written by a programmer that are completely ignored by the C++ compiler. They exist purely for humans to read.

While the code itself tells you **what** the program is doing, comments are used to explain **why**. They can be used to:

- Clarify complex or tricky parts of your code.
- Leave reminders for yourself or notes for other programmers.
- Temporarily disable a line or block of code for testing, a process known as _commenting out_.

Good code doesn't need many comments, but when used wisely, they can be very helpful.

## Single-line Comment

A single-line comment starts with `//` and continues to the end of the line.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    // This line prints a message to the console.
    cout << "Hello, World!" << endl;

    // The following line is disabled because it is commented out.
    // cout << "This will not be printed." << endl;

    return 0; // Return 0 to indicate success
}
```

Note that the `//` syntax does not work inside a string literal.

```cpp
cout << "This is not a // comment" << endl;
```

The above code will print `This is not a // comment` to the console.

## Multi-line Comment

A multi-line comment starts with `/*` and ends with `*/`. Everything between these markers is ignored, even if it spans multiple lines.

This is useful for writing longer explanations or for commenting out large blocks of code.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    /*
      This is a multi-line comment.
      It can span across several lines.
      The code below calculates the area of a rectangle.
    */
    int score = 10;
    cout << "The score is: " << score << endl;

    /*
    cout << "This is a block of code that is commented out." << endl;
    score = 15;
    */

    cout << "The score is: " << score << endl; /* Outputs 10. */

    return 0;
}
```

Like the single-line comment, the `/* */` syntax also does not work inside a string literal.

```cpp
cout << "This is not a /* comment */" << endl;
```

The above code will print `This is not a /* comment */` to the console.