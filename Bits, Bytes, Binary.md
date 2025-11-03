Computers can represent numbers only in a binary form (on, off) or (low voltage, high voltage), this limitation made computer scientist choose base 2 binary number as the communication language of the computer itself.

A **bit** in a system is the smallest piece of information a computer can store.

A **byte** is a unit of digital information that consists of **8** of those bits. Historically, the byte was the number of bits used to encode a single character of text in a computer and for this reason it is the smallest addressable unit of memory in many computer architectures.

This is a single byte of information:

| **Number of Bits** |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |
| :----------------- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **Bit Value**      |  1  |  1  |  1  |  1  |  0  |  1  |  1  |  0  |

This byte can store up to 255 in decimal digits, conversion between bits and bytes is a simple calculation: divide by 8 to convert from bits to bytes or multiply by 8 to convert from bytes to bits.

Here's what it looks like when a computer counts to ten:

| binary | decimal |
| ------ | ------- |
| 0000   | 0       |
| 0001   | 1       |
| 0010   | 2       |
| 0011   | 3       |
| 0100   | 4       |
| 0101   | 5       |
| 0110   | 6       |
| 0111   | 7       |
| 1000   | 8       |
| 1001   | 9       |
| 1010   | 10      |


## Decimal numbers

Before exploring how the binary system works, let's revisit our old friend, the decimal system. When you learned how to count, you might have learned that the right-most digit is the "ones' place", the next is the "tens' place", the next is the "hundreds' place", etc.

Another way to say that is that the digit in the right-most position is multiplied by 1, the digit one place to its left is multiplied by 10, and the digit two places to its left is multiplied by 100.

Let's visualize the number 234:

|        2        |      3      |      4      |
| :-------------: | :---------: | :---------: |
| hundreds' place | tens' place | ones' place |
|       100       |     10      |      1      |

When we multiply each digit by its place, we can see that 234 is equal to $(2\times_{}100) + (3\times_{}10) + (4\times_{}1)$.


We can also think of those places in terms of the powers of ten. The ones' place represents multiplying by $10^0$, the tens' place represents multiplying by $10^1$, and the hundreds' place represents multiplying by $10^2$. Each place we add, we're multiplying the digit in that place by the next power of 10.

|        2        |      3      |      4      |
| :-------------: | :---------: | :---------: |
| hundreds' place | tens' place | ones' place |
|       100       |     10      |      1      |
|     $10^2$      |   $10^1$    |   $10^0$    |

## Binary numbers

The binary system works the same way as decimal. The only difference is that instead of multiplying the digit by a power of 10, we multiply it by a power of 2.

Let's look at the decimal number 1, represented in binary as 0001:

| 0     | 0     | 0     | 1     |
| ----- | ----- | ----- | ----- |
| 8     | 4     | 2     | 1     |
| $2^3$ | $2^2$ | $2^1$ | $2^0$ |

That's the same as $(0\times_{}8) + (0\times_{}4) + (0\times_{}2) + (1\times_{}1)$ or $0+0+0+1$.

### Patterns in binary numbers

In last question, you converted odd numbers. There's something interesting about odd numbers in binary. Here are a few more odd numbers to give you an idea:

| Decimal | Binary |
| ------- | ------ |
| 3       | 0011   |
| 5       | 0101   |
| 7       | 0111   |
| 9       | 1001   |

The last bit is always the ones' place, and if a number is odd, it must have a 1 in that ones' place. There's no way to create an odd number in the binary system without that ones' place, since every other place is a power of 2. Knowing this can give you a better intuitive understanding of binary numbers.


There's another interesting pattern in binary numbers. Take a look at these:

| Decimal | Binary |
| ------- | ------ |
| 3       | 11     |
| 7       | 111    |
| 15      | 1111   |

Each of the decimal numbers are a power of 2, minus ‍1:
- $4-1=3$
- $8-1=7$
- $16-1=15$
When a binary number has a 1 in each of its places, then it will always equal the largest number that can be represented by that number of bits.
If you want to add 1 to that number, you need to add another bit. It's like 9, 99, and 999 in the decimal system.

As it turns out, the highest number that can be represented by $n$ bits is the same as $2^{n}-1$:

| Bits ($n$) | Highest Number | ($2^n-1$) |
| ---------- | -------------- | --------- |
| 1          | 1              | ($2^1-1$) |
| 2          | 3              | ($2^2-1$) |
| 3          | 7              | ($2^3-1$) |
| 4          | 15             | ($2^4-1$) |

What do you think: what does $11111$ represent in decimal?
