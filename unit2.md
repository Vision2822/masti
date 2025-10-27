---

## **Unit 2: Collections & Functions - Master Study Notes**

This unit covers Python's core data structures (collections) and the powerful concept of functions, which are essential for writing organized, reusable, and efficient code.

### **1. General Introduction to Data Structures**

A **data structure** is a way of organizing and storing data so that it can be accessed and modified efficiently.

- **Sequential vs. Non-Sequential:**
  - **Sequential:** Elements are stored in a specific order and can be accessed via an index (e.g., lists, tuples, strings).
  - **Non-Sequential:** Elements are not stored in a particular order. Access is often via a key (e.g., dictionaries) or by membership (e.g., sets).
- **Mutability:**
  - **Mutable:** The object's contents can be changed after it is created (e.g., lists, dictionaries, sets).
  - **Immutable:** The object's contents cannot be changed after creation (e.g., tuples, strings, numbers).

---

### **Function Reference: Built-in Functions for Collections**

These functions work on many different types of collections.

---

##### **Function: `len()`**

- **Syntax:** `len(collection)`
- **Purpose:** Returns the number of items in a collection.
- **Parameters:**
  - `collection`: A sequence (string, list, tuple) or collection (dictionary, set).
- **Returns:** An **integer** representing the item count.
- **Example from material:**
  ```python
  nums = [3, 41, 12, 9, 74, 15]
  print(len(nums))
  ```
- **Additional examples:**
  ```python
  print(len("Python"))
  print(len({'name': 'John', 'age': 30})) # Counts key-value pairs
  ```
- **Output:**
  ```
  6
  6
  2
  ```
- **Notes:** This is one of the most frequently used functions. For dictionaries, it counts the number of key-value pairs.

---

##### **Function: `max()`**

- **Syntax:** `max(iterable)`
- **Purpose:** Returns the largest item in an iterable.
- **Parameters:**
  - `iterable`: A collection of comparable items (e.g., all numbers or all strings).
- **Returns:** The largest item from the iterable.
- **Example from material:**
  ```python
  nums = [3, 41, 12, 9, 74, 15]
  print(max(nums))
  ```
- **Additional examples:**
  ```python
  print(max("python")) # Based on Unicode value, 'y' is the largest
  print(max({10, 50, 20}))
  ```
- **Output:**
  ```
  74
  y
  50
  ```
- **Notes:** This will raise a `TypeError` if you try to compare items of incompatible types, like a number and a string (`max([1, 'a'])` will fail).

---

##### **Function: `min()`**

- **Syntax:** `min(iterable)`
- **Purpose:** Returns the smallest item in an iterable.
- **Parameters:**
  - `iterable`: A collection of comparable items.
- **Returns:** The smallest item from the iterable.
- **Example from material:**
  ```python
  nums = [3, 41, 12, 9, 74, 15]
  print(min(nums))
  ```
- **Additional examples:**
  ```python
  print(min("Python")) # Based on Unicode value, 'P' is the smallest
  ```
- **Output:**
  ```
  3
  P
  ```
- **Notes:** Same `TypeError` rules as `max()` apply.

---

##### **Function: `sum()`**

- **Syntax:** `sum(iterable, start=0)`
- **Purpose:** Returns the sum of all items in an iterable.
- **Parameters:**
  - `iterable`: A collection of numeric items.
  - `start` (optional): A value that is added to the sum. Defaults to 0.
- **Returns:** A **number** (integer or float) representing the sum.
- **Example from material:**
  ```python
  nums = [3, 41, 12, 9, 74, 15]
  print(sum(nums))
  ```
- **Additional examples:**
  ```python
  # Using the start parameter
  print(sum([10, 20, 30], 5)) # (10 + 20 + 30) + 5
  ```
- **Output:**
  ```
  154
  65
  ```
- **Notes:** This function will raise a `TypeError` if the iterable contains non-numeric types. It cannot be used on a list of strings.

---

##### **Function: `sorted()`**

- **Syntax:** `sorted(iterable, reverse=False)`
- **Purpose:** Returns a **new sorted list** from the items in an iterable.
- **Parameters:**
  - `iterable`: The collection to sort.
  - `reverse` (optional): If `True`, the list is sorted in descending order.
