---
title: Working with Python Lists
author: Python Developer
date: 2024-01-15
jupyter:
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Working with Lists

+++ {"part": "abstract"}
This section dives into practical list manipulation techniques, including adding/removing elements, slicing, sorting, and using list comprehensions for efficient data processing! Master the skills needed to dynamically modify and work with lists in real-world Python programming scenarios.
+++

Lists provide dynamic capabilities for data manipulation. Programming resources have [information about algorithms](https://en.wikipedia.org/wiki/Algorithm): hover over the link for more information. Hover over [this link to see list methods](xref:code:list-methods)!

% An admonition containing a tip
:::{tip}
Always remember that list indices in Python start at 0, not 1! This is a common source of off-by-one errors for beginners. When in doubt, use `len(your_list)` to check the actual number of elements.
:::

If you have a list of n elements and you want to reverse it, you'd need n/2 swap operations according to [](#eq:reverse). If instead you use Python's built-in reverse method, it's optimized for better performance!

% A reverse operation equation
:::{math}
:label: eq:reverse
:name: eq:reverse

\text{swaps} = \frac{n}{2}
:::

*Where:*
- *swaps = number of swap operations needed*
- *n = total number of elements in the list*

Understanding list operations visually can enhance comprehension. The visualization in [](#fig:list-operations) demonstrates key concepts for adding and removing elements!

## Adding Elements to Lists

### Using `append()`

```{code-cell} python
# Start with an empty list
shopping_list = []
print("Initial list:", shopping_list)

# Append single items
shopping_list.append('milk')
shopping_list.append('eggs')
shopping_list.append('bread')
print("After appending:", shopping_list)

# Append in a loop
for item in ['cheese', 'butter', 'juice']:
    shopping_list.append(item)
print("After loop appending:", shopping_list)
```

### Using `insert()`

```{code-cell} python
# Create a list of numbers
numbers = [10, 20, 30, 40]
print("Original list:", numbers)

# Insert at beginning
numbers.insert(0, 5)
print("After inserting 5 at index 0:", numbers)

# Insert in the middle
numbers.insert(3, 25)
print("After inserting 25 at index 3:", numbers)

# Insert at the end (same as append)
numbers.insert(len(numbers), 50)
print("After inserting at the end:", numbers)

# Insert with negative index
numbers.insert(-2, 35)
print("After inserting 35 at index -2:", numbers)
```

### Using `extend()`

```{code-cell} python
# Start with a base list
fruits = ['apple', 'banana']
print("Original fruits:", fruits)

# Extend with another list
more_fruits = ['cherry', 'date', 'elderberry']
fruits.extend(more_fruits)
print("After extending:", fruits)

# Extend with other iterables
fruits.extend('fig')  # Adds each character!
print("After extending with string:", fruits)

# Better way for single string
fruits.pop()  # Remove the 'g'
fruits.pop()  # Remove the 'i'
fruits.pop()  # Remove the 'f'
fruits.append('fig')
print("After fixing:", fruits)

# Extend with tuple
fruits.extend(('grape', 'honeydew'))
print("After extending with tuple:", fruits)
```

## Removing Elements from Lists

### Using `remove()`

```{code-cell} python
# List with duplicate values
colors = ['red', 'blue', 'green', 'blue', 'yellow', 'blue']
print("Original colors:", colors)

# Remove first occurrence
colors.remove('blue')
print("After removing first 'blue':", colors)

# Remove another element
colors.remove('green')
print("After removing 'green':", colors)

# What happens with non-existent element?
try:
    colors.remove('purple')
except ValueError as e:
    print(f"Error when removing 'purple': {e}")
```

### Using `pop()`

```{code-cell} python
# Create a list
stack = [10, 20, 30, 40, 50]
print("Original stack:", stack)

# Pop from the end (default)
last_item = stack.pop()
print(f"Popped item: {last_item}")
print("Stack after pop:", stack)

# Pop from specific position
second_item = stack.pop(1)
print(f"Popped item at index 1: {second_item}")
print("Stack after popping index 1:", stack)

# Pop from beginning
first_item = stack.pop(0)
print(f"Popped item at index 0: {first_item}")
print("Stack after popping index 0:", stack)
```

### Using `del` Statement

```{code-cell} python
# Create a list
data = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print("Original data:", data)

# Delete single element
del data[2]
print("After deleting index 2:", data)

# Delete slice
del data[1:4]
print("After deleting slice 1:4:", data)

# Delete using negative index
del data[-1]
print("After deleting last element:", data)

# Delete entire list
del data  # The list no longer exists!
try:
    print(data)
except NameError as e:
    print(f"Error: {e}")
```

### Using `clear()`

```{code-cell} python
# Create a list
inventory = ['sword', 'shield', 'potion', 'key']
print("Original inventory:", inventory)
print("Number of items:", len(inventory))

# Clear the entire list
inventory.clear()
print("\nAfter clear():", inventory)
print("Number of items:", len(inventory))
print("Is the list empty?", not inventory)
```

## Accessing and Modifying Elements

### Direct Index Modification

```{code-cell} python
# Create a mutable list
temperatures = [68, 72, 65, 70, 74]
print("Original temperatures:", temperatures)

# Modify single element
temperatures[2] = 67
print("After modifying index 2:", temperatures)

# Modify with negative index
temperatures[-1] = 75
print("After modifying last element:", temperatures)

# Multiple modifications in sequence
temperatures[0] += 2  # Increase by 2
temperatures[1] -= 1  # Decrease by 1
print("After arithmetic modifications:", temperatures)
```

### Slice Modification

```{code-cell} python
# Create a list
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print("Original numbers:", numbers)

# Replace a slice
numbers[2:5] = [20, 30, 40]
print("After replacing slice 2:5:", numbers)

# Replace with different sized slice
numbers[6:8] = [60, 70, 80, 90]
print("After replacing with larger slice:", numbers)

# Replace with smaller slice
numbers[1:4] = [15]
print("After replacing with smaller slice:", numbers)

# Insert elements (replace empty slice)
numbers[1:1] = [12, 13, 14]
print("After inserting at index 1:", numbers)

# Delete elements (replace with empty list)
numbers[4:7] = []
print("After deleting slice 4:7:", numbers)
```

## Sorting and Reordering

### Using `sort()`

```{code-cell} python
# Unsorted lists
numbers = [5, 2, 8, 1, 9, 3]
fruits = ['banana', 'apple', 'cherry', 'date']
mixed_case = ['Banana', 'apple', 'cherry', 'Date']

print("Original numbers:", numbers)
print("Original fruits:", fruits)
print("Original mixed case:", mixed_case)

# Sort numbers in place
numbers.sort()
print("\nSorted numbers (ascending):", numbers)

# Sort in descending order
numbers.sort(reverse=True)
print("Sorted numbers (descending):", numbers)

# Sort strings alphabetically
fruits.sort()
print("\nSorted fruits:", fruits)

# Case-insensitive sort
mixed_case.sort(key=str.lower)
print("Case-insensitive sort:", mixed_case)
```

### Using `sorted()`

```{code-cell} python
# Original list remains unchanged
original = [5, 2, 8, 1, 9, 3]
print("Original list:", original)

# Create a new sorted list
sorted_list = sorted(original)
print("New sorted list:", sorted_list)
print("Original list (unchanged):", original)

# Sort with custom key
words = ['banana', 'pie', 'apple', 'cherry', 'date']
sorted_by_length = sorted(words, key=len)
print("\nWords sorted by length:", sorted_by_length)

# Multiple sorting criteria
students = [
    ('Alice', 'B', 12),
    ('Bob', 'A', 12),
    ('Charlie', 'B', 15),
    ('Diana', 'A', 10)
]

# Sort by grade, then age
sorted_students = sorted(students, key=lambda x: (x[1], x[2]))
print("\nStudents sorted by grade, then age:")
for student in sorted_students:
    print(f"  {student}")
```

### Using `reverse()`

```{code-cell} python
# Create a list
sequence = [1, 2, 3, 4, 5]
print("Original sequence:", sequence)

# Reverse in place
sequence.reverse()
print("After reverse():", sequence)

# Reverse back using slicing
sequence = sequence[::-1]
print("After slicing reverse:", sequence)

# Using reversed() function (returns iterator)
reversed_iterator = reversed(sequence)
reversed_list = list(reversed_iterator)
print("Using reversed() function:", reversed_list)
```

## List Comprehensions

### Basic Comprehensions

```{code-cell} python
# Traditional approach
squares = []
for x in range(10):
    squares.append(x ** 2)
print("Traditional squares:", squares)

# List comprehension equivalent
squares_comprehension = [x ** 2 for x in range(10)]
print("Comprehension squares:", squares_comprehension)

# More examples
even_numbers = [x for x in range(20) if x % 2 == 0]
print("\nEven numbers 0-19:", even_numbers)

word_lengths = [len(word) for word in ['apple', 'banana', 'cherry']]
print("Word lengths:", word_lengths)
```

### Nested Comprehensions

```{code-cell} python
# Create a 2D list (matrix)
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print("Original matrix:")
for row in matrix:
    print(f"  {row}")

# Flatten the matrix
flattened = [num for row in matrix for num in row]
print("\nFlattened matrix:", flattened)

# Transpose the matrix
transposed = [[row[i] for row in matrix] for i in range(len(matrix[0]))]
print("\nTransposed matrix:")
for row in transposed:
    print(f"  {row}")

# Create multiplication table
table = [[i * j for j in range(1, 6)] for i in range(1, 6)]
print("\nMultiplication table (1-5):")
for row in table:
    print(f"  {row}")
```

## Visualizing List Operations

% A figure illustrating list operations
:::{figure} https://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/CPT-Lists-addingandremoving.png/600px-CPT-Lists-addingandremoving.png?raw=true
:name: fig:list-operations
:label: fig:list-operations
:width: 500px

Visual representation of list operations showing how elements are added and removed. This demonstrates the dynamic nature of Python lists and how they can grow and shrink as needed.
:::

## Practice Exercises

Try these exercises to reinforce your learning:

```{admonition} Exercise 1: List Manipulation
:class: practice

Start with this list: `[10, 20, 30, 40, 50]`
1. Insert 25 between 20 and 30
2. Remove the element 40
3. Append 60 to the end
4. Reverse the list
5. Sort the list in descending order
```

```{admonition} Exercise 2: List Comprehension
:class: practice

Using list comprehension:
1. Create a list of squares for numbers 1 through 10
2. Create a list of even numbers between 1 and 50
3. Given a list of words `['apple', 'banana', 'cherry', 'date']`, create a list of their first letters
4. Create a list of tuples `(x, x², x³)` for x from 1 to 5
```

```{code-cell} python
:tags: [hide-cell]
# Solutions (hidden by default)
print("Exercise 1 Solution:")
my_list = [10, 20, 30, 40, 50]
my_list.insert(2, 25)  # Insert at index 2
print("1. After insert:", my_list)
my_list.remove(40)
print("2. After remove 40:", my_list)
my_list.append(60)
print("3. After append 60:", my_list)
my_list.reverse()
print("4. After reverse:", my_list)
my_list.sort(reverse=True)
print("5. After descending sort:", my_list)

print("\nExercise 2 Solution:")
squares = [x**2 for x in range(1, 11)]
print("1. Squares 1-10:", squares)
evens = [x for x in range(1, 51) if x % 2 == 0]
print("2. Evens 1-50 (first 5):", evens[:5], "...")
words = ['apple', 'banana', 'cherry', 'date']
first_letters = [word[0] for word in words]
print("3. First letters:", first_letters)
powers = [(x, x**2, x**3) for x in range(1, 6)]
print("4. Powers 1-5:", powers)
```

## Key Methods Summary

:::{list-table} Essential List Methods
:header-rows: 1
:widths: 30 40 30

* - Method
  - Description
  - Returns
* - **append(x)**
  - Add x to end of list
  - None
* - **insert(i, x)**
  - Insert x at index i
  - None
* - **extend(iterable)**
  - Add all items from iterable
  - None
* - **remove(x)**
  - Remove first occurrence of x
  - None
* - **pop([i])**
  - Remove and return item at index i
  - The item
* - **clear()**
  - Remove all items
  - None
* - **sort(key, reverse)**
  - Sort list in place
  - None
* - **reverse()**
  - Reverse list in place
  - None
* - **copy()**
  - Return shallow copy of list
  - New list
:::

## Next Steps

Now that you've mastered working with lists, you're ready to explore advanced techniques. Continue to the next section to learn about:

:::{button-ref} list_instructions.md
:color: primary
:expand:

Advanced List Techniques: Comprehensions and Built-in Functions
:::

```{admonition} Pro Tip
:class: tip

When working with large lists, consider using list comprehensions instead of loops for better performance. Python's list comprehensions are optimized and often faster than equivalent for-loop implementations.
```

---

*Keep practicing! The best way to master list manipulation is to write code and experiment with different operations.*
