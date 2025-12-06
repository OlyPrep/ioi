+++
title = "Built-in Types"
template = "lesson.html"
description = "Fundamental data types in C++."
+++

When you declare a variable, you must give it a type. The type tells the computer what kind of data the variable will hold (like a whole number, a letter, or a number with a decimal point). This is crucial because different types of data take up different amounts of memory and have different operations that can be performed on them. This lesson covers the most common built-in data types in C++.

## Integers

Integers are used to store whole numbers.

#### `int`

The most common integer type is `int`. It is typically 32 bits (4 bytes) on most systems. A bit is a binary digit (0 or 1). With 32 bits, you can represent $2^{32}$ different values. Since `int` is _signed_ (it can be positive or negative), you can store integers from $-2^{31}$ to $2^{31} - 1$, from roughly $-2 \cdot 10^9$ to $2 \cdot 10^9$.

#### `unsigned int`

An `unsigned int` also uses 32 bits, but it can only store non-negative values. This shifts its range to be from 0 to $2^{32} - 1$ (approximately $4 \cdot 10^9$).

#### Larger Integers

For competitive programming, you often need to store numbers larger than what a standard `int` can hold. For this, we have `long long`.

| Type                 | Typical Size        | Range                       |
|:---------------------|:--------------------|:----------------------------|
| `int`                | 32 bits (4 bytes)   | $-2^{31}$ to $2^{31} - 1$   |
| `unsigned int`       | 32 bits (4 bytes)   | $0$ to $2^{32} - 1$         |
| `long long`          | 64 bits (8 bytes)   | $-2^{63}$ to $2^{63} - 1$   |
| `unsigned long long` | 64 bits (8 bytes)   | $0$ to $2^{64} - 1$         |
| `__int128_t`         | 128 bits (16 bytes) | $-2^{127}$ to $2^{127} - 1$ |
| `__uint128_t`        | 128 bits (16 bytes) | $0$ to $2^{128} - 1$        |

**Rule of Thumb:** If the problem constraints mention numbers up to $10^9$, `int` is fine. If they go up to $10^{18}$, you must use `long long`.

> **A Note on `__int128_t`:**
>
> The `__int128_t` type is a non-standard extension provided by some compilers like GCC and Clang on 64-bit systems. While it can be very useful for problems with extremely large numbers, **it is not guaranteed to be available on all platforms.** Always check the compiler and platform details for the online judge you are using. If you use it and the judge's compiler doesn't support it, your code will fail to compile. Use it with caution!

#### Fixed-Width Integers

The size of `int` and `long long` can technically vary between systems (though it's rare nowadays). To guarantee the size, you can use fixed-width integers from the `<cstdint>` header.

| Type       | Size    | Range                   |
|:-----------|:--------|:------------------------|
| `int32_t`  | 32 bits | $-2^{31}$ to $2^{31}-1$ |
| `uint32_t` | 32 bits | $0$ to $2^{32}-1$       |
| `int64_t`  | 64 bits | $-2^{63}$ to $2^{63}-1$ |
| `uint64_t` | 64 bits | $0$ to $2^{64}-1$       |

## Floating-point Numbers

These types are for numbers with decimal points, like 3.14159.

| Type          | Typical Size            | Precision          |
|:--------------|:------------------------|:-------------------|
| `float`       | 32 bits (4 bytes)       | ~7 decimal digits  |
| `double`      | 64 bits (8 bytes)       | ~15 decimal digits |
| `long double` | Usually atleast 80 bits | More than `double` |

In competitive programming, `double` is the most common choice. It offers a good balance of precision and performance.

## Characters

The `char` type is used to store a single character, like a letter, a digit, or a symbol. _Character literals_ are enclosed in single quotes (`'`).

```cpp
char my_grade = 'A';
char my_symbol = '#';
```

Under the hood, a `char` is just a small integer (usually 8 bits). It stores the numeric code of the character based on a character set, most commonly **ASCII** (American Standard Code for Information Interchange). For example, the ASCII value for `'A'` is 65.

### ASCII Table Reference

ASCII (American Standard Code for Information Interchange) standard is a character set that represents each character with a unique integer value, called a _codepoint_. Here's a partial reference for common characters:

| Codepoint | Character |
|:----------|:----------|
| 32        | (space)   |
| 48-57     | 0-9       |
| 65-90     | A-Z       |
| 97-122    | a-z       |
| 10        | (newline) |

For a complete ASCII table, you can check out [here at C++ reference](https://en.cppreference.com/w/cpp/language/ascii.html).

## The `auto` Keyword

The `auto` keyword is a feature from modern C++ that tells the compiler to automatically figure out the data type of a variable from its initial value. This can make code shorter and easier to read, as you don't have to write out a type name that is already obvious from the initial value.

It's important to understand that `auto` is not a "magic" type. The variable still has a concrete, static type (like `int` or `double`), but you're just letting the compiler figure it out for you.

You can use `auto` just like a data type.

```cpp
auto variable_name = initial_value;
```

An initial value is **required** when using `auto`, because that is the only information the compiler has to determine the variable's type.

Here's an example of a program using `auto`.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    auto x = 5;           // The compiler sees 5 and deduces that x is an int
    auto y = 3.14;        // The compiler sees 3.14 and deduces that y is a double
    auto z = 'A';         // The compiler sees 'A' and deduces that z is a char

    cout << "x is an int: " << x << endl;
    cout << "y is a double: " << y << endl;
    cout << "z is a char: " << z << endl;

    // The line below would cause a compile error because 'a' has no initializer.
    // auto a;

    return 0;
}
```