- **Returns:** A **new list** containing the sorted items.
- **Example from material (for Tuples):**
  ```python
  tuple1 = ('rama', 'shama', 'bhama', 'balarama')
  print(sorted(tuple1))
  ```
- **Additional examples:**

  ```python
  my_set = {10, 1, 100}
  print(sorted(my_set, reverse=True))

  my_dict = {'b': 1, 'a': 2}
  print(sorted(my_dict)) # Sorts the keys by default
  ```

- **Output:**
  ```
  ['balarama', 'bhama', 'rama', 'shama']
  [100, 10, 1]
  ['a', 'b']
  ```
- **Notes (Mastery Focus):** **`sorted()` vs `.sort()`**
  - `sorted()` is a built-in function that works on **any iterable** (list, tuple, set, dict) and **returns a new sorted list**. It does not modify the original.
  - `.sort()` is a **list method** that sorts the list **in-place**. It modifies the original list and returns `None`. You cannot use `.sort()` on a tuple or set.

---

### **2. Lists**

Lists are ordered, mutable collections that allow duplicate, heterogeneous elements.

---

#### **Function Reference: List Methods**

---

##### **Method: `append()`**

- **Syntax:** `list.append(item)`
- **Purpose:** Adds a single item to the end of the list.
- **Parameters:**
  - `item`: The object to add to the end of the list.
- **Returns:** `None`. It modifies the list in-place.
- **Example from material:**
  ```python
  list1 = [10, 20, 30, 40, 50]
  list1.append(22)
  print(list1)
  ```
- **Output:** `[10, 20, 30, 40, 50, 22]`
- **Notes:** If you append another list, it becomes a single, nested element: `[1, 2].append([3, 4])` results in `[1, 2, [3, 4]]`. Use `extend()` to add elements individually.

---

##### **Method: `insert()`**

- **Syntax:** `list.insert(index, item)`
- **Purpose:** Inserts an item at a specific position.
- **Parameters:**
  - `index`: The integer index where the item should be inserted.
  - `item`: The object to insert.
- **Returns:** `None`. It modifies the list in-place.
- **Example from material:**
  ```python
  list1 = [10, 20, 30, 40, 50]
  list1.insert(3, 55)
  print(list1)
  ```
- **Output:** `[10, 20, 30, 55, 40, 50]`

---

##### **Method: `extend()`**

- **Syntax:** `list.extend(iterable)`
- **Purpose:** Adds all the items from an iterable (like another list, tuple, or string) to the end of the current list.
- **Parameters:**
  - `iterable`: The collection whose elements are to be added.
- **Returns:** `None`. It modifies the list in-place.
- **Example from material:**
  ```python
  list1 = [10, 20, 30, 40, 50]
  list1.extend([11, 22, 33, 44, 55])
  print(list1)
  ```
- **Additional examples:**
  ```python
  my_list = [1, 2]
  my_list.extend("abc") # A string is an iterable of characters
  print(my_list)
  ```
- **Output:**
  ```
  [10, 20, 30, 40, 50, 11, 22, 33, 44, 55]
  [1, 2, 'a', 'b', 'c']
  ```
- **Notes:** `+` vs `extend()`: `my_list + another_list` creates a _new_ list, while `extend()` modifies the original list in-place, which is more memory-efficient.

---

##### **Method: `remove()`**

- **Syntax:** `list.remove(value)`
- **Purpose:** Removes the **first** occurrence of the specified value.
- **Parameters:**
  - `value`: The value to be removed.
- **Returns:** `None`.
- **Example from material:**
  ```python
  list1 = [10, 20, 30, 40, 50]
  list1.remove(40)
  print(list1)
  ```
- **Output:** `[10, 20, 30, 50]`
- **Notes:** If the value is not found, it raises a `ValueError`.

---

##### **Method: `pop()`**

- **Syntax:** `list.pop(index=-1)`
- **Purpose:** Removes and **returns** the item at a given index.
- **Parameters:**
  - `index` (optional): The index of the item to remove. If not specified, it removes the last item.
