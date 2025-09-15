# Lesson 2: Basic Operations

## Learning Objectives
By the end of this lesson, you will:
- Perform mathematical operations with numbers
- Work with string operations and concatenation
- Understand comparison operators
- Use logical operators (and, or, not)
- Practice combining different types of operations

## Mathematical Operations

Since you already know basic math, let's see how Python handles it:

### Arithmetic Operators
```python
# Addition
result = 10 + 5      # 15
age_next_year = 25 + 1   # 26

# Subtraction
difference = 10 - 3   # 7
years_ago = 2024 - 10 # 2014

# Multiplication
area = 5 * 8         # 40
double = 15 * 2      # 30

# Division (always gives a float)
half = 10 / 2        # 5.0
average = (80 + 90 + 85) / 3  # 85.0

# Floor Division (gives whole number part)
whole_part = 17 // 3  # 5

# Modulo (remainder after division)
remainder = 17 % 3    # 2

# Exponentiation (power)
squared = 5 ** 2      # 25
cubed = 3 ** 3        # 27
```

### Order of Operations (PEMDAS)
Python follows the same math rules you know:

```python
# Parentheses first, then Exponents, then Multiplication/Division, then Addition/Subtraction
result = 2 + 3 * 4        # 14 (not 20)
result = (2 + 3) * 4      # 20
result = 2 ** 3 + 1       # 9 (8 + 1)
result = 2 * (3 + 4) ** 2 # 98
```

## String Operations

### String Concatenation (Joining)
```python
first_name = "John"
last_name = "Smith"

# Using + to join strings
full_name = first_name + " " + last_name  # "John Smith"

# Using += to add to existing string
greeting = "Hello"
greeting += " World"  # "Hello World"
greeting += "!"       # "Hello World!"
```

### String Repetition
```python
laugh = "Ha" * 3      # "HaHaHa"
line = "-" * 20       # "--------------------"
cheer = "Go team! " * 2  # "Go team! Go team! "
```

### String Methods (Preview)
```python
message = "Hello World"

# Length of string
length = len(message)     # 11

# Uppercase and lowercase
upper = message.upper()   # "HELLO WORLD"
lower = message.lower()   # "hello world"
```

## Comparison Operators

These create True/False (boolean) results:

```python
# Equal to
is_same = 5 == 5        # True
is_same = 5 == 3        # False

# Not equal to
is_different = 5 != 3   # True
is_different = 5 != 5   # False

# Greater than
is_bigger = 8 > 5       # True
is_bigger = 3 > 7       # False

# Less than
is_smaller = 3 < 7      # True
is_smaller = 8 < 5      # False

# Greater than or equal to
is_big_enough = 5 >= 5  # True
is_big_enough = 7 >= 5  # True

# Less than or equal to
is_small_enough = 3 <= 5 # True
is_small_enough = 3 <= 3 # True
```

### Comparing Strings
```python
# Alphabetical comparison
name1 = "Alice"
name2 = "Bob"
is_first = name1 < name2    # True (Alice comes before Bob)

# Case matters!
"Apple" == "apple"          # False
"Apple".lower() == "apple"  # True
```

## Logical Operators

Combine True/False values:

```python
# AND - both must be True
has_license = True
is_adult = True
can_drive = has_license and is_adult  # True

age = 16
has_license = False
can_drive = (age >= 16) and has_license  # False

# OR - at least one must be True
is_weekend = False
is_holiday = True
can_sleep_in = is_weekend or is_holiday  # True

# NOT - flips True/False
is_raining = True
is_sunny = not is_raining   # False

sunny_day = not False       # True
```

## Quick Practice Exercises

### Exercise 2.1: Math Practice
```python
# Calculate the following and print results:
# 1. The area of a rectangle: length 12, width 8
# 2. The perimeter of the same rectangle
# 3. How many whole groups of 7 can you make from 50?
# 4. What's left over when you divide 50 by 7?

# Your code here:
length = 12
width = 8
area = length * width
perimeter = 2 * (length + width)
groups = 50 // 7
leftover = 50 % 7

print("Area:", area)
print("Perimeter:", perimeter)
print("Groups of 7:", groups)
print("Leftover:", leftover)
```

### Exercise 2.2: String Building
```python
# Create variables for your favorite:
favorite_color = "blue"
favorite_food = "pizza"
favorite_number = 42

# Build a sentence that says:
# "My favorite color is blue, my favorite food is pizza, and my lucky number is 42!"

# Your code here:
sentence = "My favorite color is " + favorite_color + ", my favorite food is " + favorite_food + ", and my lucky number is " + str(favorite_number) + "!"
print(sentence)
```

## Hands-On Coding Exercise

### Exercise 2.3: Simple Calculator
Create a calculator that performs operations on two numbers:

