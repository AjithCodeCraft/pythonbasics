# Lesson 1: Data Types and Variables

## Learning Objectives
By the end of this lesson, you will:
- Understand Python's four basic data types
- Know how to create and use variables
- Be able to check data types using type()
- Practice converting between data types

## What Are Data Types?

Think of data types as different kinds of information, just like in real life:
- **Numbers** for counting and calculations
- **Text** for names and messages
- **True/False** for yes/no questions

Python has four main data types we'll start with:

### 1. Integers (int) - Whole Numbers
```python
age = 25
year = 2024
temperature = -5
```

### 2. Floating Point Numbers (float) - Decimal Numbers
```python
price = 19.99
height = 5.8
pi = 3.14159
```

### 3. Strings (str) - Text
```python
name = "Alice"
message = "Hello, World!"
email = 'user@example.com'
```

### 4. Booleans (bool) - True or False
```python
is_student = True
is_raining = False
has_license = True
```

## Variables - Storing Information

Variables are like labeled boxes where you store information:

```python
# Creating variables
student_name = "John"
student_age = 20
student_grade = 85.5
is_passing = True
```

### Variable Naming Rules
- Use descriptive names: `student_age` not `a`
- Use underscores for multiple words: `first_name`
- Start with a letter or underscore, not a number
- No spaces or special characters (except underscore)

## Checking Data Types

Use the `type()` function to see what type of data you have:

```python
print(type(42))        # <class 'int'>
print(type(3.14))      # <class 'float'>
print(type("Hello"))   # <class 'str'>
print(type(True))      # <class 'bool'>
```

## Quick Practice Exercises

### Exercise 1.1: Create Variables
Create variables for the following information about yourself:
```python
# Your turn - create these variables:
# 1. Your first name (string)
# 2. Your age (integer)
# 3. Your height in feet (float)
# 4. Whether you like pizza (boolean)

# Example solution:
first_name = "Alex"
age = 22
height = 5.9
likes_pizza = True
```

### Exercise 1.2: Type Checking
```python
# Create these variables and use type() to check their types
mystery_1 = 100
mystery_2 = "100"
mystery_3 = 100.0
mystery_4 = False

# Use print(type(variable_name)) for each
# What do you notice about the differences?
```

## Hands-On Coding Exercise

### Exercise 1.3: Personal Information Card
Create a simple information card about yourself:

```python
# Create variables for:
full_name = "Your Full Name"
birth_year = 2000  # Your birth year
current_year = 2024
favorite_number = 7.5
is_learning_python = True

# Calculate your age
age = current_year - birth_year

# Print your information card
print("=== Personal Information Card ===")
print("Name:", full_name)
print("Age:", age)
print("Favorite Number:", favorite_number)
print("Learning Python:", is_learning_python)
print("Data Types:")
print("- Name type:", type(full_name))
print("- Age type:", type(age))
print("- Favorite Number type:", type(favorite_number))
print("- Learning Python type:", type(is_learning_python))
print(f"My name is  {full_name}")  f-string (formatted string literal)
```

## Type Conversion

Sometimes you need to convert between data types:

```python
# String to integer
age_string = "25"
age_number = int(age_string)

# Integer to string
score = 95
score_text = str(score)

# String to float
price_text = "19.99"
price_number = float(price_text)

# Integer/Float to boolean (0 is False, everything else is True)
zero = bool(0)      # False
positive = bool(5)  # True
```

## Live Exercise: Data Type Detective

We'll work through this together:

```python
# I'll give you some values, you tell me:
# 1. What data type it is
# 2. What happens when we convert it

values = [42, "42", 42.0, "42.0", True, False, "True", 0, "0"]

# For each value, we'll:
# 1. Print the value and its type
# 2. Try converting it to different types
# 3. Discuss what happens and why

# Example for first value:
value = 42
print(f"Value: {value}")
print(f"Type: {type(value)}")
print(f"As string: {str(value)}")
print(f"As float: {float(value)}")
print(f"As boolean: {bool(value)}")
print("---")
```

## Common Mistakes to Avoid

1. **Forgetting quotes around strings:**
   ```python
   # Wrong:
   name = John  # This will cause an error

   # Right:
   name = "John"
   ```

2. **Mixing up data types:**
   ```python
   # This might not work as expected:
   age = "25"
   next_year = age + 1  # Error! Can't add number to string

   # Fix:
   age = 25  # or age = int("25")
   next_year = age + 1
   ```

## Challenge Problems (Optional)

### Challenge 1.1: Age Calculator
Create a program that calculates someone's age in different units:

```python
# Given: birth_year = 1995
# Calculate and print:
# - Age in years
# - Age in months (approximately)
# - Age in days (approximately)
# Use current_year = 2024
```

### Challenge 1.2: Data Type Conversion Chain
```python
# Start with the number 42
# Convert it through this chain:
# int → float → string → back to int
# Print the value and type at each step
# What do you notice?
```

## Lesson Summary

✅ **What we learned:**
- Four basic data types: int, float, str, bool
- How to create and name variables
- Using type() to check data types
- Converting between data types

✅ **Key takeaways:**
- Variables are labeled storage for data
- Data types determine what operations you can perform
- Python is flexible but precise about data types
- Good variable names make code easier to understand

## Next Lesson Preview
In Lesson 2, we'll learn how to perform operations with these data types - adding numbers, combining strings, and making comparisons. We'll build on everything we learned today!

## Self-Check Questions
Before moving on, make sure you can answer:
1. What are the four basic data types in Python?
2. How do you create a variable?
3. What does the type() function do?
4. How do you convert a string "123" to an integer?
5. What happens when you convert the number 0 to a boolean?

Ready for the next lesson? Let's keep building your Python skills!