- **Returns:** The removed item.
- **Example from material:**
  ````python
  list1 = [10, 20, 30, 40, 50]
  list1.pop(2) # Removes the item at index 2 (which is 30)
  print(list1)
  ```*   **Output:** `[10, 20, 40, 50]`
  ````
- **Notes:** `remove()` works with the _value_, while `pop()` works with the _index_. `pop()` is useful when you want to use the removed item.

---

##### **Method: `clear()`**

- **Syntax:** `list.clear()`
- **Purpose:** Removes all items from the list, making it empty.
- **Returns:** `None`.
- **Example:**
  ```python
  my_list = [1, 2, 3]
  my_list.clear()
  print(my_list)
  ```
- **Output:** `[]`

---

##### **Method: `index()`**

- **Syntax:** `list.index(value, start=0, stop=len(list))`
- **Purpose:** Returns the index of the first occurrence of a value.
- **Parameters:**
  - `value`: The value to search for.
  - `start`, `stop` (optional): Search within a specific slice of the list.
- **Returns:** An **integer** index.
- **Example from material:**
  ```python
  list1 = [10, 20, 30, 40, 50]
  print(list1.index(20))
  ```
- **Output:** `1`
- **Notes:** If the value is not found, it raises a `ValueError`.

---

##### **Method: `count()`**

- **Syntax:** `list.count(value)`
- **Purpose:** Returns the number of times a value appears in the list.
- **Returns:** An **integer**.
- **Example from material:**
  ```python
  list1 = [10, 20, 30, 40, 50, 20]
  print(list1.count(20))
  ```
- **Output:** `2`

---

##### **Method: `sort()`**

- **Syntax:** `list.sort(reverse=False)`
- **Purpose:** Sorts the list **in-place**.
- **Parameters:**
  - `reverse` (optional): If `True`, sorts in descending order.
- **Returns:** `None`.
- **Example from material:**
  ```python
  list1 = [10, 1, -2, 2, 9]
  list1.sort()
  print(list1)
  ```
- **Output:** `[-2, 1, 2, 9, 10]`
- **Notes:** See the `sorted()` function for the crucial difference.

---

##### **Method: `reverse()`**

- **Syntax:** `list.reverse()`
- **Purpose:** Reverses the elements of the list **in-place**.
- **Returns:** `None`.
- **Example:**
  ```python
  my_list = [1, 2, 3]
  my_list.reverse()
  print(my_list)
  ```
- **Output:** `[3, 2, 1]`

---

##### **Method: `copy()`**

- **Syntax:** `list.copy()`
- **Purpose:** Returns a shallow copy of the list.
- **Returns:** A **new list** object.
- **Example:**
  ```python
  list_a = [1, 2]
  list_b = list_a.copy()
  print(list_a is list_b) # Check if they are the same object
  ```
- **Output:** `False`
- **Notes:** This is crucial to avoid unintended modification of the original list. `new_list = old_list[:]` is an alternative way to create a shallow copy.

---

### **3. Tuples**

Tuples are ordered, **immutable** collections. They are like "read-only" lists.

- **Benefits:** Faster than lists, can be used as dictionary keys, and protect data from accidental changes.
- **MCQ Analysis:** The question "Can tuple be used as dictionary key in python?" is **True**. This is a primary use case for tuples, as dictionary keys must be immutable.

---

#### **Function Reference: Tuple Methods**

Because tuples are immutable, they have very few methods.

---

##### **Method: `count()`**

- **Syntax:** `tuple.count(value)`
- **Purpose:** Returns the number of times a value appears in the tuple.
- **Returns:** An **integer**.
- **Example from material:**
  ```python
  tuple1 = (10, 20, 30, 10, 40, 10, 50)
  print(tuple1.count(10))
  ```
- **Output:** `3`

---

##### **Method: `index()`**

- **Syntax:** `tuple.index(value)`
- **Purpose:** Returns the index of the first occurrence of a value.
- **Returns:** An **integer** index. Raises a `ValueError` if the value is not found.
- **Example from material:**
  ```python
  tuple1 = (10, 20, 30, 40, 50)
  print(tuple1.index(30))
  ```
- **Output:** `2`

---

### **4. Dictionaries**

Dictionaries are unordered, mutable collections of **key-value pairs**. Keys must be unique and immutable.

- **MCQ Analysis:**
  - You access values using keys, but you **cannot access keys using values**.
  - `Dict = dict({1: 'hello', 2: 'everyone'})` is the correct syntax for creating a dictionary from another dictionary using the `dict()` constructor.
  - `get()` is the alternative function to access a value without causing an error if the key doesn't exist.

---

#### **Function Reference: Dictionary Methods**

---

##### **Method: `get()`**

- **Syntax:** `dict.get(key, default=None)`
- **Purpose:** Safely retrieves the value for a given key.
- **Parameters:**
  - `key`: The key to look for.
  - `default` (optional): The value to return if the key is not found.
- **Returns:** The value for the key if it exists, otherwise `default` (which is `None` if not specified).
- **Example from material:**
  ```python
  phonebook = {"Johan": 938477565, "Jill": 938547565}
  print(phonebook.get('Jill'))
  ```
- **Additional examples:**
  ```python
  print(phonebook.get('Erik')) # Key does not exist
  print(phonebook.get('Erik', 'Not Found'))
  ```
- **Output:**
  ```
  938547565
  None
  Not Found
  ```
- **Notes:** This is the preferred way to access dictionary values when you are not sure if a key exists, as it prevents a `KeyError`.

---

##### **Method: `keys()`**

- **Syntax:** `dict.keys()`
- **Purpose:** Returns a view object that displays a list of all the keys in the dictionary.
- **Returns:** A **dict_keys** view object.
- **Example from material:**
  ```python
  phonebook = {"Johan": 938477565, "Jill": 938547565}
  print(phonebook.keys())
  ```
- **Output:** `dict_keys(['Johan', 'Jill'])`
- **Notes:** You can iterate directly over a dictionary (`for key in my_dict:`) which is a shortcut for iterating over `my_dict.keys()`.

---

##### **Method: `values()`**

- **Syntax:** `dict.values()`
- **Purpose:** Returns a view object that displays a list of all the values in the dictionary.
- **Returns:** A **dict_values** view object.
- **Example from material:**
  ```python
  marks = {'Physics': 67, 'Maths': 87}
  print(marks.values())
  ```
- **Output:** `dict_values([67, 87])`

---

##### **Method: `items()`**

- **Syntax:** `dict.items()`
- **Purpose:** Returns a view object that displays a list of the dictionary's key-value tuple pairs.
- **Returns:** A **dict_items** view object.
- **Example from material:**
  ```python
  phonebook = {"Johan": 938477565, "Jill": 938547565}
  print(phonebook.items())
  ```
- **Output:** `dict_items([('Johan', 938477565), ('Jill', 938547565)])`
- **Notes:** This is the most efficient way to loop through both the keys and values of a dictionary simultaneously: `for key, value in my_dict.items():`.

---

##### **Method: `pop()`**

- **Syntax:** `dict.pop(key, default)`
- **Purpose:** Removes the specified key and returns its corresponding value.
- **Parameters:**
  - `key`: The key to remove.
  - `default` (optional): If the key is not found, this value is returned instead of raising a `KeyError`.
- **Returns:** The value of the removed key.
- **Example from material:**
  ```python
  phonebook = {"Johan": 938477565, "Jill": 938547565}
  jill_phone = phonebook.pop('Jill')
  print(jill_phone)
  print(phonebook)
  ```
- **Output:**
  ```
  938547565
  {'Johan': 938477565}
  ```

---

##### **Method: `popitem()`**

- **Syntax:** `dict.popitem()`
- **Purpose:** Removes and returns the last inserted key-value pair as a tuple.
- **Returns:** A `(key, value)` **tuple**.
- **Example from material:**
  ```python
  person = {'name': 'Phill', 'age': 22, 'salary': 3500.0}
  result = person.popitem()
  print('Return Value = ', result)
  print('person = ', person)
  ```
- **Output:**
  ```
  Return Value =  ('salary', 3500.0)
  person =  {'name': 'Phill', 'age': 22}
  ```
- **Notes:** Raises a `KeyError` if the dictionary is empty.

---

##### **Method: `update()`**

- **Syntax:** `dict.update(other_dict)`
- **Purpose:** Updates the dictionary with key-value pairs from another dictionary or an iterable of key-value pairs.
- **Returns:** `None`. It modifies the dictionary in-place.
- **Example from material:**
  ```python
  marks = {'Physics': 67, 'Maths': 87}
  internal_marks = {'Practical': 48}
  marks.update(internal_marks)
  marks.update([('Chemistry', 90)]) # Can also update from a list of tuples
  print(marks)
  ```
- **Output:** `{'Physics': 67, 'Maths': 87, 'Practical': 48, 'Chemistry': 90}`
- **Notes:** If a key already exists, `update()` will overwrite its value.

---

##### **Method: `setdefault()`**

- **Syntax:** `dict.setdefault(key, default_value)`
- **Purpose:** A safe way to add a key only if it doesn't already exist.
- **Logic:**
  1.  If `key` is in the dictionary, it returns the key's current value.
  2.  If `key` is **not** in the dictionary, it inserts the key with a value of `default_value` and then returns `default_value`.
- **Returns:** The value of the key.
- **Example from material:**
  ```python
  person = {'name': 'Phil', 'age': 22}
  # 'phone' does not exist, so it's added and its value is returned
  phone = person.setdefault('phone', 90909090)
  print('person = ', person)
  print('phone = ', phone)
  ```
- **Output:**
  ```
  person =  {'name': 'Phil', 'age': 22, 'phone': 90909090}
  phone =  90909090
  ```

---

### **5. Sets**

Sets are unordered, mutable collections of **unique, hashable** elements.

- **Key Concepts:**
  - **Unordered:** You cannot use an index to access items.
  - **Unique:** Duplicates are automatically removed.
  - **Hashable Elements:** Items in a set must be immutable (e.g., numbers, strings, tuples). You cannot put a list or another set inside a set. This is a common source of `TypeError`.
- **MCQ Analysis:**
  - `set([1,1,2,3,4,2,3,4])` correctly evaluates to `{1, 2, 3, 4}` because sets store only unique elements.
  - `s = {[1, 2]}` results in an error because lists are mutable and therefore not hashable.
  - To create an empty set, you **must use `set()`**. Using `{}` creates an empty dictionary.

---

#### **Function Reference: Set Methods**

---

##### **Set Creation & Modification**

- `add(item)`: Adds a single element. `a.add(5)` on `{5, 6, 7}` does nothing as 5 is already present.
- `update(iterable)` / `|=`: Adds all elements from another iterable.
- `remove(item)`: Removes an element. **Raises a `KeyError` if the element is not found.**
- `discard(item)`: Removes an element. **Does not raise an error if the element is not found.** This is the safer option.
- `pop()`: Removes and returns an **arbitrary** element. You don't know which one you'll get.
- `clear()`: Removes all elements.

---

##### **Mathematical Set Operations**

- `union(other_set)` or `s1 | s2`: Returns a new set with all elements from both sets.
- `intersection(other_set)` or `s1 & s2`: Returns a new set with only the elements common to both sets.
- `difference(other_set)` or `s1 - s2`: Returns a new set with elements in `s1` but **not** in `s2`.
- `symmetric_difference(other_set)` or `s1 ^ s2`: Returns a new set with elements in either `s1` or `s2`, but **not both**.

---

##### **Set Comparison Methods**

- `issubset(other)` / `<=`: Returns `True` if all elements of the set are in `other`. A set is always a subset of itself.
- `issuperset(other)` / `>=`: Returns `True` if the set contains all elements of `other`.
- `isdisjoint(other)`: Returns `True` if the two sets have no common elements.

---

##### **In-place Update Methods**

These methods modify the original set instead of returning a new one.

- `intersection_update(other)` / `&=`
- `difference_update(other)` / `-=`
- `symmetric_difference_update(other)` / `^=`

---

### **6. Functions**

A function is a named, reusable block of code that performs a specific task.

- **MCQ Analysis:**
  - Functions provide **reusability** and **modularity**.
  - A function is called using its name followed by parentheses: `my_function()`.
  - Python uses both **call by value** (for immutable types like numbers/strings) and **call by reference** (for mutable types like lists/dicts) - this is more accurately called "pass-by-assignment".

---

#### **Function Reference: Argument Types**

---

##### **Positional and Keyword Arguments**

- **Positional:** Arguments are matched to parameters based on their order. `def func(a, b): ...` called as `func(10, 20)`.
- **Keyword:** Arguments are matched by parameter name. Order doesn't matter. `func(b=20, a=10)`.
- **Rule:** Positional arguments **must** come before keyword arguments. `func(10, b=20)` is valid; `func(a=10, 20)` is a `SyntaxError`.

---

##### **Default Arguments**

- **Purpose:** To make an argument optional by providing a default value.
- **Syntax:** `def say(message, times=1): ...`
- **Rule:** Parameters with default values must come **after** parameters without default values.

---

##### **Arbitrary Positional Arguments: `*args`**

- **Syntax:** `def my_func(*args): ...`
- **Purpose:** To allow a function to accept a variable number of positional arguments.
- **How it Works:** Inside the function, `args` will be a **tuple** containing all the positional arguments passed to it.
- **Example from material:**

  ```python
  def f1(*arg):
    print(type(arg)) # Will print <class 'tuple'>
    for i in arg:
      print(i)

  f1(2, 1, 6, 4)
  ```

---

##### **Arbitrary Keyword Arguments: `**kwargs`\*\*

- **Syntax:** `def my_func(**kwargs): ...`
- **Purpose:** To allow a function to accept a variable number of keyword arguments.
- **How it Works:** Inside the function, `kwargs` will be a **dictionary** containing all the keyword arguments.
- **Example from material:**

  ```python
  def intro(**data):
      print(type(data)) # Will print <class 'dict'>
      for key, value in data.items():
          print(f"{key} is {value}")

  intro(Firstname="Sita", Age=22)
  ```

---

#### **Function Reference: Scope (LEGB Rule)**

Scope determines the visibility and lifetime of a variable. Python searches for a variable in this order:

1.  **L**ocal: Inside the current function.
2.  **E**nclosing: In the scope of any enclosing (outer) functions.
3.  **G**lobal: In the main body of the script.
4.  **B**uilt-in: Pre-defined names in Python like `len`, `print`.

- **`global` keyword:** Used inside a function to indicate that you want to **modify** a global variable, not create a new local one.
- **MCQ Analysis:** The code `i = 0; change(1); print(i)` prints `0`. The `i` inside the `change` function is a _local_ variable. Changing it does not affect the _global_ `i`. If the function had `global i` at the beginning, the output would have been `1`.

---

### **7. File Handling**

(Covered in detail in the provided notes, key functions are `open`, `read`, `readline`, `readlines`, `write`, `writelines`, `close`).

#### **Function Reference: `zip()`**

- **Syntax:** `zip(*iterables)`
- **Purpose:** To aggregate elements from two or more iterables into an iterator of tuples.
- **Parameters:**
  - `*iterables`: One or more iterables (lists, tuples, etc.).
- **Returns:** A **zip object** (an iterator).
- **Example from material (Lab 6):**
  ```python
  list1 = ['a', 'b', 'c']
  list2 = [1, 2, 3]
  result = tuple(zip(list1, list2))
  print(result)
  ```
- **Output:** `(('a', 1), ('b', 2), ('c', 3))`
- **Notes (Mastery Focus):**
  - The most important rule: The iterator stops as soon as the **shortest** input iterable is exhausted.
  - `zip()` is its own inverse when used with the `*` operator: `unzipped = list(zip(*result))` would give you `[('a', 'b', 'c'), (1, 2, 3)]`.

---

### **Mastering the `csv` Module in Python**

#### **1. What is a CSV File and Why Do We Need a Special Module?**

A **CSV (Comma-Separated Values)** file is a simple, plain-text file used to store tabular data, like a spreadsheet or a database table. Each line in the file represents a row of data, and the values (or "fields") within that row are separated by a comma.

**Example `data.csv` file:**

```csv
Name,Age,Occupation
John,30,Engineer
Sara,25,Doctor
Mike,28,Lawyer
```

While you _could_ try to read and write these files by manually splitting strings by commas, this approach is fragile and prone to errors. What if a value itself contains a comma?

> `"17, Oak Street, New York"`

The `csv` module is Python's built-in solution to handle these complexities robustly. It correctly handles quoting, delimiters, and line endings, ensuring your data is read and written accurately.

**To use the module, you must first import it:**

```python
import csv
```

---

### **2. Reading from CSV Files**

There are two primary ways to read a CSV file: as a sequence of lists or as a sequence of dictionaries.

#### **2.1 Reading Rows as Lists with `csv.reader()`**

This is the most direct way to read a CSV. Each row is returned as a **list of strings**.

---

##### **Function: `csv.reader()`**

- **Syntax:** `csv.reader(csvfile, delimiter=',', quotechar='"', ...)`
- **Purpose:** Creates a reader object that iterates over lines in the given `csvfile`. It parses the CSV data and yields each row as a list of strings.
- **Parameters:**
  - `csvfile`: A file object that has been opened (typically in read mode `'r'`).
  - `delimiter` (optional): The character used to separate fields. Defaults to a comma `,`.
  - `quotechar` (optional): The character used to quote fields containing special characters (like the delimiter). Defaults to a double quote `"`.
