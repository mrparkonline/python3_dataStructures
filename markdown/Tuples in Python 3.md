# Tuples in Python 3
---

## What are Tuples?

Strings and Lists are basic iterable data types that are very similar with key differences:
- Strings only allow alphanumeric characters and special symbols to represent text
- Lists allow all data types as its items/members
- Strings are immutable whereas Lists are mutable

These significant differences cause a headache when you require the following data structure:
- It must be immutable
- It must allow different datatypes as items
- It must be iterable
- It must be nestable (much like a list within a list)
 
**All of these are solved** with a data structure called: **Tuple**.

## How to use Tuples in Python 3

- Tuples are declared with parenthesis ... aka round brackets
- () is an empty tuple
- (50,) is a singleton tuple; the comma is required
- Tuples are sliceable; therefore, indexable using square brackets

*A singleton is an iterable data structure with only single item*.

### Tuple Example 1


```python
tup = ('C', ' Java', 'Python')
empty_tup = ()
single_tup = ('Park',)

print(tup)
print(empty_tup)
print(single_tup)
```

    ('C', ' Java', 'Python')
    ()
    ('Park',)


## Tuple Operators


```python
# Concatenation: Joining two tuples
a = (1,2,3)
b = (4,5,6)
concat_result = a + b
print('a+b:', concat_result)


# Repetition: Repeating a list multiple times
c = ('Hi!',)
repet_result = c * 3
print('c*3', repet_result)

# Membership: Check if a value exists in a tuple
d = a + b + c
print('d:', d)
print('\'Hi!\' in d:', 'Hi!' in d)
print('7 in d:', 7 in d)
```

    a+b: (1, 2, 3, 4, 5, 6)
    c*3 ('Hi!', 'Hi!', 'Hi!')
    d: (1, 2, 3, 4, 5, 6, 'Hi!')
    'Hi!' in d: True
    7 in d: False


## Tuples are Iterable, Indexable, and Sliceable


```python
# Iteration
example = ('C', 'Java', 'Python', 'C#', 'JavaScript')

print('Tuple example items:')
for language in example:
    print(language)
print('--')

# Indexing
print('Index 1:', example[1])
print('Last Value:', example[-1])

# Slicing
print('Backwards:', example[::-1])
print('Every other:', example[::2])
print('From 1 to end:', example[1:])
print('From 1 to 3:', example[1:3])
```

    Tuple example items:
    C
    Java
    Python
    C#
    JavaScript
    --
    Index 1: Java
    Last Value: JavaScript
    Backwards: ('JavaScript', 'C#', 'Python', 'Java', 'C')
    Every other: ('C', 'Python', 'JavaScript')
    From 1 to end: ('Java', 'Python', 'C#', 'JavaScript')
    From 1 to 3: ('Java', 'Python')


## Built-in Functions with Tuple


```python
example = ('C', 'Java', 'Python', 'C#', 'JavaScript')

print('Length:', len(example))
print('Minimum value:', min(example))
print('Maximum value:', max(example))
print('--')

word = 'Hello'
array = [1,2,3,4]
array_array = [[1],[2,3],[4]]

print('String to Tuple:', tuple(word))
print('List to Tuple:', tuple(array))
print('2D array to Tuple:', tuple(array_array))
print('--')

array_array[0][0] = 'p'
print(array_array)

# Note: don't have mutable data type as items in a tuple ...
```

    Length: 5
    Minimum value: C
    Maximum value: Python
    --
    String to Tuple: ('H', 'e', 'l', 'l', 'o')
    List to Tuple: (1, 2, 3, 4)
    2D array to Tuple: ([1], [2, 3], [4])
    --
    [['p'], [2, 3], [4]]


## Tuple Comprehension


```python
# Tuple of Even values from 1 to 100
even_tup = tuple(i for i in range(1,101) if i % 2 == 0)

print(even_tup)
```

    (2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42, 44, 46, 48, 50, 52, 54, 56, 58, 60, 62, 64, 66, 68, 70, 72, 74, 76, 78, 80, 82, 84, 86, 88, 90, 92, 94, 96, 98, 100)


The parentheses were taken for a different functionality in python; therefore, we have to do comprehension like this.

The general format is the exactly the same as list comprehension.

## Tuple & Python: Packing and Unpacking


```python
# Examine the following code

# Packing
var_1 = 2
var_2 = 3
var_3 = 5

prime = var_1, var_2, var_3

print('Packed prime values:', prime)

# Unpacking and Repacking
fib = (0, 1, 1, 2, 3, 5, 8)

fib_0, fib_1, fib_n = fib[0], fib[1], fib[2:]
print('fib_0:', fib_0)
print('fib_1:', fib_1)
print('fib_n:', fib_n)
```

    Packed prime values: (2, 3, 5)
    fib_0: 0
    fib_1: 1
    fib_n: (1, 2, 3, 5, 8)


**Explanation:**
- Packing collect multiple variable's values and assign it to a single variable
- Unpacking help us assign certain values from a tuple to different variables
- This becomes very useful skill when combined with variable arguments for Function Definition and Function Calls
