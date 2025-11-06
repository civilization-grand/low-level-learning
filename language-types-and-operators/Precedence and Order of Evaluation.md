The table below summarizes the rules for precedence and associativity of all operators.
Operators on the same line have the same precedence; rows are in order of decreasing precedence, so, for example, `*`, `/`, and `%` all have the same precedence, which is higher than that of `+` and `-`.

| Operator                                             | Associativity |
| ---------------------------------------------------- | ------------- |
| `()` `[]` `->` `.`                                   | left to right |
| `!` `~` `++` `--` `-` `(type)` `*` `&` `sizeof`      | right to left |
| `*` `/` `%`                                          | left to right |
| `+` `-`                                              | left to right |
| `<<` `>>`                                            | left to right |
| `<` `<=` `>` `>=`                                    | left to right |
| `==` `!=`                                            | left to right |
| `&`                                                  | left to right |
| `^`                                                  | left to right |
| `\|`                                                 | left to right |
| `&&`                                                 | left to right |
| `\|`                                                 | left to right |
| `?:`                                                 | right to left |
| `=` `+=` `-=` etc.                                   | right to left |
| `,` [Chapter 3](https://www.cc4e.com/book/chap03.md) | left to right |

expressions involving one of the associative and commutative operators (`*`, `+`, `&`, `^`, `|`) can be rearranged even when parenthesized. In most cases this makes no difference whatsoever; in situations where it might, explicit temporary variables can be used to force a particular order of evaluation.