- **Returns:** A **reader object** (an iterator).
- **Example from material (Lab 7 / Unit 2 Slides):**

  ```python
  import csv

  # Best practice: use 'with open' to automatically close the file
  # CRUCIAL: use newline='' to prevent blank rows in the output on some systems
  with open('data.csv', mode='r', newline='') as csvfile:
      # Create a reader object
      csv_reader = csv.reader(csvfile)

      # A common pattern is to skip the header row
      header = next(csv_reader)
      print(f"Header: {header}")

      # Iterate over the remaining rows
      print("Data Rows:")
      for row in csv_reader:
          # Each 'row' is a list of strings
          print(row)
  ```

- **Input File (`data.csv`):**
  ```csv
  Name,Age,Occupation
  John,30,Engineer
  Sara,25,Doctor
  ```
- **Output:**
  ```
  Header: ['Name', 'Age', 'Occupation']
  Data Rows:
  ['John', '30', 'Engineer']
  ['Sara', '25', 'Doctor']
  ```
- **Notes (Mastery Focus):**
  - **Data Type:** Notice that all values in the list, including `'30'` and `'25'`, are **strings**. You must manually convert them to integers (`int()`) or floats (`float()`) if you need to perform calculations.
  - **Accessing Data:** You access data by its index: `row[0]` for the name, `row[1]` for the age, etc. This can be hard to maintain if the column order changes.

