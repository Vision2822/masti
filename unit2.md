## **Unit 2: Collections & Functions - Master Study Notes**

### **1. Introduction to Data Structures in Python**

A **data structure** is a specialized format for organizing, processing, retrieving, and storing data. Python has several powerful built-in data structures.

#### **1.1. Classification of Data Structures**

- **Sequential Data Structures:** Store elements in a defined order. You can access elements using their position or **index**.
  - **Examples:** Lists, Tuples, Strings.
- **Non-Sequential Data Structures:** Store elements without a specific order. Access is typically done through a **key** or by iterating over the collection.
  - **Examples:** Dictionaries, Sets.

#### **1.2. Common Operations on Collections**

| Operation                     | Description                                     | Applies To             |
| :---------------------------- | :---------------------------------------------- | :--------------------- |
| **Indexing `[ ]`**            | Access an element at a specific position.       | Lists, Tuples, Strings |
| **Slicing `[ : ]`**           | Extract a subsequence from the collection.      | Lists, Tuples, Strings |
| **Concatenation `+`**         | Combine two collections of the same type.       | Lists, Tuples, Strings |
| **Repetition `*`**            | Repeat the contents of a collection.            | Lists, Tuples, Strings |
| **Membership `in`, `not in`** | Check if an element exists within a collection. | All Collections        |
| **`len()`**                   | Get the number of items in a collection.        | All Collections        |
| **`min()`, `max()`**          | Get the minimum or maximum item.                | All Collections        |
| **`sum()`**                   | Get the sum of all numeric items.               | Lists, Tuples, Sets    |

---

### **2. Lists: The Mutable Workhorse**

A list is an **ordered and mutable** collection of items. It is one of the most versatile data structures in Python.

#### **2.1. Key Characteristics of Lists**

- **Ordered:** The items in a list have a defined order, and that order will not change unless you modify it.
- **Mutable:** You can change, add, and remove items in a list after it has been created.
- **Heterogeneous:** A single list can contain items of different data types (e.g., integers, strings, and even other lists).
- **Allows Duplicates:** Lists can contain multiple occurrences of the same value.
- **Iterable (Eager):** A list is an "eager" object, meaning all its elements are created and stored in memory at once when the list is defined.

#### **2.2. Creating Lists**

```python
# Create an empty list
empty_list_a = []
empty_list_b = list()

# Create a list with items
my_list = [1, "hello", 3.14, True]

# Create a list from another iterable
list_from_tuple = list((1, 2, 3)) # -> [1, 2, 3]
```

#### **2.3. Accessing and Modifying List Items**

- **Indexing:** Access an item by its position. Indexing starts at **0**.
  ```python
  numbers = [10, 20, 30, 40]
  print(numbers[0])   # Output: 10
  print(numbers[-1])  # Negative indexing: gets the last item. Output: 40
  ```
- **Modifying:** Since lists are mutable, you can change an item directly.

  ```python
  numbers[1] = 25 # The list is now [10, 25, 30, 40]
  ```

- **Slicing:** Extract a new sub-list from the original.
  - **Syntax:** `my_list[start:stop:step]`
  - `start`: The index to begin the slice (inclusive).
  - `stop`: The index to end the slice (exclusive).
  - `step`: The interval between indices.
  ```python
  numbers = [0, 1, 2, 3, 4, 5, 6]
  print(numbers[2:5])     # Output: [2, 3, 4]
  print(numbers[:3])      # Output: [0, 1, 2] (from the start)
  print(numbers[3:])      # Output: [3, 4, 5, 6] (to the end)
  print(numbers[::2])     # Output: [0, 2, 4, 6] (every second element)
  print(numbers[::-1])    # Output: [6, 5, 4, 3, 2, 1, 0] (reverses the list)
  ```

#### **2.4. Important List Methods**

| Method                    | Description                                                                                                        | Example                        |
| :------------------------ | :----------------------------------------------------------------------------------------------------------------- | :----------------------------- |
| **`append(item)`**        | Adds an item to the **end** of the list.                                                                           | `my_list.append(5)`            |
| **`insert(index, item)`** | Inserts an item at a specified index.                                                                              | `my_list.insert(1, "new")`     |
| **`extend(iterable)`**    | Appends all items from an iterable to the list.                                                                    | `my_list.extend([6, 7])`       |
| **`remove(item)`**        | Removes the **first** occurrence of an item.                                                                       | `my_list.remove("hello")`      |
| **`pop(index)`**          | Removes and returns the item at a given index. If no index is specified, it removes and returns the **last** item. | `item = my_list.pop(0)`        |
| **`clear()`**             | Removes all items from the list.                                                                                   | `my_list.clear()`              |
| **`sort()`**              | Sorts the list in place (modifies the original list).                                                              | `numbers.sort()`               |
| **`reverse()`**           | Reverses the order of the list in place.                                                                           | `numbers.reverse()`            |
| **`index(item)`**         | Returns the index of the first occurrence of an item.                                                              | `idx = my_list.index("hello")` |
| **`count(item)`**         | Returns the number of times an item appears in the list.                                                           | `c = my_list.count(5)`         |

