# Main Specifiers

| Specifier  | Data Type      | Description                                                                                  |
| :--------- | :------------- | :------------------------------------------------------------------------------------------- |
| `%d`, `%i` | `int`          | Signed decimal integer.                                                                      |
| `%u`       | `unsigned int` | Unsigned decimal integer.                                                                    |
| `%o`       | `unsigned int` | Unsigned octal integer (base 8).                                                             |
| `%x`, `%X` | `unsigned int` | Unsigned hexadecimal integer (base 16). `%x` uses lowercase letters, `%X` uses uppercase.    |
| `%f`       | `double`       | Decimal floating-point number.                                                               |
| `%e`, `%E` | `double`       | Scientific notation (e.g., 1.23e+02). `%e` uses a lowercase 'e', `%E` uses an uppercase 'E'. |
| `%g`, `%G` | `double`       | Uses the shorter of `%f` or `%e`/`%E`.                                                       |
| `%a`, `%A` | `double`       | Hexadecimal scientific notation (e.g., 0x1.3p+1). `%a` uses lowercase, `%A` uses uppercase.  |
| `%c`       | `int`          | Single character.                                                                            |
| `%s`       | `char*`        | String of characters.                                                                        |
| `%p`       | `void*`        | Pointer address.                                                                             |
| `%n`       | `int*`         | Stores the number of characters printed so far into an integer pointer. Nothing is printed.  |
| `%%`       | N/A            | Prints a literal percent sign (`%`).                                                         |


# Format Modifiers
Modifiers are placed between the `%` and the specifier (e.g., `%#08.2f`).

## Flags

| Flag            | Description                                                                                              |
| :-------------- | :------------------------------------------------------------------------------------------------------- |
| **`-`**         | **Left-justify** the output within the specified width.                                                  |
| **`+`**         | Forces the result to be **preceded by a sign** (`+` or `-`), even for positive numbers.                  |
| **` ` (space)** | If no sign is written, a space is inserted before the value.                                             |
| **`#`**         | **Alternate form**. Prepends `0` for octal, `0x` or `0X` for hex, and forces a decimal point for floats. |
| **`0`**         | **Zero-pads** the output on the left instead of using spaces. Ignored if `-` is present.                 |

## Width and Precision

| Modifier | Description | Example |
| :--- | :--- | :--- |
| **`(number)`** | **Width**: Specifies the minimum number of characters to print. | `printf("%5d", 12);` -> `   12` |
| **`*`** | **Width**: The width is specified by an extra `int` argument. | `printf("%*d", 5, 12);` -> `   12` |
| **`.(number)`** | **Precision**: For floats, the number of digits after the decimal. For strings, the max characters. For integers, the min number of digits. | `printf("%.2f", 3.1415);` -> `3.14` |
| **`.*`** | **Precision**: The precision is specified by an extra `int` argument. | `printf("%.*f", 2, 3.1415);` -> `3.14` |

# Length Modifiers
This modifier specifies the argument's data type size.

## Length Modifiers for Integer Types (`d`, `i`, `o`, `u`, `x`, `X`)
These modifiers tell `printf` to expect an integer argument that is smaller or larger than the default `int`.

### `hh` (short short)
**What it means:** The integer is a `signed char` or `unsigned char`.
**Example:** `char c = 65; printf("%hhd", c);`

### `h` (short)
**What it means:** The integer is a `short int` or `unsigned short int`.
**Example:** `short s = 30000; printf("%hd", s);`

### `l` (long)
**What it means:** The integer is a `long int` or `unsigned long int`.
**Example:** `long l = 3000000000L; printf("%ld", l);`

### `ll` (long long)
**What it means:** The integer is a `long long int` or `unsigned long long int`.
**Example:** `long long ll = 9000000000000000000LL; printf("%lld", ll);`

### `j` (intmax_t)
**What it means:** The integer is the largest possible integer type on the system (`intmax_t` or `uintmax_t`). This is useful for portability.
**Example:** `intmax_t im = INTMAX_MAX; printf("%jd", im);`

### `z` (size_t)
**What it means:** The integer is a `size_t` type, which is used for memory object sizes. It's the type returned by `sizeof`.
**Example:** `size_t size = sizeof(int); printf("%zu", size);`

### `t` (ptrdiff_t)
**What it means:** The integer is a `ptrdiff_t`, which represents the difference between two pointers.
**Example:** `int arr[5]; ptrdiff_t diff = &arr[4] - &arr[0]; printf("%td", diff);`


## Length Modifiers for Floating-Point Types (`f`, `e`, `g`, `a`, etc.)

### `L` (long double)
**What it means:** The floating-point number is a `long double`, which has higher precision than a standard `double`.
**Example:** `long double ld = 3.141592653589793238L; printf("%Lf", ld);`


## Length Modifiers for Character/String Types (`c`, `s`)

### `l` (long/wide)
**What it means:** The character or string is "wide" (for handling character sets like Unicode).
**For `%lc`**: The argument is a `wint_t` (wide character).
**For `%ls`**: The argument is a pointer to a `wchar_t` string (wide character string).