---

#### **2.2 Reading Rows as Dictionaries with `csv.DictReader()`**

This is a more robust and readable way to process CSV data. Each row is returned as a **dictionary**, where the keys are the column headers.

---

##### **Function: `csv.DictReader()`**

- **Syntax:** `csv.DictReader(csvfile, fieldnames=None, ...)`
- **Purpose:** Creates a reader object that works like a regular reader but maps the information in each row to a `dict`.
- **Parameters:**
  - `csvfile`: A file object opened in read mode.
  - `fieldnames` (optional): A list of strings to be used as the dictionary keys. If omitted, the values in the **first row** of the file are used as the keys.
- **Returns:** A **`DictReader` object** (an iterator).
- **Example from material (Unit 2 Slides):**

  ```python
  import csv

  with open('data.csv', mode='r', newline='') as csvfile:
      # Create a DictReader object. It automatically uses the first row as keys.
      csv_reader = csv.DictReader(csvfile)

      print("Data Rows (as Dictionaries):")
      for row in csv_reader:
          # Each 'row' is a dictionary
          print(row)
          # Now you can access data by name, which is much clearer!
          print(f"Processing {row['Name']} who is a {row['Occupation']}.")
  ```

- **Input File (`data.csv`):** (Same as before)
- **Output:**
  ```
  Data Rows (as Dictionaries):
  {'Name': 'John', 'Age': '30', 'Occupation': 'Engineer'}
  Processing John who is a Engineer.
  {'Name': 'Sara', 'Age': '25', 'Occupation': 'Doctor'}
  Processing Sara who is a Doctor.
  ```
