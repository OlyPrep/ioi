+++
title = "Type Casting"
template = "lesson.html"
description = "Converting value from one type to another."
+++

In C++, converting a value from one data type to another is called **type casting** (or type conversion). This is necessary when you need to perform operations involving different data types or to ensure an operation, like division, behaves exactly as you intend.

## Implicit Type Casting

This is when the C++ compiler automatically converts one data type to another without you explicitly telling it to. This usually happens when a value of one type is assigned to a variable of another type, or in expressions with mixed types. The compiler generally allows conversions that it considers "safe."

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    // Promotion: int to double (safe)
    int x = 5;
    double y = x; // y is now 5.0
    cout << "y = " << y << endl;

    // Promotion: char to int (safe)
    char c = 'A';
    int i = c; // i is now 65 (the ASCII value of 'A')
    cout << "i = " << i << endl;

    // Demotion: double to int (potential data loss!)
    double pi = 3.14159;
    int truncated_pi = pi; // truncated_pi is now 3 (the decimal part is lost)
    cout << "truncated_pi = " << truncated_pi << endl;
}
```

## Explicit Type Casting

This is when you, the programmer, explicitly force a type conversion. This is often needed to get the desired behavior from an operation. The most commonly used syntax to do this is `(new_type)value`.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    // Promotion: int to double
    int x = 5;
    cout << "x = " << (double)x << endl; // Output: 5.0

    // Promotion: char to int
    char c = 'A';
    cout << "c = " << (int)c << endl; // Output: 65 (the ASCII value of 'A')

    // Demotion: double to int (potential data loss!)
    double pi = 3.14159;
    cout << "pi = " << (int)pi << endl;
    // Output: 3 (the decimal part is lost)
}
```