#### **2.5. Copying Lists: A Common Pitfall**

> **Mastery Tip:** Understanding the difference between a reference and a copy is crucial.

- **Assignment (Reference):** `list_b = list_a` does **not** create a new list. It just makes `list_b` another name (reference) for the _same_ list object. Changing one will affect the other.

- **Copying (New Object):** To create a true, independent copy, use slicing or the `.copy()` method.

  ```python
  list_a = [1, 2, 3]

  # Method 1: Slicing (most common)
  list_b = list_a[:]

  # Method 2: .copy() method
  list_c = list_a.copy()

  list_b[0] = 99
  print(list_a) # Output: [1, 2, 3] (original is unaffected)
  print(list_b) # Output: [99, 2, 3]
  ```

---

### **3. Tuples: The Immutable Sibling**

A tuple is an **ordered and immutable** collection of items. Think of it as a "read-only" list.

#### **3.1. Key Characteristics of Tuples**

- **Ordered:** Items have a defined order.
- **Immutable:** Once a tuple is created, you **cannot** change, add, or remove items.
- **Heterogeneous:** Can contain items of different data types.
- **Faster than Lists:** Because they are immutable, Python can optimize their storage, making them slightly faster to access.

#### **3.2. Why Use a Tuple?**

1.  **Data Integrity:** When you have data that should not be changed (e.g., coordinates, RGB color values), a tuple protects it from accidental modification.
2.  **Dictionary Keys:** Because they are immutable, tuples can be used as keys in a dictionary. Lists cannot.

#### **3.3. Creating Tuples**

```python
# Create an empty tuple
empty_tuple_a = ()
empty_tuple_b = tuple()

# Create a tuple with items
my_tuple = (1, "hello", 3.14)

# Special Case: Creating a tuple with a single item requires a trailing comma
single_item_tuple = (1,) # Without the comma, this would just be the integer 1
```

#### **3.4. Tuple Operations**

- You can access items using **indexing** and **slicing**, just like lists.
- You can use **concatenation (`+`)** and **repetition (`*`)** to create _new_ tuples.
  ```python
  t1 = (1, 2)
  t2 = (3, 4)
  t3 = t1 + t2 # t3 is a new tuple: (1, 2, 3, 4)
  ```
- You **cannot** use methods that modify the tuple, like `.append()`, `.remove()`, or `.sort()`.

---

### **4. Dictionaries: Key-Value Pairs**

A dictionary is an **unordered, mutable** collection that stores data in **key-value pairs**. It's optimized for retrieving a value when you know the key.

#### **4.1. Key Characteristics of Dictionaries**

- **Unordered:** The items do not have a defined order (though in modern Python versions, they preserve insertion order, you should not rely on it).
- **Mutable:** You can add, change, and remove key-value pairs.
- **Indexed by Keys:** You access values using their associated key, not by a numerical index.
- **Keys must be Unique and Immutable:**
  - Each key in a dictionary must be unique.
  - Keys must be of an immutable data type (e.g., string, number, tuple). **This is why lists cannot be keys.**
- **Values can be anything:** Values can be of any data type and can be duplicated.

#### **4.2. Creating and Accessing Dictionaries**

```python
# Create an empty dictionary
empty_dict_a = {}
empty_dict_b = dict()

# Create a dictionary
student = {"name": "Alice", "age": 25, "courses": ["Math", "CompSci"]}

# Access a value using its key
print(student["name"]) # Output: Alice

# Add or update a key-value pair
student["age"] = 26      # Updates the existing key
student["id"] = "S123"   # Adds a new key-value pair
```

#### **4.3. Important Dictionary Methods**

| Method                   | Description                                                                                                                                  | Example                                    |
| :----------------------- | :------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------- |
| **`get(key, default)`**  | Safely gets the value for a key. If the key doesn't exist, it returns `None` (or the specified `default` value) instead of raising an error. | `age = student.get("age", 0)`              |
| **`keys()`**             | Returns a view object containing all the keys.                                                                                               | `for k in student.keys(): print(k)`        |
| **`values()`**           | Returns a view object containing all the values.                                                                                             | `for v in student.values(): print(v)`      |
| **`items()`**            | Returns a view object where each item is a `(key, value)` tuple. Best for looping.                                                           | `for k, v in student.items(): print(k, v)` |
| **`pop(key)`**           | Removes the specified key and returns its value.                                                                                             | `name = student.pop("name")`               |
| **`update(other_dict)`** | Merges another dictionary into the current one.                                                                                              | `student.update({"city": "New York"})`     |