- **Notes (Mastery Focus):**
  - **Why it's better:** Using `DictReader` makes your code more readable and resilient to change. If someone reorders the columns in your CSV file, your code will still work perfectly as long as the header names don't change. With `csv.reader`, your code would break.
  - The header row is automatically consumed and is not yielded as a data row.

---

### **3. Writing to CSV Files**

#### **3.1 Writing Lists to Rows with `csv.writer()`**

This is the counterpart to `csv.reader()`. You provide it with a list of values, and it writes them as a single CSV row.

---

##### **Function: `csv.writer()`**

- **Syntax:** `csv.writer(csvfile, delimiter=',', ...)`
- **Purpose:** Creates a writer object responsible for converting the user’s data into a delimited string on the given file-like object.
- **Parameters:**
  - `csvfile`: A file object opened in a write mode (`'w'`, `'a'`).
- **Returns:** A **writer object**.
- **Methods of the Writer Object:**
  - `writerow(list)`: Writes a single row from a list of values.
  - `writerows(list_of_lists)`: Writes multiple rows from a list of lists.
- **Example from material (Unit 2 Slides):**

  ```python
  import csv

  # Data to be written (a list of lists)
  header = ['Name', 'Age', 'Occupation']
  data_rows = [
      ['John', 30, 'Engineer'],
      ['Sara', 25, 'Doctor'],
      ['Mike', 28, 'Lawyer']
  ]

  with open('output.csv', mode='w', newline='') as csvfile:
      # Create a writer object
      csv_writer = csv.writer(csvfile)

      # Write the header row
      csv_writer.writerow(header)

      # Write all the data rows at once
      csv_writer.writerows(data_rows)

  print("output.csv has been created.")
  ```

