---

## **Unit 1: Introduction to Python - Master Study Notes**

### **1. The World of Computational Problem Solving**

This section covers the foundational theory of how we approach problem-solving with computers. It explains the "what" and "why" before we get to the "how" with Python.

#### **1.1. Classification of Tasks & Problems**

- **Computational Tasks:** These are tasks a computer can perform. They are logical, follow a sequence of steps, and can be described by an algorithm.
  - _Examples:_ Sorting a list, finding the shortest path, calculating payroll.
- **Non-Computational Tasks:** Tasks performed by humans that involve understanding, consciousness, or emotion.
  - _Examples:_ Recognizing a face, understanding a poem, feeling empathy.
- **Classification of Computational Problems:** When tackling a computational problem, we must consider two main aspects:
  1.  **Representation:** How to represent the problem's data in a way a computer can process (e.g., representing a maze as a grid of numbers).
  2.  **Algorithm:** The step-by-step procedure to solve the problem.

#### **1.2. The Process of Computational Problem Solving (CPS)**

This is a structured, multi-stage process that moves from a problem idea to a tested, working program.

1.  **Analysis:**
    - **Goal:** Understand the problem completely. This involves identifying inputs, desired outputs, constraints, and the core computational challenges.
    - **Example (from slides):** For the "Missionaries, Cannibals, Goat, Wolf" (MCGW) problem, the analysis involves understanding the rules: the boat's capacity, which combinations are unsafe, etc. You would also identify what constitutes a solution (getting everyone across safely).
2.  **Design:**
    - **Goal:** Create the blueprint for a solution. This is where you develop the **algorithm** (the logical steps) and decide on the **data structures** (how to store the state of the problem, e.g., who is on which river bank).
    - **Brute-Force Approach:** A common starting point mentioned in your notes. It involves trying every single possible solution. While simple, it is often too slow for complex problems. For the MCGW problem, this means trying every possible rowing action.
3.  **Implementation:**
    - **Goal:** Write the actual code based on the design. This involves translating your algorithm into a programming language like Python, paying close attention to the language's **syntax** (rules) and features.
4.  **Testing:**
    - **Goal:** Verify that the program works correctly. As the slides note, "programming errors are pervasive, persistent and inevitable."
    - **Process:** Testing is done incrementally during development and thoroughly upon completion using a well-designed **test plan** with multiple **test cases**.

#### **1.3. Algorithms**

- **Definition:** An algorithm is a finite, unambiguous, step-by-step procedure for solving a general problem.
- **Key Properties (from MCQs):**
  1.  It has a **finite number of steps**.
  2.  It produces a result in a **finite amount of time**.
  3.  It solves a **general problem** (not just one specific instance).

### **2. The Digital Computer: Hardware and Software**

A digital computer processes information in **discrete form** (using binary 0s and 1s).

#### **2.1. Computer Hardware**

These are the physical components of the system.

- **CPU (Central Processing Unit):** The "brain" that executes instructions.
- **Main Memory (RAM - Random Access Memory):** Temporary storage for currently running programs and data. **RAM is volatile**, meaning its contents are lost when the power is turned off. (This answers an MCQ).
- **Secondary Memory:** Permanent storage (Hard Drive, SSD). It is **non-volatile**.
- **Buses:** Communication channels that transfer data between components.

#### **2.2. Computer Software**

These are the programs and instructions that run on the hardware.

- **System Software:** Manages the computer hardware and provides a platform for other software. It works in the background.
  - **The Operating System** is the most critical piece of system software. (This answers an MCQ).
  - Other examples include **compilers, interpreters, assemblers**, and device drivers.
- **Application Software:** Used by users to perform specific tasks (e.g., web browser, word processor).

#### **2.3. Program Translation: Compilers, Interpreters, Assemblers**

Since computers only understand machine code (binary), our human-readable source code must be translated.

- **Compiler:** Translates the **entire source code** into machine code at once, creating a standalone executable file. This process happens _before_ the program is run.
- **Interpreter:** Translates and executes the source code **line by line** _as the program is run_. Python is primarily an interpreted language.
- **Assembler:** A specialized translator that converts low-level assembly language into machine code.

