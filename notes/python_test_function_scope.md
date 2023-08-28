```python
def test_function_scope(h, i, j, k, l, m, n):
    h = "b"
    i = 2
    j = 2.0
    k = [4, 5, 6]
    l = (4, 5, 6)
    m = {4: 4, 5: 5, 6: 6}
    n = {4, 5, 6}


if __name__ == "__main__":
    a = "a"
    b = 1
    c = 1.0
    d = [1, 2, 3]
    e = (1, 2, 3)
    f = {1: 1, 2: 2, 3: 3}
    g = {1, 2, 3}

    test_function_scope(a, b, c, d, e, f, g)

    print(f"""
    a: {a},
    b: {b},
    c: {c},
    d: {d},
    e: {e},
    f: {f},
    g: {g},
    """)
```
