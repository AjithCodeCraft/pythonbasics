# Lesson 3: Input and Output

## Learning Objectives
By the end of this lesson, you will:
- Use print() function to display information in various formats
- Get user input with input() function
- Convert user input to different data types
- Format output to look professional
- Create interactive programs

## The print() Function

You've already seen `print()` - it displays information to the user.

### Basic Printing
```python
print("Hello, World!")
print(42)
print(3.14)
print(True)

# Print multiple things at once
print("Name:", "Alice", "Age:", 25)
print("Score:", 95, "Grade:", "A")
```

### Print Function Parameters
```python
# Default separator is a space
print("apple", "banana", "cherry")  # apple banana cherry

# Change the separator
print("apple", "banana", "cherry", sep=", ")    # apple, banana, cherry
print("2024", "12", "25", sep="-")              # 2024-12-25
print("Hello", "World", sep="")                  # HelloWorld

# Change what comes at the end (default is newline)
print("Loading", end="")
print("...", end="")
print("Done!")  # All on same line: Loading...Done!

# Print to create patterns
print("*" * 20)  # ********************
print("=" * 30)  # ==============================
```

### Formatted Strings (f-strings)
This is the modern way to include variables in strings:

```python
name = "Alice"
age = 25
height = 5.6

# Old way (still works but not preferred)
print("My name is " + name + " and I am " + str(age) + " years old")

# New way (f-strings) - much easier!
print(f"My name is {name} and I am {age} years old")
print(f"Height: {height} feet")
print(f"Next year I'll be {age + 1}")

# Formatting numbers in f-strings
price = 19.99567
print(f"Price: ${price:.2f}")      # Price: $20.00 (2 decimal places)

percentage = 0.756
print(f"Success rate: {percentage:.1%}")  # Success rate: 75.6%
```

## The input() Function

Use `input()` to get information from the user:

### Basic Input
```python
# Get user's name
name = input("What's your name? ")
print(f"Hello, {name}!")

# Get user's age
age_text = input("How old are you? ")
print(f"You entered: {age_text}")
print(f"Type of input: {type(age_text)}")  # Always string!
```

### Converting Input to Numbers
`input()` always returns a string, so convert when needed:

```python
# Convert to integer
age_text = input("Enter your age: ")
age = int(age_text)
next_year = age + 1
print(f"Next year you'll be {next_year}")

# Convert to float
height_text = input("Enter your height in feet: ")
height = float(height_text)
height_cm = height * 30.48
print(f"That's {height_cm:.1f} cm")

# Do it all in one line
score = int(input("Enter your test score: "))
print(f"Your score: {score}")
```

## Quick Practice Exercises

### Exercise 3.1: Personal Greeting
```python
# Get user's information and create a personalized greeting
first_name = input("Enter your first name: ")
last_name = input("Enter your last name: ")
age = int(input("Enter your age: "))

print(f"Hello, {first_name} {last_name}!")
print(f"You are {age} years old.")
print(f"In 10 years, you'll be {age + 10}.")
```

### Exercise 3.2: Simple Math with User Input
```python
# Get two numbers and show all operations
print("=== Simple Calculator ===")
num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))

print(f"\nResults:")
print(f"{num1} + {num2} = {num1 + num2}")
print(f"{num1} - {num2} = {num1 - num2}")
print(f"{num1} * {num2} = {num1 * num2}")
if num2 != 0:
    print(f"{num1} / {num2} = {num1 / num2:.2f}")
else:
    print("Cannot divide by zero!")
```

## Hands-On Coding Exercise

### Exercise 3.3: Restaurant Order Calculator
Create a program that calculates a restaurant bill:

```python
print("=== Restaurant Order Calculator ===")
print()

# Get order information
customer_name = input("Customer name: ")
main_dish = input("Main dish: ")
main_price = float(input("Main dish price: $"))

side_dish = input("Side dish: ")
side_price = float(input("Side dish price: $"))

drink = input("Drink: ")
drink_price = float(input("Drink price: $"))

# Calculate totals
subtotal = main_price + side_price + drink_price
tax_rate = 0.08  # 8% tax
tax = subtotal * tax_rate
tip_rate = 0.15  # 15% tip
tip = subtotal * tip_rate
total = subtotal + tax + tip

# Display receipt
print()
print("=" * 30)
print(f"RECEIPT FOR {customer_name.upper()}")
print("=" * 30)
print(f"{main_dish:<20} ${main_price:>6.2f}")
print(f"{side_dish:<20} ${side_price:>6.2f}")
print(f"{drink:<20} ${drink_price:>6.2f}")
print("-" * 30)
print(f"{'Subtotal':<20} ${subtotal:>6.2f}")
print(f"{'Tax (8%)':<20} ${tax:>6.2f}")
print(f"{'Tip (15%)':<20} ${tip:>6.2f}")
print("=" * 30)
print(f"{'TOTAL':<20} ${total:>6.2f}")
print("=" * 30)
print("Thank you for dining with us!")
```

## Formatting Output

### String Formatting Options
```python
name = "Alice"
score = 95.7

# Left, center, right alignment
print(f"{name:<10}|")    # Alice     |
print(f"{name:>10}|")    # |     Alice
print(f"{name:^10}|")    # |  Alice   |

# Number formatting
print(f"{score:.0f}")    # 96 (no decimals)
print(f"{score:.1f}")    # 95.7 (1 decimal)
print(f"{score:.2f}")    # 95.70 (2 decimals)

# Padding with zeros
number = 42
print(f"{number:04d}")   # 0042 (pad to 4 digits)
```

