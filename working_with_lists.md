```markdown
---
title: Introduction to Python Lists
author: Python Developer
date: 2024-01-15
jupyter:
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Introduction to Lists

+++ {"part": "abstract"}
This section introduces Python lists, covering their basic characteristics, creation methods, and fundamental operations. Perfect for beginners starting their journey with Python data structures! Learn how to create, access, and understand the fundamental properties of one of Python's most versatile data structures.
+++

Lists are ordered collections in Python that can store items of different data types. Programming documentation has [information about data structures](https://en.wikipedia.org/wiki/Data_structure): hover over the link for more information. Hover over [this link to see list examples](xref:code:basic-lists)!

% An admonition containing a note
:::{note}
Unlike arrays in some other programming languages, Python lists can contain elements of different types - integers, strings, floats, and even other lists can all coexist in the same list! This makes them incredibly flexible for various programming tasks.
:::

If you create a list with 10 elements and access the middle element, you'd use index 4 according to [](#eq:indexing). If instead you want the last element, you'd use index -1, which is Python's convenient negative indexing feature!

% An indexing equation
:::{math}
:label: eq:indexing
:name: eq:indexing

\text{last\_index} = \text{length} - 1
:::

*Where:*
- *last_index = position of the last element*
- *length = total number of elements in the list*

Sometimes when learning lists it helps to see visual representations. The concept in [](#fig:list-structure) would be very helpful for understanding how lists are organized in memory!

## Creating Lists

Lists can be created in several ways in Python. Here are the most common methods:

### Using Square Brackets

```{code-cell} python
# Empty list
empty_list = []
print("Empty list:", empty_list)
print("Type:", type(empty_list))

# List with integers
numbers = [1, 2, 3, 4, 5]
print("\nNumber list:", numbers)

# List with mixed types
mixed = [1, "hello", 3.14, True, [1, 2, 3]]
print("\nMixed list:", mixed)
```

### Using the list() Constructor

```{code-cell} python
# From a string
letters = list("python")
print("From string:", letters)

# From a tuple
my_tuple = (1, 2, 3)
list_from_tuple = list(my_tuple)
print("From tuple:", list_from_tuple)

# From a range
numbers_range = list(range(5))
print("From range:", numbers_range)
```

### List Multiplication

```{code-cell} python
# Creating lists with repetition
repeated = [0] * 5
print("Repeated zeros:", repeated)

repeated_text = ["hello"] * 3
print("Repeated text:", repeated_text)
```

## Accessing List Elements

### Basic Indexing

```{code-cell} python
fruits = ['apple', 'banana', 'cherry', 'date', 'elderberry']

# Positive indexing (starts at 0)
print("First fruit (index 0):", fruits[0])
print("Third fruit (index 2):", fruits[2])

# Negative indexing (starts at -1 from the end)
print("Last fruit (index -1):", fruits[-1])
print("Second last fruit (index -2):", fruits[-2])
```

### Slicing Lists

```{code-cell} python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Basic slicing
print("First 5 elements:", numbers[:5])
print("Elements 2 to 5:", numbers[2:6])
print("Last 3 elements:", numbers[-3:])
print("All elements:", numbers[:])

# Slicing with step
print("Every 2nd element:", numbers[::2])
print("Reverse the list:", numbers[::-1])
print("Every 3rd element starting from index 1:", numbers[1::3])
```

## List Characteristics and Properties

### Checking List Properties

```{code-cell} python
# Create a sample list
sample_list = [10, 20, 30, 40, 50]

# Length of list
print("Length of list:", len(sample_list))

# Checking if empty
empty_check = []
print("Is empty list empty?", len(empty_check) == 0)
print("Better way:", not empty_check)

# Checking membership
print("Is 30 in the list?", 30 in sample_list)
print("Is 100 in the list?", 100 in sample_list)
print("Is 30 not in the list?", 30 not in sample_list)
```

### Type Checking

```{code-cell} python
# Different ways to check if something is a list
my_list = [1, 2, 3]
my_tuple = (1, 2, 3)
my_string = "hello"

print("Is my_list a list?", isinstance(my_list, list))
print("Is my_tuple a list?", isinstance(my_tuple, list))
print("Is my_string a list?", isinstance(my_string, list))
print("Type of my_list:", type(my_list))
```

## Basic List Operations

### Concatenation

```{code-cell} python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# Using + operator
combined = list1 + list2
print("Combined list:", combined)