---

### **5. Sets: Unique and Unordered**

A set is an **unordered, mutable** collection of **unique, hashable** items.

#### **5.1. Key Characteristics of Sets**

- **Unordered:** Items have no defined order.
- **Unique:** A set cannot contain duplicate elements.
- **Mutable:** You can add and remove items from a set.
- **Hashable Elements:** The items inside a set must be of an immutable type (like numbers, strings, or tuples).

#### **5.2. Why Use a Set?**

1.  **Removing Duplicates:** Quickly get a unique collection of items from another iterable.
    ```python
    my_list = [1, 2, 2, 3, 4, 3]
    unique_items = set(my_list) # -> {1, 2, 3, 4}
    ```
2.  **Fast Membership Testing:** Checking if an item is `in` a set is significantly faster than checking if it's `in` a list.
3.  **Mathematical Set Operations:** Perform union, intersection, difference, etc.

#### **5.3. Creating Sets**

> **Common Mistake:** `empty = {}` creates an empty **dictionary**, not an empty set.

```python
# Create an empty set
empty_set = set()

# Create a set with items
my_set = {1, "hello", 3.14} # Duplicates are automatically removed
```

#### **5.4. Set Operations and Methods**

| Operation                | Method                        | Operator  | Description                                                            |
| :----------------------- | :---------------------------- | :-------- | :--------------------------------------------------------------------- | -------------------------------- |
| **Union**                | `s1.union(s2)`                | `s1       | s2`                                                                    | All items from both sets.        |
| **Intersection**         | `s1.intersection(s2)`         | `s1 & s2` | Items that exist in both sets.                                         |
| **Difference**           | `s1.difference(s2)`           | `s1 - s2` | Items in `s1` but not in `s2`.                                         |
| **Symmetric Difference** | `s1.symmetric_difference(s2)` | `s1 ^ s2` | Items in either set, but not both.                                     |
| **Add**                  | `s1.add(item)`                | -         | Adds a single item to the set.                                         |
| **Update**               | `s1.update(iterable)`         | `s1       | = s2`                                                                  | Adds all items from an iterable. |
| **Remove**               | `s1.remove(item)`             | -         | Removes an item. Raises a `KeyError` if the item is not found.         |
| **Discard**              | `s1.discard(item)`            | -         | Removes an item. Does **not** raise an error if the item is not found. |

---

### **6. Strings: Immutable Sequences of Characters**

A string is an **ordered and immutable** sequence of characters.

- **Characteristics:** Immutable, ordered, iterable, and indexable.
- **Operations:** All operations that "modify" a string (like `.replace()` or `.upper()`) return a **new string**; they do not change the original.
- **Creation:** Use single (`'...'`), double (`"..."`), or triple (`"""..."""` for multi-line) quotes.
- **Common Methods:**
  - **Changing Case:** `.upper()`, `.lower()`, `.capitalize()`, `.title()`
  - **Searching:** `.find(sub)`, `.index(sub)`, `.startswith(sub)`, `.endswith(sub)`
  - **Modifying/Cleaning:** `.replace(old, new)`, `.strip()`, `.lstrip()`, `.rstrip()`
  - **Splitting/Joining:**
    - `.split(separator)`: Splits a string into a list of substrings.
    - `separator.join(list_of_strings)`: Joins a list of strings into a single string using the separator.
  - **Checking Content:** `.isalpha()`, `.isdigit()`, `.isalnum()`, `.isspace()`

---

### **7. File Handling**

Files are used for **persistent storage**, meaning the data remains even after the program has finished running.

#### **7.1. The Three-Step Process**

1.  **Open** the file using the `open()` function.
2.  **Read or Write** to the file using file object methods.
3.  **Close** the file using the `.close()` method to free up system resources.

#### **7.2. The `with` Statement (Best Practice)**

The `with` statement is the recommended way to handle files because it **automatically closes the file** for you, even if errors occur.

```python
with open("my_file.txt", "w") as f:
    f.write("Hello, World!")
# The file is automatically closed here
```

#### **7.3. File Modes**

| Mode   | Description                                                                   |
| :----- | :---------------------------------------------------------------------------- |
| `'r'`  | **Read** (default). Fails if the file doesn't exist.                          |
| `'w'`  | **Write**. Creates a new file. **Overwrites** the file if it exists.          |
| `'a'`  | **Append**. Creates a new file. Adds new content to the **end** if it exists. |
| `'r+'` | **Read and Write**.                                                           |
| `'w+'` | **Write and Read**. Overwrites the file.                                      |
| `'a+'` | **Append and Read**.                                                          |

