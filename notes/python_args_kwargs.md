Can you explain `*args` and `**kwargs` in Python?

---

## *args and **kwargs in Python:

In Python, `*args` and `**kwargs` are conventions used for passing a variable
number of arguments to a function.

1. **`*args`**:
    - Allows you to pass a variable number of **non-keyworded** arguments.
    - Within the function, `args` is a **tuple** containing all the passed
      arguments.
    - You can use any name you want instead of `args`, but the `*` prefix is
      important. Using `args` is just a convention.

    ```python
    def print_args(*args):
        for arg in args:
            print(arg)
    
    print_args(1, 2, 3, 4)
    ```

   Output:
    ```
    1
    2
    3
    4
    ```

2. **`**kwargs`**:
    - Allows you to pass a variable number of **keyworded** arguments.
    - Within the function, `kwargs` is a **dictionary** containing the names as
      keys and the values as key-values.
    - As with `args`, you can use any name you prefer instead of `kwargs`, but
      the `**` prefix is essential. Using `kwargs` is a convention.

    ```python
    def print_kwargs(**kwargs):
        for key, value in kwargs.items():
            print(f"{key} = {value}")
    
    print_kwargs(first_name="John", last_name="Doe")
    ```

   Output:
    ```
    first_name = John
    last_name = Doe
    ```

You can combine both in function definitions, but `*args` must come
before `**kwargs`.

Example:

```python
def combined_example(x, y, *args, **kwargs):
    print(x, y)
    print(args)
    print(kwargs)

combined_example(1, 2, 3, 4, 5, a=6, b=7)
```

Output:

```
1 2
(3, 4, 5)
{'a': 6, 'b': 7}
```

Remember, `args` and `kwargs` are just naming conventions, and you could
technically use names like `*varargs` or `**keyargs`, but `*args` and `**kwargs`
are widely recognized by the Python community.
