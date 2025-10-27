---

## **Lab Sessions - Master Study Notes**

This guide covers the key concepts from your lab sessions: Object-Oriented Programming (Classes and the `__init__` constructor) and the `zip()` function.

### **1. Lab 3: Object-Oriented Programming (OOP) in Python**

OOP is a programming paradigm that uses "objects" to represent real-world entities. It's built on the core concepts of classes and objects.

- **Class:** A **blueprint** for creating objects. It defines the attributes (data) and methods (functions/behavior) that its objects will have.
- **Object (Instance):** A specific instance created from a class. Each object has its own set of attributes. For example, if `Car` is a class, then two different cars on the road are two different objects of that class.

---

#### **Function/Method Reference: The `__init__()` Constructor**

---

##### **Method: `__init__()`**

- **Syntax:** `def __init__(self, param1, param2, ...):`
- **Purpose:** The special **constructor** method for a class. Its primary job is to **initialize the attributes** of an object when it is first created. It sets the initial state of the object.
- **Parameters:**
  - `self`: **(Required)** The first parameter of any instance method. It is a reference to the specific instance of the object being created. Python passes this argument automatically in the background. You use it to access and define attributes for that instance (e.g., `self.name = "John"`).
  - `param1`, `param2`, ... (optional): Any other parameters needed to set up the object's initial state. These values are passed when you create the object.
- **Returns:** `None`. The `__init__` method never returns a value. Its purpose is to modify the newly created object.
- **Example from material (Lab 3, Q1):**

  ```python
  class Car:
    # The constructor for the Car class
    def __init__(self, model, year):
      # self.model and self.year are "instance attributes"
      self.model = model
      self.year = year

  # When this line is executed, __init__ is called automatically
  car1 = Car("Tesla", 2022)
  ```

- **Additional examples:**

  ```python
  # Example 1: A Student class
  class Student:
      def __init__(self, student_id, name):
          self.id = student_id
          self.name = name
          self.courses = [] # Initialize with an empty list

  # Example 2: Creating student objects
  student1 = Student("s123", "Alice")
  student2 = Student("s456", "Bob")
  ```

- **Output (from additional examples):**
  - No direct output is printed, but two `Student` objects are created in memory.
  - `student1.id` would be `"s123"`.
  - `student2.name` would be `"Bob"`.
  - `student1.courses` would be `[]`.
- **Notes (Mastery Focus):**
  - `__init__` is a "dunder" method (double underscore). These are special methods in Python.
  - **Crucial Point:** You **never call `__init__` directly** (e.g., `car1.__init__(...)`). Python calls it for you when you create an object: `car1 = Car(...)`.
  - The `self` parameter is **not optional**. It's a mandatory convention. Omitting it will cause a `TypeError`.

---

#### **Problem Analysis from Lab 3 MCQs**

##### **Question 1 & 6: Basic Object Creation and Constructor Theory**

- **Code:**

  ```python
  class Car:
    def __init__(self, model, year):
      self.model = model
      self.year = year

  car1 = Car("Tesla", 2022)
  car2 = Car("Toyota", 2019)

  print(car1.model, car1.year)
  print(car2.model, car2.year)
  ```

- **Line-by-Line Explanation:**
  1.  `car1 = Car("Tesla", 2022)`: An object of the `Car` class is created. Python automatically calls `__init__` on this new object, passing `"Tesla"` for `model` and `2022` for `year`. The object's `self.model` is set to `"Tesla"` and `self.year` to `2022`.
  2.  `car2 = Car("Toyota", 2019)`: A **second, separate** object is created with its own attributes (`"Toyota"`, `2019`).
  3.  `print(car1.model, car1.year)`: Accesses and prints the attributes of the `car1` object.
  4.  `print(car2.model, car2.year)`: Accesses and prints the attributes of the `car2` object.
- **Correct Answer:** "Tesla 2022" on the first line and "Toyota 2019" on the second.
- **Key Concept:** The MCQ about constructor theory confirms that the purpose of a constructor is **"to initialize the state of an object."**

##### **Question 2: Understanding the `self` Parameter**

- **Question:** Which statement is incorrect regarding the `Teacher` program?
- **Correct Answer:** "The `self` parameter is optional in the `__init__` method."
- **Explanation:** This statement is **false**. The `self` parameter is the mechanism by which an object's methods can refer to the object itself. It is a mandatory first parameter for all instance methods, including `__init__`.

##### **Question 3: Execution Flow and Attribute Modification**

- **Code:**

  ```python
  class Teacher:
    def __init__(self, id, age):
      self.id = id
      self.age = age
      print(self.age) # This line is inside the constructor

  tear = Teacher("John", 20)
  tear.age = 30
  print(tear.age)
  ```

- **Line-by-Line Explanation:**
  1.  `tear = Teacher("John", 20)`: The `Teacher` object is created. The `__init__` method is called.
  2.  Inside `__init__`, `self.age` is set to `20`.
  3.  The line `print(self.age)` is executed **during initialization**. It prints `20`.
  4.  After the object is created, the line `tear.age = 30` **modifies** the `age` attribute of the `tear` object directly.
  5.  `print(tear.age)` prints the new, updated value of the attribute.
- **Correct Answer:** `20` followed by `30` on the next line.

##### **Question 4: Pass-by-Assignment with Immutable Types**

- **Code:**

  ```python
  class Test:
    def __init__(self):
      self.variable = 'Old'
      self.change(self.variable)

    def change(self, var):
      var = 'New' # This only changes the local variable 'var'

  obj = Test()
  print(obj.variable)
  ```

