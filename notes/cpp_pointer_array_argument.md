In my C++ textbook about pointers, there’s an example that talks about a
function where “p is assumed to point to a zero-terminated array of char (or to
nothing).” But the function type doesn’t indicate an array, only a regular
pointer (I think):

```cpp
int count_x(const char* p, char x)
```

---

In C++, the name of an array decays into a pointer to its first element. So when
we pass an array to a function that takes a pointer as an argument, it receives
a pointer to the array's first element. This is why arrays and pointers are
often used interchangeably in function parameters.

So, when your textbook says that `p` is assumed to point to a "zero-terminated
array of char (or to nothing)", it's talking about a C-style string, which is a
sequence of characters stored in an array of char, terminated by a null
character (`'\0'`).

The function `int count_x(const char* p, char x)` is likely to count the
occurrences of the character `x` in the string pointed to by `p`. The `const`
keyword is used to specify that the function will not modify the string. Note
that this does not prevent the function from modifying the pointer `p` itself,
but it cannot modify the characters that `p` points to.

So in this case, `const char* p` can be a pointer to a single character, but it
can also be a pointer to the first character of an array of characters, i.e., a
C-style string. The string is assumed to be zero-terminated, which is a common
assumption when dealing with C-style strings. The function will probably use
this assumption to determine when it has reached the end of the string, by
stopping when it encounters a `'\0'` character.