### Creating Tables
```python
# Simple table
print(f"{'Name':<10} {'Age':<5} {'Score':<7}")
print("-" * 22)
print(f"{'Alice':<10} {25:<5} {95.5:<7}")
print(f"{'Bob':<10} {30:<5} {87.2:<7}")
print(f"{'Charlie':<10} {22:<5} {92.0:<7}")
```

## Live Exercise: Grade Book Entry

We'll work through this together:

```python
print("=== Student Grade Entry System ===")
print()

# Get student information
student_name = input("Student name: ")
student_id = input("Student ID: ")

print(f"\nEntering grades for {student_name} (ID: {student_id})")

# Get grades for different assignments
test1 = float(input("Test 1 score (0-100): "))
test2 = float(input("Test 2 score (0-100): "))
test3 = float(input("Test 3 score (0-100): "))
homework = float(input("Homework average (0-100): "))
participation = float(input("Participation score (0-100): "))

# Calculate weighted average
# Tests: 60%, Homework: 25%, Participation: 15%
test_average = (test1 + test2 + test3) / 3
final_grade = (test_average * 0.6) + (homework * 0.25) + (participation * 0.15)

# Determine letter grade
if final_grade >= 90:
    letter_grade = "A"
elif final_grade >= 80:
    letter_grade = "B"
elif final_grade >= 70:
    letter_grade = "C"
elif final_grade >= 60:
    letter_grade = "D"
else:
    letter_grade = "F"

# Display report
print()
print("=" * 40)
print(f"GRADE REPORT FOR {student_name.upper()}")
print(f"Student ID: {student_id}")
print("=" * 40)
print(f"Test 1:        {test1:>6.1f}")
print(f"Test 2:        {test2:>6.1f}")
print(f"Test 3:        {test3:>6.1f}")
print(f"Test Average:  {test_average:>6.1f}")
print(f"Homework:      {homework:>6.1f}")
print(f"Participation: {participation:>6.1f}")
print("-" * 40)
print(f"Final Grade:   {final_grade:>6.1f} ({letter_grade})")
print("=" * 40)
```

## Error Handling with Input

### Common Input Errors
```python
# What happens when user enters wrong data type?
try:
    age = int(input("Enter your age: "))
    print(f"You are {age} years old")
except ValueError:
    print("Please enter a valid number!")

# We'll learn more about error handling later
```

### Input Validation (Preview)
```python
# Simple validation
while True:
    age_input = input("Enter your age (0-120): ")
    try:
        age = int(age_input)
        if 0 <= age <= 120:
            break
        else:
            print("Age must be between 0 and 120")
    except ValueError:
        print("Please enter a valid number")

print(f"Your age: {age}")
```

## Common Mistakes to Avoid

1. **Forgetting to Convert Input:**
   ```python
   # Wrong:
   age = input("Age: ")
   next_year = age + 1  # Error! Can't add to string

   # Right:
   age = int(input("Age: "))
   next_year = age + 1
   ```

2. **Not Handling Invalid Input:**
   ```python
   # User enters "abc" when you expect a number
   # Program will crash without error handling
   ```

3. **Confusing Print Parameters:**
   ```python
   print("Hello", "World", sep=", ", end="!\n")
   # Remember: sep goes between items, end goes at the very end
   ```

## Challenge Problems (Optional)

### Challenge 3.1: BMI Calculator
```python
# Create a BMI calculator that:
# 1. Gets user's weight in pounds
# 2. Gets user's height in feet and inches
# 3. Converts to metric (kg and meters)
# 4. Calculates BMI = weight(kg) / height(m)²
# 5. Displays result with interpretation

# Conversion factors:
# 1 pound = 0.453592 kg
# 1 foot = 12 inches
# 1 inch = 0.0254 meters
```

### Challenge 3.2: Time Zone Converter
```python
# Create a program that:
# 1. Gets current time in one city (24-hour format)
# 2. Gets time difference between cities
# 3. Calculates and displays time in other city
# 4. Handles going past midnight (0-23 hours)

# Example: If it's 15:30 in New York (-5 from GMT)
# What time is it in London (0 GMT)?
```

## Lesson Summary

✅ **What we learned:**
- Using print() for formatted output
- Getting user input with input()
- Converting string input to numbers
- F-string formatting for clean output
- Creating interactive programs

✅ **Key takeaways:**
- input() always returns a string - convert when needed
- F-strings make formatting easy and readable
- Good formatting makes programs look professional
- Always consider what happens with bad input
- Interactive programs are more engaging

## Next Lesson Preview
In Lesson 4, we'll combine everything we've learned so far to work with data in more complex ways. Then we'll start our deep dive into conditional logic!

## Self-Check Questions
Before moving on, make sure you can answer:
1. What data type does input() always return?
2. How do you include a variable in an f-string?
3. How do you convert a string to an integer?
4. What's the difference between `sep` and `end` in print()?
5. How do you format a number to show 2 decimal places?

Excellent progress! You can now create programs that interact with users. In the next lesson, we'll start making decisions in our code!