- **Resulting File (`output.csv`):**
  ```csv
  Name,Age,Occupation
  John,30,Engineer
  Sara,25,Doctor
  Mike,28,Lawyer
  ```

---

#### **3.2 Writing Dictionaries to Rows with `csv.DictWriter()`**

This is the recommended approach for writing data, as it is more robust. You work with a list of dictionaries.

---

##### **Function: `csv.DictWriter()`**

- **Syntax:** `csv.DictWriter(csvfile, fieldnames)`
- **Purpose:** Creates an object which operates like a regular writer but maps dictionaries onto output rows.
- **Parameters:**
  - `csvfile`: A file object opened in a write mode.
  - `fieldnames`: A **required** list of strings that specifies the order in which values from the dictionaries are written. It defines the header and the column order.
- **Returns:** A **`DictWriter` object**.
- **Methods of the `DictWriter` Object:**
  - `writeheader()`: Writes the header row using the `fieldnames`.
  - `writerow(dictionary)`: Writes a single row from a dictionary.
  - `writerows(list_of_dictionaries)`: Writes multiple rows.
- **Example from material (Unit 2 Slides):**

  ```python
  import csv

  # Data to be written (a list of dictionaries)
  data = [
      {'Name': 'John', 'Age': 30, 'Occupation': 'Engineer'},
      {'Name': 'Sara', 'Age': 25, 'Occupation': 'Doctor'},
      {'Name': 'Mike', 'Age': 28, 'Occupation': 'Lawyer'}
  ]

  # The fieldnames list defines the column order in the CSV
  fieldnames = ['Name', 'Age', 'Occupation']

  with open('output_dict.csv', mode='w', newline='') as csvfile:
      # Create a DictWriter object
      csv_writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

      # Step 1: Write the header
      csv_writer.writeheader()

      # Step 2: Write the data rows
      csv_writer.writerows(data)

  print("output_dict.csv has been created.")
  ```