#### **7.4. Reading and Writing Text Files**

| Method                            | Description                                                         |
| :-------------------------------- | :------------------------------------------------------------------ |
| **`read()`**                      | Reads the entire file content into a single string.                 |
| **`readline()`**                  | Reads one line from the file, including the newline character `\n`. |
| **`readlines()`**                 | Reads all lines into a list of strings.                             |
| **`write(string)`**               | Writes a single string to the file.                                 |
| **`writelines(list_of_strings)`** | Writes each string from a list to the file.                         |

#### **7.5. Working with CSV Files**

CSV (Comma-Separated Values) files are used for tabular data. Python's built-in `csv` module makes them easy to work with.

- **`csv.reader(file_object)`:** Creates a reader object to iterate over rows in the CSV file. Each row is a **list of strings**.
- **`csv.writer(file_object)`:** Creates a writer object to write data to a CSV. Use `.writerow()` for a single row (list) or `.writerows()` for multiple rows (list of lists).
- **`csv.DictReader(file_object)`:** Similar to `reader`, but each row is an **ordered dictionary**, where the keys are the column headers.
- **`csv.DictWriter(file_object, fieldnames=...)`:** Writes data from a list of dictionaries. You must specify the `fieldnames` (headers).

**Example: Reading with `DictReader`**

```python
import csv

with open('data.csv', 'r') as csvfile:
    reader = csv.DictReader(csvfile)
    for row in reader:
        print(f"Name: {row['Name']}, Age: {row['Age']}")
```

---

### **8. Functions**

A function is a reusable block of organized code that is used to perform a single, related action.

#### **8.1. Why Use Functions?**

- **Reusability:** Write code once and use it multiple times.
- **Modularity:** Break down complex problems into smaller, manageable pieces.
- **Abstraction:** Hide the complex implementation details and only expose the functionality.

#### **8.2. Defining and Calling a Function**

- **`def` keyword:** Used to define a function.
- **`return` keyword:** Used to send a value back from the function. If omitted, the function returns `None`.
- **Function Call:** To execute the function, you call it by its name followed by parentheses `()`.

```python
# Definition
def add_numbers(a, b):
    result = a + b
    return result

# Call
sum_value = add_numbers(5, 10) # sum_value is now 15
```

#### **8.3. Arguments and Parameters**

- **Parameter:** The variable listed inside the parentheses in the function **definition** (e.g., `a` and `b` above).
- **Argument:** The actual value that is sent to the function when it is **called** (e.g., `5` and `10` above).

#### **8.4. Types of Arguments**

1.  **Positional Arguments:** The default type. Arguments are matched to parameters based on their position. The order matters.
2.  **Keyword Arguments:** You specify which parameter the argument is for by using the parameter name. The order does not matter.

    > **Rule:** Keyword arguments must come _after_ positional arguments in a function call.
    > `my_func(10, y=20)` is valid. `my_func(x=10, 20)` is **invalid**.

3.  **Default Arguments:** You can provide a default value for a parameter in the function definition. This makes the argument optional when the function is called.

    > **Rule:** Default parameters must come _after_ non-default parameters in the function definition.

4.  **Arbitrary Positional Arguments (`*args`):** Allows a function to accept any number of positional arguments. These arguments are collected into a **tuple**.
5.  **Arbitrary Keyword Arguments (`**kwargs`):** Allows a function to accept any number of keyword arguments. These arguments are collected into a **dictionary\*\*.

**Example of all types:**

```python
def example_func(a, b, c='default', *args, **kwargs):
    print(f"a (positional): {a}")
    print(f"b (positional): {b}")
    print(f"c (default): {c}")
    print(f"args (tuple): {args}")
    print(f"kwargs (dict): {kwargs}")

# Function call
example_func(1, 2, 'custom', 4, 5, name='Alice', city='New York')
```

#### **8.5. Scope and the LEGB Rule**

Scope determines the visibility of a variable. Python searches for a variable in the following order:

1.  **L - Local:** The innermost scope, inside the current function.
2.  **E - Enclosing:** The scope of any enclosing functions (for nested functions).
3.  **G - Global:** The top-level scope of the module/script.
4.  **B - Built-in:** Python's built-in names (e.g., `len`, `print`).

- **`global` keyword:** To modify a global variable from within a function, you must declare it with `global`.
- **`nonlocal` keyword:** To modify a variable in an enclosing scope (but not global), you use `nonlocal`.