# Note: Original lists remain unchanged
print("Original list1:", list1)
print("Original list2:", list2)
```

### Repetition

```{code-cell} python
base_list = [1, 2, 3]

# Repeat list multiple times
repeated = base_list * 3
print("Repeated list:", repeated)

# Repeat with different multiplier
half_repeated = base_list * 0
print("Empty list (multiply by 0):", half_repeated)
```

### Comparison

```{code-cell} python
list_a = [1, 2, 3]
list_b = [1, 2, 3]
list_c = [1, 2, 4]
list_d = [1, 2]

print("list_a == list_b?", list_a == list_b)
print("list_a == list_c?", list_a == list_c)
print("list_a > list_d?", list_a > list_d)
print("list_d < list_a?", list_d < list_a)
```

## Common List Methods

Here are some essential list methods you should know:

```{code-cell} python
# Creating a list to demonstrate methods
colors = ['red', 'green', 'blue']

# append() - Add to the end
colors.append('yellow')
print("After append:", colors)

# insert() - Add at specific position
colors.insert(1, 'orange')
print("After insert at index 1:", colors)

# index() - Find position of element
position = colors.index('blue')
print("Position of 'blue':", position)

# count() - Count occurrences
colors.append('red')
red_count = colors.count('red')
print("Count of 'red':", red_count)
```

## Visualizing List Structure

% A figure illustrating list structure
:::{figure} https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Array_of_array_storage.svg/500px-Array_of_array_storage.svg.png?raw=true
:name: fig:list-structure
:label: fig:list-structure
:width: 400px

Visual representation of how lists are stored in memory. Each element has an index starting from 0, and lists can contain different data types including other lists (nested lists).
:::

## Practice Exercises

Try these exercises to reinforce your learning:

```{admonition} Exercise 1: Create and Access
:class: practice

Create a list called `student_grades` with the following grades: 85, 92, 78, 90, 88. Then:
1. Print the first grade
2. Print the last grade
3. Print grades 2 through 4
4. Print every other grade
```

```{admonition} Exercise 2: List Operations
:class: practice

Given two lists:
```python
list_a = [1, 2, 3]
list_b = [4, 5, 6]
```
1. Create a new list that combines both lists
2. Create a new list that repeats list_a three times
3. Check if the number 3 is in list_a
4. Check if the number 7 is not in list_b
```

```{code-cell} python
:tags: [hide-cell]
# Solutions (hidden by default)
print("Exercise 1 Solution:")
student_grades = [85, 92, 78, 90, 88]
print("1. First grade:", student_grades[0])
print("2. Last grade:", student_grades[-1])
print("3. Grades 2-4:", student_grades[1:4])
print("4. Every other grade:", student_grades[::2])

print("\nExercise 2 Solution:")
list_a = [1, 2, 3]
list_b = [4, 5, 6]
combined = list_a + list_b
print("1. Combined:", combined)
repeated = list_a * 3
print("2. Repeated:", repeated)
print("3. Is 3 in list_a?", 3 in list_a)
print("4. Is 7 not in list_b?", 7 not in list_b)
```

## Key Takeaways

:::{list-table} List Fundamentals Summary
:header-rows: 1
:widths: 40 60

* - Concept
  - Description
* - **Creation**
  - Use square brackets `[]` or `list()` constructor
* - **Indexing**
  - Zero-based, supports negative indices
* - **Slicing**
  - `list[start:stop:step]` syntax
* - **Mutability**
  - Lists can be modified after creation
* - **Heterogeneous**
  - Can contain different data types
* - **Ordered**
  - Maintains insertion order
* - **Dynamic**
  - Can grow and shrink as needed
:::

## Next Steps

Now that you understand the basics of Python lists, you're ready to learn how to manipulate them. Continue to the next section to learn about:

:::{button-ref} working_with_lists.md
:color: primary
:expand:

Working with Lists: Adding, Removing, and Modifying Elements
:::

```{admonition} Remember
:class: tip

Lists are one of the most frequently used data structures in Python. Master these fundamentals well, as they form the foundation for more advanced list operations and other Python data structures.
```