- **Resulting File (`output_dict.csv`):** (Same as the previous example, but created in a more maintainable way)
  ```csv
  Name,Age,Occupation
  John,30,Engineer
  Sara,25,Doctor
  Mike,28,Lawyer
  ```
- **Notes (Mastery Focus):** `DictWriter` ensures your output columns are always in the same order, defined by `fieldnames`, regardless of the key order in your individual dictionaries.

---

### **4. Crucial Best Practice: `newline=''`**

When you open a file to be used by the `csv` module, you **must** specify `newline=''`.

- **The Problem:** Different operating systems use different characters to signify the end of a line (e.g., `\n` on Linux/macOS, `\r\n` on Windows). When writing, Python's regular file handling might convert `\n` to `\r\n` on Windows. The `csv` module also handles line endings and might write `\r\n`. The result is that you get `\r\r\n` for each line, which appears as a **blank row** between every data row in your CSV file.
- **The Solution:** `newline=''` tells Python's file handler _not_ to touch the line endings and to let the `csv` module manage them exclusively. This makes your code work correctly on all operating systems.

---

### **5. Summary: `reader` vs. `DictReader` and `writer` vs. `DictWriter`**

| Object               | Reads/Writes Data As... | Access By                | Key Advantage                                         |
| :------------------- | :---------------------- | :----------------------- | :---------------------------------------------------- |
| **`csv.reader`**     | Lists of strings        | Index (`row[0]`)         | Simple and direct.                                    |
| **`csv.DictReader`** | Dictionaries            | Key name (`row['Name']`) | Highly readable, robust to column order changes.      |
| **`csv.writer`**     | Lists of values         | N/A                      | Simple for writing basic lists.                       |
| **`csv.DictWriter`** | Dictionaries            | N/A                      | Ensures consistent column order, highly maintainable. |