| Feature            | Compiler                                     | Interpreter                           |
| :----------------- | :------------------------------------------- | :------------------------------------ |
| **How it works**   | Translates the whole program at once.        | Translates and runs line by line.     |
| **Output**         | An executable file.                          | Direct output from execution.         |
| **Speed**          | Generally faster execution.                  | Slower execution but faster to start. |
| **Error Handling** | Reports all syntax errors after compilation. | Stops at the first error encountered. |

### **3. Introduction to Python Programming**

Python is a high-level, interpreted language known for its simple and readable syntax.

#### **3.1. Program Structure and Basic Syntax**

- **Execution Flow:** Code is executed sequentially from the top of the file to the bottom.
- **Indentation is KEY:** Python uses indentation (spaces or tabs at the beginning of a line) to define code blocks. Incorrect indentation will cause an `IndentationError`. This is a rigid format, not free-form.
- **Case-Sensitivity:** `myVar` and `myvar` are different variables.
- **Statements:**
  - Ideally, one statement per line.
  - A statement can span multiple lines using a backslash `\` or by being enclosed in parentheses `()`, brackets `[]`, or braces `{}`.
- **Comments:**
  - Single-line comments start with `#`.
  - Multi-line comments (or docstrings) are enclosed in triple quotes `"""..."""` or `'''...'''`.

#### **3.2. Identifiers, Keywords, and Literals**

- **Identifiers:** Names given to variables, functions, etc.
  - **Rules:** Must start with a letter or underscore (`_`), followed by letters, numbers, or underscores. Cannot be a keyword.
  - _Valid:_ `total_sales`, `_value`, `name1`
  - _Invalid:_ `1st_place`, `total-sales`, `for`
- **Keywords:** Reserved words with special meaning. You cannot use them as variable names.
  - _Examples:_ `if`, `else`, `for`, `while`, `def`, `True`, `False`, `None`, `is`, `in`, `and`, `or`, `not`, `pass`.
- **Literals:** Data items with a fixed value.
  - _Examples:_ `100` (integer), `3.14` (float), `"Hello"` (string).

---

### **Function and Keyword Reference: Unit 1**

Here is a detailed breakdown of every function and important keyword from your Unit 1 materials.

#### **I/O Functions**

---

##### **Function: `print()`**

- **Syntax:** `print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)`
- **Purpose:** Displays the value of one or more arguments to the output screen (console).
- **Parameters:**
  - `*objects`: One or more objects (variables, literals, expressions) to be printed.
  - `sep` (optional keyword): The string to insert between values. Defaults to a single space `' '`.
  - `end` (optional keyword): The string to append after the last value. Defaults to a newline character `'\n'`.
- **Returns:** `None`.
- **Example from material:**
  ```python
  # Using the default separator (space)
  print(10, 12, 14)
  ```
- **Additional examples:**

  ```python
  name = "Alice"
  age = 30

  # Example 1: Custom separator
  print("Name", name, "Age", age, sep=": ")

  # Example 2: Preventing the newline
  print("Processing...", end="")
  print(" Done!")

  # Example 3: Printing an expression
  print("5 + 3 =", 5 + 3)
  ```

- **Output:**
  ```
  10 12 14
  Name: Alice: Age: 30
  Processing... Done!
  5 + 3 = 8
  ```
- **Notes (Mastery Focus):**
  - The `print` statement in Python 2 was different (`print "hello"`). Python 3 requires parentheses, treating it as a function. This is a common point of confusion.
  - To print a variable's value, pass the variable itself (`print(my_var)`), not its name as a string (`print("my_var")`). This was a specific MCQ question.
  - **Common Mistake:** Trying to concatenate strings and numbers directly in `print`, like `print("Age: " + 25)`, will cause a `TypeError`. The correct way is to use a comma: `print("Age:", 25)`.

---

##### **Function: `input()`**

- **Syntax:** `input(prompt)`
- **Purpose:** Reads a line of text from the user's keyboard.
- **Parameters:**
  - `prompt` (optional): A string that is displayed to the user before they enter input.
- **Returns:** The user's input as a **string**.
- **Example from material:**
  ```python
  a = input("Enter the length in cm: ")
  print(type(a)) # This will show <class 'str'>
  ```
