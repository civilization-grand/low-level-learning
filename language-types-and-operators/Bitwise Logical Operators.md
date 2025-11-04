Make sure to study [[Bits, Bytes, Binary]].

| Operator | Description              |
| -------- | ------------------------ |
| &        | bitwise AND              |
| \|       | bitwise inclusive OR     |
| ^        | bitwise exclusive OR     |
| <<       | left shift               |
| >>       | right shift              |
| ~        | one's complement (unary) |

## `&` Bitwise AND
Compares each bit position. Result is `1` only if **both bits are 1**.
```
	5 = 0101 
&   3 = 0011 
----------- 
	1 = 0001
```

**Use cases:**
- Checking if specific bits are set
- Clearing bits
- Masking operations

## `|` Bitwise Inclusive OR
Compares each bit position. Result is `1` if **either bit is 1**.

```
	5 = 0101 
|   3 = 0011
----------- 
	7 = 0111 
```

**Use cases:** 
- Setting specific bits
- Combining flags


## `^` Bitwise Exclusive OR
Result is `1` if bits are **different**.

```
	5 = 0101 
^   3 = 0011 
 ------------
	6 = 0110
```

**Use cases:** 
- Toggling bits
- Swapping values without a temp variable
- Finding unique elements
- Simple encryption

**Cool trick:** Swap two numbers:
```javascript
a = a ^ b;
b = a ^ b; // b now equals original a
a = a ^ b; // a now equals original b
```


## `~` one's complement (unary)
Flips all bits (1 becomes 0, 0 becomes 1). This is a **unary operator** (works on one operand).

```c
~5 = ~0101 = 1010 (in 4-bit)
```

**Use cases:** 
- Inverting bit patterns 
- Creating bit masks

## `<<` Left Shift
Shifts bits to the left, filling with zeros on the right.

```c
5 << 1: 0101 becomes 1010 (which is 10) 
5 << 2: 0101 becomes 10100 (which is 20)
```
**Key insight:** Each left shift multiplies by 2! 

**Use cases:** 
- Fast multiplication by powers of 2 
- Creating bit masks 
- Efficient array indexing in certain algorithms


## `>>` Right Shift
Shifts bits to the right. Left side behavior depends on signed/unsigned:
- **Arithmetic shift:** Preserves sign (fills with the sign bit) 
- **Logical shift:** Fills with zeros

```c
20 >> 1: 10100 becomes 1010 (which is 10) 
20 >> 2: 10100 becomes 101 (which is 5)
```

**Key insight:** Each right shift divides by 2 (integer division)!

**Use cases:**
- Fast division by powers of 2
- Extracting bit fields

## Practical Examples

#### Checking if a number is a power of 2:
```javascript
function isPowerOfTwo(n) {
    return n > 0 && (n & (n - 1)) === 0;
}
// 8 = 1000, 7 = 0111 → 1000 & 0111 = 0000 ✓
```

#### Counting set bits (Hamming weight):
```javascript
function countBits(n) {
    let count = 0;
    while (n) {
        count += n & 1;  // Check if last bit is 1
        n >>= 1;         // Shift right
    }
    return count;
}
```

#### Using flags (common in permissions, settings):
```javascript
const READ = 1;    // 001
const WRITE = 2;   // 010
const EXECUTE = 4; // 100

let permissions = READ | WRITE;  // 011 (has read and write)

// Check permission
if (permissions & WRITE) {
    console.log("Has write permission");
}

// Add permission
permissions |= EXECUTE;  // Now 111

// Remove permission
permissions &= ~WRITE;   // Now 101 (has read and execute)
```

#### Swapping nibbles (4-bit halves of a byte):
```javascript
function swapNibbles(x) {
    return ((x & 0x0F) << 4) | ((x & 0xF0) >> 4);
}
// 0xAB (10101011) becomes 0xBA (10111010)
```


## Practice Exercises
Want to test your understanding? Try these:
1. Write a function to toggle the nth bit of a number
2. Check if two numbers have opposite signs (without comparison operators)
3. Find the only non-duplicate number in an array where every other number appears twice
4. Reverse the bits of a 32-bit integer

