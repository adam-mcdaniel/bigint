# bigint

![Header Image](assets/header.png)

This repository implements a big integer library in C. The library supports many operations, such as basic arithmetic, comparison, fast modular exponentiation, prime number detection, square roots, and more.

## Usage

To use the library, first include it in your C file.

```c
#include "bigint.h"
```

To create a new big integer, use the `bigint` struct. You can initialize a big integer from a string, an integer, or another big integer.

```c
int main() {
    // Initialize a big integer from a string
    bigint a = bigint_from_string("123456789012345678901234567890");

    // Initialize a big integer from an integer
    bigint b = bigint_from_int(1234567890);

    // Initialize a big integer from another big integer
    bigint c = bigint_copy(a);

    bigint_delete(a);
    bigint_delete(b);
    bigint_delete(c);

    return 0;
}
```

To perform arithmetic operations on big integers, use the provided functions.

```c
int main() {
    // Initialize big integers
    bigint a = bigint_from_string("123456789012345678901234567890");
    bigint b = bigint_from_string("987654321098765432109876543210");

    // Perform arithmetic operations
    bigint c = bigint_add(a, b);
    bigint d = bigint_sub(a, b);
    bigint e = bigint_mul(a, b);
    bigint f = bigint_div(a, b);
    bigint g = bigint_mod(a, b);

    bigint_delete(a);
    bigint_delete(b);
    bigint_delete(c);
    bigint_delete(d);
    bigint_delete(e);
    bigint_delete(f);
    bigint_delete(g);

    return 0;
}
```

To compare big integers:

```c    
int main() {
    // Initialize big integers
    bigint a = bigint_from_string("123456789012345678901234567890");
    bigint b = bigint_from_string("987654321098765432109876543210");

    // Compare big integers
    if (bigint_eq(a, b)) {
        printf("a == b\n");
    } else if (bigint_lt(a, b)) {
        printf("a < b\n");
    } else if (bigint_gt(a, b)) {
        printf("a > b\n");
    }

    bigint_delete(a);
    bigint_delete(b);

    return 0;
}
```

To perform fast modular exponentiation:

```c
int main() {
    // Initialize big integers
    bigint a = bigint_from_string("2");
    bigint b = bigint_from_string("1234");
    bigint m = bigint_from_string("10007");

    // Perform fast modular exponentiation
    bigint c = bigint_fast_pow(a, b, m);

    bigint_delete(a);
    bigint_delete(b);
    bigint_delete(c);
    bigint_delete(m);

    return 0;
}
```

To check if a big integer is prime:

```c
int main() {
    // Initialize a big integer
    bigint a = bigint_from_string("123456789012345678901234567890");

    // Check if the big integer is prime
    if (bigint_is_prime(a)) {
        printf("a is prime\n");
    } else {
        printf("a is not prime\n");
    }

    bigint_delete(a);

    return 0;
}
```

To calculate the square root of a big integer:

```c
int main() {
    // Initialize a big integer
    bigint a = bigint_from_string("123412341");

    // Calculate the square root
    bigint b = bigint_sqrt(a);

    bigint_delete(a);
    bigint_delete(b);

    return 0;
}
```

## Building

To build your program with the big integer library, simply add it to your include path and link against the C standard library.

```bash
gcc -I path/to/bigint main.c -o main
```

### CMake

To build with CMake, you can use a `CMakeLists.txt` file like the following:

```cmake
cmake_minimum_required(VERSION 3.0)

# Create a new project
project(HelloWorld)

# Add an executable
add_executable(HelloWorld main.c)

include_directories(path/to/bigint)
```

Alternatively, you can use `FetchContent` to download the big integer repository and include it in your project.

```cmake
# Import the library from the git repo
include(FetchContent)

FetchContent_Declare(
  bigint
  GIT_REPOSITORY https://github.com/adam-mcdaniel/bigint
  GIT_TAG        main
)

FetchContent_MakeAvailable(bigint)

# Include the header only library
include_directories(${bigint_SOURCE_DIR})
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


<!-- 

This repository implements a regex engine in C++ using Thompson's NFA algorithm. This algorithm prevents pathological backtracking, a common problem with most widely used regex implementations.

This implementation is also a header-only library.

## Usage

To use the library, first include it in your C++ file.

```c++
// Optionally, you can define `CACHING` to allow
// the regex engine to cache transition states.
// This can improve performance in many cases.
#define CACHING

// Include the regex header file
#include "regex.hpp"
```

To use the regex engine, first create a regex object with the desired regex pattern. You can use `std::cout` to print out the compiled regex NFA. Use the `match` method to use the regex on a given content string.

```c++
int main() {
    // Compile a regex pattern
    Regex r("((ab)*|c)+");

    // Print out the compiled NFA
    std::cout << r << std::endl;

    // The content to match
    std::string content = "abc";

    // Check if the content matches the regex
    if (r.match(content)) {
        std::cout << "Matched!" << std::endl;
    } else {
        std::cout << "Not matched!" << std::endl;
    }

    return 0;
}
```

## Regex Syntax

The regex engine supports the following syntax:

| Syntax | Description |
|--------|-------------|
| `*` | Zero or more of the preceding expression |
| `+` | One or more of the preceding expression |
| `?` | Zero or one of the preceding expression |
| `\|` | Alternation |
| `()` | Grouping |
| `a`, `b`, `c`, ... | Any single character |

## Building

To build your program with the regex engine, simply add it to your include path and link against the C++ standard library.

```bash
g++ -I path/to/regex-engine main.cpp -o main
```

### CMake

To build with CMake, you can use a `CMakeLists.txt` file like the following:

```cmake
cmake_minimum_required(VERSION 3.0)

# Create a new project
project(HelloWorld)

# Add an executable
add_executable(HelloWorld main.cpp)

include_directories(path/to/regex-engine)
```

Alternatively, you can use `FetchContent` to download the regex engine repository and include it in your project.

```cmake
# Import the library from the git repo
include(FetchContent)

FetchContent_Declare(
  regex-engine
  GIT_REPOSITORY https://github.com/adam-mcdaniel/regex-engine
  GIT_TAG        main
)

FetchContent_MakeAvailable(regex-engine)

# Include the header only library
include_directories(${regex-engine_SOURCE_DIR})
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details. -->