- **Additional examples:**

  ```python
  # Example 1: Reading a name
  name = input("What is your name? ")
  print("Hello, " + name)

  # Example 2: Reading a number and converting it
  age_str = input("Enter your age: ")
  age_int = int(age_str) # Type conversion is necessary for math
  print("Next year, you will be", age_int + 1)
  ```

- **Output (for Example 2, user enters 29):**
  ```
  Enter your age: 29
  Next year, you will be 30
  ```
- **Notes (Mastery Focus):**
  - **Crucial Point:** `input()` **ALWAYS** returns a string, even if the user types only numbers. You must explicitly convert the type using functions like `int()` or `float()` if you need to perform calculations. This is a very common source of `TypeError`.
  - The MCQ on this topic reinforces this: `age = input('Enter your age:')`, then `age // 10` would cause a `TypeError` if `age` wasn't converted to an integer first.

---

##### **Function: `split()` (String Method)**

- **Syntax:** `string.split(sep=None, maxsplit=-1)`
- **Purpose:** Splits a string into a list of substrings.
- **Parameters:**
  - `sep` (optional): The delimiter string to split on. If not specified, it splits on any whitespace (spaces, tabs, newlines).
  - `maxsplit` (optional): The maximum number of splits to do.
- **Returns:** A **list** of strings.
- **Example from material:**
  ```python
  marks_str = input("Enter maths and science marks: ") # User enters "95 99"
  marks_list = marks_str.split()
  print(marks_list)
  ```
- **Additional examples:**

  ```python
  date = "27-10-2025"
  parts = date.split('-')
  print(parts)

  sentence = "one two three"
  # maxsplit example
  words = sentence.split(' ', 1)
  print(words)
  ```

- **Output:**
  ```
  ['95', '99']
  ['27', '10', '2025']
  ['one', 'two three']
  ```
- **Notes (Mastery Focus):** `split()` is essential for reading multiple values from a single line of user input. The resulting list items will still be strings and may need further type conversion.

---

#### **Utility and Type Functions**

---

##### **Function: `id()`**

- **Syntax:** `id(object)`
- **Purpose:** Returns the unique identity (memory address) of an object.
- **Parameters:**
  - `object`: Any Python object (variable, literal, etc.).
- **Returns:** An **integer** representing the object's unique ID.
- **Example from material:**
  ```python
  k = 2
  print(id(k))
  num = 2
  print(num is k) # Checks if ids are the same
  ```
- **Output:**
  ```
  140735642076104
  True
  ```
- **Notes (Mastery Focus):** The `id()` is guaranteed to be unique for simultaneously existing objects. It's the primary way to check if two variables refer to the _exact same object_ versus two different objects with the same value. This is the foundation of the `is` operator.

---

##### **Function: `type()`**

- **Syntax:** `type(object)`
- **Purpose:** Returns the type of an object.
- **Parameters:**
  - `object`: Any Python object.
- **Returns:** A **type object**.
- **Example from material:**
  ```python
  a = 10
  print(type(a))
  a = 10.0
  print(type(a))
  ```
- **Output:**
  ```
  <class 'int'>
  <class 'float'>
  ```
- **Notes (Mastery Focus):** Python is **dynamically typed**, meaning a variable's type can change during program execution simply by assigning it a value of a different type. `type()` is essential for debugging to check what kind of data your variable is currently holding.

---

##### **Type Conversion Functions (`int()`, `float()`, `bool()`, `complex()`, `list()`)**

- **Syntax:** `new_type(value)`
- **Purpose:** To convert a value from one data type to another. This is also known as **type casting**.
- **Returns:** A new object of the specified type.
- **Examples:**

  ```python
  str_num = "100"
  int_num = int(str_num) # Converts string to integer
  print(type(int_num))

  float_num = float(int_num) # Converts integer to float
  print(float_num)

  # Using list() with range()
  r = range(3)
  l = list(r) # Converts the range object into a list
  print(l)
  ```

- **Output:**
  ```
  <class 'int'>
  100.0
  [0, 1, 2]
  ```
- **Notes (Mastery Focus):**
  - Type conversion can fail. `int("hello")` will raise a `ValueError`.
  - **Type Coercion** is different. It's the _implicit_ or automatic conversion of types by Python during an operation (e.g., `2 + 3.5` automatically converts the `2` to `2.0` before adding). **Type Casting** is _explicit_ conversion by the programmer. The MCQ `(float) 2 + 4.5` is an example of explicit conversion (casting), not coercion.