- **Line-by-Line Explanation:**
  1.  `obj = Test()`: A `Test` object is created, and its `__init__` method is called.
  2.  `self.variable = 'Old'`: The instance attribute `obj.variable` is created and points to the string object `'Old'`.
  3.  `self.change(self.variable)`: The `change` method is called. The _value_ of `self.variable` (the string `'Old'`) is passed as an argument.
  4.  Inside `change(self, var)`, a **local variable** named `var` is created. It now also points to the string object `'Old'`.
  5.  `var = 'New'`: This is the crucial step. Since strings are **immutable**, this line does **not** change the original `'Old'` string. Instead, it makes the **local variable `var`** point to a completely new string object, `'New'`. The instance attribute `obj.variable` is **unaffected** and still points to `'Old'`.
  6.  The `change` method finishes. The local variable `var` is destroyed.
  7.  `print(obj.variable)`: This prints the value of the instance attribute, which was never changed.
- **Correct Answer:** `'Old'` is printed.
- **Key Concept:** This demonstrates Python's "pass-by-assignment" behavior. When you pass an immutable object (like a string, number, or tuple), you can't change the original object from inside the function. Reassigning the parameter to a new value only affects the local scope of that function.

##### **Question 5: Methods Calling Other Methods**

- **Code:**

  ```python
  class MyClass:
    def __init__(self, value):
      self.value = value
    def manipulate(self, value):
      return value * 2
    def calculate(self):
      return self.manipulate(self.value)

  obj = MyClass(5)
  print(obj.calculate())
  ```

- **Line-by-Line Explanation:**
  1.  `obj = MyClass(5)`: An object is created, and its `self.value` attribute is set to `5`.
  2.  `print(obj.calculate())`: The `calculate` method is called on the `obj` instance.
  3.  Inside `calculate`, the line `return self.manipulate(self.value)` is executed. This means "call the `manipulate` method _on this same object_ (`self`), and pass it my own `value` attribute (`self.value`, which is 5)".
  4.  The `manipulate` method is called with `value=5`.
  5.  `manipulate` calculates `5 * 2` and returns `10`.
  6.  The return value `10` is passed back to the `calculate` method, which in turn returns it to the `print` function.
- **Correct Answer:** `10`.

---

### **2. Lab 6: The `zip()` Function**

The `zip()` function is a built-in utility that acts like a zipper, combining multiple iterables (like lists or tuples) element by element.

---

#### **Function Reference: `zip()`**

---

##### **Function: `zip()`**

- **Syntax:** `zip(*iterables)`
- **Purpose:** To create an iterator that aggregates elements from two or more iterables. The i-th tuple it produces contains the i-th element from each of the argument iterables.
- **Parameters:**
  - `*iterables`: One or more iterable objects (e.g., `zip(list1, list2, list3)`).
- **Returns:** A **zip object**, which is an **iterator**. An iterator is an object that can be looped over but generates its values one at a time, making it very memory efficient. You can convert it to a list or tuple to see all its values at once.
- **Example from material (Lab 6, Q1):**
  ```python
  list1 = ['a', 'b', 'c']
  list2 = [1, 2, 3]
  # zip creates an iterator that will yield ('a', 1), then ('b', 2), then ('c', 3)
  result = tuple(zip(list1, list2))
  print(result)
  ```
- **Additional examples:**

  ```python
  # Example 1: Zipping lists of different lengths
  names = ['Alice', 'Bob']
  ages = [30, 25, 40] # '40' will be ignored
  result_list = list(zip(names, ages))
  print(result_list)

  # Example 2: Zipping three iterables
  letters = ('A', 'B', 'C')
  numbers = [1, 2, 3]
  symbols = "!@#"
  result_list_3 = list(zip(letters, numbers, symbols))
  print(result_list_3)
  ```

- **Output:**
  ```
  (('a', 1), ('b', 2), ('c', 3))
  [('Alice', 30), ('Bob', 25)]
  [('A', 1, '!'), ('B', 2, '@'), ('C', 3, '#')]
  ```
- **Notes (Mastery Focus):**
  - **The Golden Rule of `zip()`:** The iterator stops as soon as the **shortest** input iterable is exhausted. Any remaining elements in the longer iterables are ignored. This is the most important behavior to remember and was the subject of MCQ questions 2 and 3.
  - **"Unzipping":** You can reverse the process using the `*` operator: `unzipped = zip(*result)`.

---

#### **Problem Analysis from Lab 6 MCQs**

##### **Question 1: Basic Zipping**

- **Code:**
  ```python
  list1 = ['a', 'b', 'c']
  list2 = [1, 2, 3]
  result = tuple(zip(list1, list2))
  print(result)
  ```
- **Explanation:** `zip` pairs `'a'` with `1`, `'b'` with `2`, and `'c'` with `3`. The `tuple()` constructor consumes these pairs from the zip iterator to create a single tuple containing three tuples.
- **Correct Answer:** `(('a', 1), ('b', 2), ('c', 3))`

##### **Question 2 & 3: Zipping Iterables of Different Lengths**

- **Code:**
  ```python
  list1 = [10, 20, 30] # Length 3
  list2 = ['apple', 'banana', 'cherry', 'date'] # Length 4
  result = list(zip(list1, list2))
  print(result)
  ```
- **Explanation:**
  1.  `zip` takes the first element from each list: `(10, 'apple')`.
  2.  It takes the second from each: `(20, 'banana')`.
  3.  It takes the third from each: `(30, 'cherry')`.
  4.  It tries to take a fourth element from `list1`, but `list1` is now exhausted. Because the shortest iterable is finished, the `zip` operation stops.
  5.  The element `'date'` from `list2` is ignored.
- **Correct Answer (Q2):** `[(10, 'apple'), (20, 'banana'), (30, 'cherry')]`
- **Correct Answer (Q3 - Theory):** "The resulting iterator's length is determined by the shortest input iterable." This is a direct test of the core `zip()` rule.
