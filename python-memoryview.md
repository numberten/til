# memoryview() in Python

Objects in python that implement the
[buffer protocol](https://www.python.org/dev/peps/pep-3118/) can be read with zero
copies by calling `memoryview()` on them. `memoryview()` (as the name implies) returns
a readonly view of memory. A `memoryview's` slice operation returns another memoryview,
so slicing can be done with no copies.

Example:

    >>> a = b"abcdef"
    >>> b = memoryview(a)[1:]
    >>> chr(b[0])
    'b'