---

##### **Function: `help()`**

- **Syntax:** `help(object)`
- **Purpose:** Invokes the built-in help system. If called with no arguments, it enters an interactive help session. If called with an object, it prints information about that object.
- **Example from material:** Typing `help()` in the Python prompt starts the interactive help utility, where you can then type `keywords` to see a list of all Python keywords.

---

##### **Function: `range()`**

- **Syntax:** `range(stop)` or `range(start, stop, step=1)`
- **Purpose:** Generates an immutable sequence of numbers.
- **Parameters:**
  - `start` (optional): The starting number (inclusive). Defaults to 0.
  - `stop`: The ending number (**exclusive**).
  - `step` (optional): The increment between numbers. Defaults to 1.
- **Returns:** A **range object**.
- **Example from material:**
  ```python
  # Using range in a for loop
  for i in range(0, 4):
      print(i)
  ```
- **Additional examples:**
  ```python
  # Convert range to list to see its contents
  print(list(range(5)))
  print(list(range(2, 8)))
  print(list(range(10, 0, -2)))
  ```
- **Output:**
  ```
  0
  1
  2
  3
  [0, 1, 2, 3, 4]
  [2, 3, 4, 5, 6, 7]
  [10, 8, 6, 4, 2]
  ```
- **Notes (Mastery Focus):** `range()` is **lazy**. It doesn't store all the numbers in memory at once. It generates them one by one as needed, making it very efficient for loops over large number sequences. To see all the values at once, you must convert it to another type, like a `list`.

---

#### **Keywords Used for Control and Logic**

---

##### **Keywords: `if`, `elif`, `else`**

- **Purpose:** Used for selection or decision control. They allow you to execute different blocks of code based on whether a condition is true or false.
- **Syntax:**
  ```python
  if <condition1>:
      # block of code
  elif <condition2>:
      # block of code
  else:
      # block of code
  ```
- **Notes:** The `elif` and `else` clauses are optional. An `if` statement marks the beginning of a **selection construct**.

---

##### **Keywords: `for`, `while`**

- **Purpose:** Used for iterative control (loops).
- **`while` Loop:** Repeats a block of code as long as a condition is `True`.
- **`for` Loop:** Iterates over the items of any sequence (like a list, tuple, or range object) in the order that they appear in the sequence.

---

##### **Keyword: `pass`**

- **Purpose:** The `pass` statement is a null operation; nothing happens when it executes.
- **Use Case:** It is used as a placeholder where a statement is syntactically required, but you don't want any code to execute. This is common when creating stub functions or empty classes that you plan to implement later. (This answers an MCQ).

---

##### **Keywords: `is`, `is not` (Identity Operators)**

- **Purpose:** To check if two variables refer to the exact same object in memory.
- **How it Works:** It's a shorthand for comparing the result of `id(a) == id(b)`.
- **Returns:** `True` or `False`.
- **Notes:** This is different from `==`, which checks for equality of _values_.

---

##### **Keywords: `in`, `not in` (Membership Operators)**

- **Purpose:** To test whether a value is present in a sequence (like a list, tuple, or string).
- **Returns:** `True` or `False`.
- **Example:** `'E' in 'PES'` returns `True`.

---

##### **Keywords: `and`, `or`, `not` (Logical Operators)**

- **Purpose:** To combine or invert boolean expressions.
- **`and`:** Returns `True` only if both operands are true.
- **`or`:** Returns `True` if at least one operand is true.
- **`not`:** Inverts the boolean value (`not True` is `False`).
- **Short-Circuit Evaluation:**
  - For `x and y`: If `x` is false, `y` is **not evaluated**.
  - For `x or y`: If `x` is true, `y` is **not evaluated**.
  - This is an important optimization and can be used for conditional execution.
- **MCQ Analysis:** The question `15 and 10` is tricky. In Python, non-zero numbers are "truthy". The `and` operator evaluates the first operand (15). Since it's truthy, it _must_ evaluate the second operand (10) and returns its value. So, the result is `10`. If it were `0 and 10`, the result would be `0` because of short-circuiting.
