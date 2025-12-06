+++
title = "Hello, World!"
template = "lesson.html"
description = "Writing your first C++ program."
+++

In this lesson, we will write our very first C++ program: "Hello, World!". This is a classic program that simply prints "Hello, World!".

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
```

Compile and run this code. You should see the following output:

```text
Hello, World!
```

## Breaking It Down

```cpp
#include <bits/stdc++.h>
using namespace std;
```

These two lines enable us to use anything from the C++ standard library.

```cpp
int main() {
```

This line marks the point from where the program starts running, the beginning of the main function. [Functions](@/ioi/olympiad-cpp/function.md) discusses in detail about this, for now let's just call it "_the main function_."

```cpp
    cout << "Hello, World!" << endl;
```

This line is a statement, and it instructs the program to print `Hello, World!` and end the line with `endl`.

Here, `"Hello, World!"` is a _string literal_. A _literal_ is a value that is specified directly in the code, and a _string literal_ is a piece of text enclosed by double quotes (`"`).

Note the semicolon (`;`), each C++ statement must end with a semicolon. Beginners, even seasoned programmer often miss out the semicolon which results in the program failing to compile, so keeping the semicolon in mind saves a huge amount of debugging time and frustration.

```cpp
    return 0;
```

This line is also a statement and instructs the program to stop. The number `0` indicates the program has succesfully performed its job.

```text
}
```

Marks the end of the main function.
