# Primitive Types

## char
The smallest integer type, typically one byte. It's used to store single characters (like 'a') or small integers.
**Size**: 1 byte

## int
The platform's default, "most efficient" integer size.
**Size**: depends on the machine, it's most often `4 bytes` on a 32-bit as well as 64-bit systems

### short
A short integer.
**Size**: typically 2 bytes
### long (or `long int`)
A long integer.
**Size**: typically 8 bytes

## float
Single-precision floating-point number.
**Size**: typically 4 bytes

## double
Double-precision floating-point number.
**Size**: typically 8 bytes

## void
A special-purpose type that means "no type".
### Use Cases:
- Indicate that a function returns no value (e.g., `void print_hello()`).
- Indicate that a function takes no arguments (e.g., `int get_value(void)`).
- Create generic pointers (e.g., `void *ptr`).


# User Defined Types

## struct (Structures)
A **structure** is the most common user-defined type. It bundles several variables (of different or a-like types) into a single, named unit.

```c
struct Point { 
	int x;
	int y;
};
```

## union (Unions)
A **union** is like a `struct`, but all its members _share the same memory location_. This means you can only use _one_ member at a time.

```c
union Data {
	int i;
	float f;
	char c;
};
```

## enum (Enumerations)
An **enumeration** creates a new type whose only possible values are a list of named integer constants.

```c
enum Day {
    MONDAY,    // Gets value 0
    TUESDAY,   // Gets value 1
    WEDNESDAY, // Gets value 2
    // ...and so on
};

enum Day today = TUESDAY;

if (today == TUESDAY) {
    printf("It's Tuesday!\n");
}
```


## typedef (Type Definition)
The **`typedef`** keyword doesn't create a _new_ type; it creates an _alias_ or a nickname for an existing type. This is extremely common and powerful, especially when used with `struct`.

```c
// WITHOUT typedef
struct Vector2D {
    int x;
    int y;
};
struct Vector2D vec1; // You must write "struct Vector2D" every time


// WITH typedef
typedef struct {
    int x;
    int y;
} Vector2D; // "Vector2D" is now an alias for the struct

Vector2D vec2; // Much cleaner!
```


# Derived Types
In C, derived types are types whose definitions are based on other types. The main ones are pointers, arrays, and functions.

## Pointer Types
A **pointer** is a variable that stores the memory address of _another_ variable. A pointer's type is "derived" from the type of data it points to.

**Purpose:** Direct memory manipulation, dynamic memory allocation (`malloc`), and passing large data to functions efficiently (by passing its address instead of a copy).

**Example:** 
```c
int var = 10;

// 'ptr' is not an 'int'. 
// Its type is 'int *' (pointer to an integer).
int *ptr = &var;
```
Here, `int *` is a type derived from `int`.

## Array Types
An **array** is a fixed-size, sequential collection of elements of the _same_ type. Its type is "derived" from the type of elements it holds and its size.

**Purpose:** To store lists of data, like a list of 10 scores or 50 characters.
**Example:**
```c
// 'scores' is not an 'int'.
// Its type is 'array of 10 integers' (often written int[10]).
int scores[10];

// 'name' is an 'array of 50 characters'.
char name[50];
```

## Function Types
Even **functions** have a type. A function's type is defined (or derived) from its **return type** and the **types of its parameters**.

**Purpose:** This becomes important when you use function pointers, which allow you to treat functions like variables (e.g., pass a function as an argument to another function).
**Example:**
```c
// The type of this function is:
// "function that takes (int, int) and returns int"
int add(int a, int b) {
    return a + b;
}

// This defines a function pointer 'func_ptr'
// that can point to any function with that specific type.
int (*func_ptr)(int, int);

// Assign it
func_ptr = &add;

// Call it
int result = func_ptr(5, 3); // result is 8
```