```python
# Get two numbers (we'll use variables for now)
num1 = 15
num2 = 4

print("=== Simple Calculator ===")
print(f"Number 1: {num1}")
print(f"Number 2: {num2}")
print()

# Perform all operations
addition = num1 + num2
subtraction = num1 - num2
multiplication = num1 * num2
division = num1 / num2
floor_division = num1 // num2
remainder = num1 % num2
power = num1 ** num2

print("Results:")
print(f"{num1} + {num2} = {addition}")
print(f"{num1} - {num2} = {subtraction}")
print(f"{num1} * {num2} = {multiplication}")
print(f"{num1} / {num2} = {division}")
print(f"{num1} // {num2} = {floor_division}")
print(f"{num1} % {num2} = {remainder}")
print(f"{num1} ** {num2} = {power}")

# Add some comparisons
print()
print("Comparisons:")
print(f"{num1} > {num2}: {num1 > num2}")
print(f"{num1} < {num2}: {num1 < num2}")
print(f"{num1} == {num2}: {num1 == num2}")
```

## Working with Mixed Data Types

### Converting for Operations
```python
# You can't directly add numbers and strings
age = 25
message = "I am " + str(age) + " years old"  # Convert number to string

# Or use f-strings (we'll learn more about these later)
message = f"I am {age} years old"

# Converting string numbers for math
price1 = "19.99"
price2 = "25.50"
total = float(price1) + float(price2)  # Convert strings to numbers first
```

## Live Exercise: Grade Calculator

We'll work through this together:

```python
# Student's scores
test1 = 85
test2 = 92
test3 = 78
homework = 95
participation = 88

# Calculate different averages
test_average = (test1 + test2 + test3) / 3
all_average = (test1 + test2 + test3 + homework + participation) / 5

# Grade thresholds
a_grade = 90
b_grade = 80
c_grade = 70

# Check what grades they earned
has_a_tests = test_average >= a_grade
has_a_overall = all_average >= a_grade
has_b_overall = all_average >= b_grade
has_c_overall = all_average >= c_grade

print("=== Grade Report ===")
print(f"Test 1: {test1}")
print(f"Test 2: {test2}")
print(f"Test 3: {test3}")
print(f"Homework: {homework}")
print(f"Participation: {participation}")
print()
print(f"Test Average: {test_average:.1f}")
print(f"Overall Average: {all_average:.1f}")
print()
print("Grade Analysis:")
print(f"Has A in tests: {has_a_tests}")
print(f"Has A overall: {has_a_overall}")
print(f"Has B overall: {has_b_overall}")
print(f"Has C overall: {has_c_overall}")
```

## Operator Precedence Summary

From highest to lowest priority:
1. **Parentheses** `()`
2. **Exponentiation** `**`
3. **Multiplication, Division, Floor Division, Modulo** `*`, `/`, `//`, `%`
4. **Addition, Subtraction** `+`, `-`
5. **Comparisons** `==`, `!=`, `<`, `>`, `<=`, `>=`
6. **Logical NOT** `not`
7. **Logical AND** `and`
8. **Logical OR** `or`

## Common Mistakes to Avoid

1. **Integer vs Float Division:**
   ```python
   # In older Python versions, this was 1, now it's 1.5
   result = 3 / 2      # 1.5 (float division)
   result = 3 // 2     # 1 (floor division)
   ```

2. **String and Number Mixing:**
   ```python
   # Wrong:
   age = 25
   message = "I am " + age + " years old"  # Error!

   # Right:
   message = "I am " + str(age) + " years old"
   ```

3. **Boolean vs String:**
   ```python
   is_true = True      # Boolean
   is_true = "True"    # String (not the same!)
   ```

## Challenge Problems (Optional)

### Challenge 2.1: Compound Interest Calculator
```python
# Calculate compound interest
# Formula: A = P(1 + r)^t
# Where: P = principal, r = rate, t = time, A = amount

principal = 1000      # Starting amount
rate = 0.05          # 5% interest rate
time = 3             # 3 years

# Calculate the final amount
# Calculate how much interest was earned
# Print both results
```

### Challenge 2.2: Time Converter
```python
# Convert seconds to hours, minutes, and seconds
total_seconds = 7265

# Figure out how many:
# - Hours (1 hour = 3600 seconds)
# - Minutes (1 minute = 60 seconds)
# - Remaining seconds

# Example: 7265 seconds = 2 hours, 1 minute, 5 seconds
```

## Lesson Summary

✅ **What we learned:**
- Arithmetic operations: +, -, *, /, //, %, **
- String concatenation and repetition
- Comparison operators: ==, !=, <, >, <=, >=
- Logical operators: and, or, not
- Order of operations (PEMDAS)
- Converting between data types for operations

✅ **Key takeaways:**
- Python follows mathematical rules you already know
- Strings and numbers require conversion to work together
- Comparison operations always return True or False
- Logical operators help combine conditions
- Practice makes these operations second nature

## Next Lesson Preview
In Lesson 3, we'll learn how to get input from users and display output in formatted ways. This will make our programs interactive!

## Self-Check Questions
Before moving on, make sure you can answer:
1. What's the difference between `/` and `//`?
2. How do you join two strings together?
3. What does `5 > 3 and 2 < 1` evaluate to?
4. How do you convert the number 42 to a string?
5. What's the order of operations for `2 + 3 * 4`?

Great job! You're building a solid foundation in Python operations.