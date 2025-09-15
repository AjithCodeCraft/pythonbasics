# Lesson 5: Conditional Logic Part 1 - if Statements

## Learning Objectives
By the end of this lesson, you will:
- Understand how conditional logic works in programming
- Master the basic if statement syntax
- Use comparison operators to create conditions
- Combine conditions with logical operators
- Write programs that make decisions based on data

## What is Conditional Logic?

Conditional logic is how programs make decisions. Just like in real life:
- **If** it's raining, take an umbrella
- **If** you're hungry, eat something
- **If** your score is above 90, you get an A

In Python, we use `if` statements to make these decisions.

## Basic if Statement Syntax

```python
# Basic structure
if condition:
    # code to run if condition is True
    print("This runs when condition is True")

# Example
temperature = 75
if temperature > 70:
    print("It's a warm day!")
```

**Important**: Notice the colon `:` after the condition and the indentation (4 spaces) for the code inside the if block.

### Simple Examples
```python
# Check if someone is old enough to vote
age = 18
if age >= 18:
    print("You can vote!")

# Check if password is correct
password = "secret123"
if password == "secret123":
    print("Access granted!")

# Check if number is positive
number = 5
if number > 0:
    print("This is a positive number")
```

## Conditions Using Comparison Operators

You already learned these in Lesson 2, now let's use them in if statements:

```python
score = 85

# Equal to
if score == 100:
    print("Perfect score!")

# Not equal to
if score != 0:
    print("You got some points!")

# Greater than
if score > 90:
    print("Excellent work!")

# Less than
if score < 60:
    print("Needs improvement")

# Greater than or equal to
if score >= 80:
    print("Good job!")

# Less than or equal to
if score <= 100:
    print("Valid score")
```

### Working with Strings
```python
name = "Alice"
favorite_color = "blue"

# String comparisons
if name == "Alice":
    print("Hello Alice!")

if favorite_color != "red":
    print("Your favorite color is not red")

# Alphabetical comparison
if name < "Bob":
    print("Alice comes before Bob alphabetically")

# Case-sensitive comparison
if name == "alice":  # This is False!
    print("This won't print")

if name.lower() == "alice":  # This is True!
    print("Hello alice (case-insensitive)")
```

## Quick Practice Exercises

### Exercise 5.1: Age Categories
```python
# Write if statements to categorize people by age
age = int(input("Enter your age: "))

if age < 13:
    print("You are a child")

if age >= 13:
    print("You are at least a teenager")

if age >= 18:
    print("You are an adult")

if age >= 65:
    print("You are a senior citizen")

# Note: All applicable statements will run!
```

### Exercise 5.2: Grade Checker
```python
# Check different grade thresholds
score = float(input("Enter your test score (0-100): "))

if score >= 90:
    print("A grade - Excellent!")

if score >= 80:
    print("At least a B grade - Good work!")

if score >= 70:
    print("At least a C grade - Passing")

if score < 60:
    print("Below 60 - Needs improvement")

if score > 100:
    print("Score is above maximum!")

if score < 0:
    print("Invalid negative score!")
```

## Using Logical Operators in Conditions

Combine multiple conditions using `and`, `or`, and `not`:

### The `and` Operator
Both conditions must be True:

```python
age = 25
has_license = True

# Both conditions must be True
if age >= 18 and has_license:
    print("You can drive!")

# Another example
score = 85
attendance = 90
if score >= 80 and attendance >= 85:
    print("You qualify for the honor roll!")

# Multiple and conditions
temperature = 75
is_sunny = True
is_weekend = True
if temperature > 70 and is_sunny and is_weekend:
    print("Perfect day for a picnic!")
```

### The `or` Operator
At least one condition must be True:

```python
day = "Saturday"
is_holiday = False

# At least one condition must be True
if day == "Saturday" or day == "Sunday":
    print("It's the weekend!")

if day == "Saturday" or is_holiday:
    print("No work today!")

# Student discount example
age = 20
is_student = True
if age < 18 or is_student:
    print("You qualify for a discount!")
```

### The `not` Operator
Flips True to False and False to True:

```python
is_raining = False
has_homework = True

if not is_raining:
    print("Great day to go outside!")

if not has_homework:
    print("Free evening!")

# Combined with other operators
if not is_raining and temperature > 70:
    print("Perfect weather!")
```

## Hands-On Coding Exercise

### Exercise 5.3: Login System
Create a simple login system that checks username and password:

```python
print("=== Login System ===")

# Correct credentials
correct_username = "admin"
correct_password = "password123"

# Get user input
username = input("Username: ")
password = input("Password: ")

# Check credentials
if username == correct_username and password == correct_password:
    print("✓ Login successful!")
    print("Welcome to the system!")

if username != correct_username:
    print("✗ Incorrect username")

if password != correct_password:
    print("✗ Incorrect password")

if username == correct_username and password != correct_password:
    print("Username is correct, but password is wrong")

if username != correct_username and password == correct_password:
    print("Password is correct, but username is wrong")
```

### Exercise 5.4: Movie Ticket Pricing
```python
print("=== Movie Ticket Pricing ===")

age = int(input("Enter your age: "))
is_student = input("Are you a student? (yes/no): ").lower() == "yes"
is_matinee = input("Is this a matinee show? (yes/no): ").lower() == "yes"
day = input("What day is it? (e.g., Monday, Tuesday): ").capitalize()

base_price = 12.00
price = base_price

print(f"\nBase ticket price: ${price:.2f}")

# Child discount
if age < 12:
    price = 8.00
    print("Child discount applied: $8.00")

# Senior discount
if age >= 65:
    price = 9.00
    print("Senior discount applied: $9.00")

# Student discount (if not already child/senior)
if is_student and age >= 12 and age < 65:
    price = price - 2.00
    print("Student discount applied: $2.00 off")

# Matinee discount
if is_matinee:
    price = price - 3.00
    print("Matinee discount applied: $3.00 off")

# Tuesday discount
if day == "Tuesday":
    price = price - 2.00
    print("Tuesday special: $2.00 off")

# Make sure price doesn't go below $5
if price < 5.00:
    price = 5.00
    print("Minimum price applied: $5.00")

print(f"\nFinal ticket price: ${price:.2f}")
```

## Nested if Statements

You can put if statements inside other if statements:

```python
age = int(input("Enter your age: "))

if age >= 18:
    print("You are an adult.")

    # Nested if - only runs if age >= 18
    if age >= 65:
        print("You are also a senior citizen.")

    if age < 25:
        print("You are a young adult.")

if age < 18:
    print("You are a minor.")

    # Nested if - only runs if age < 18
    if age >= 13:
        print("You are a teenager.")

    if age < 13:
        print("You are a child.")
```

### Practical Nested Example
```python
# Bank account access
account_balance = 1000
pin = input("Enter your PIN: ")
correct_pin = "1234"

if pin == correct_pin:
    print("PIN accepted")

    # Only check balance if PIN is correct
    if account_balance > 0:
        print(f"Your balance is ${account_balance:.2f}")

        # Only offer withdrawal if balance > 0
        if account_balance >= 100:
            print("You have enough for a large withdrawal")

    if account_balance <= 0:
        print("Your account is overdrawn")

if pin != correct_pin:
    print("Incorrect PIN - Access denied")
```

## Live Exercise: Weather Advisory System

We'll work through this together:

```python
print("=== Weather Advisory System ===")
print()

# Get weather conditions
temperature = float(input("Current temperature (°F): "))
humidity = float(input("Humidity percentage: "))
wind_speed = float(input("Wind speed (mph): "))
is_precipitation = input("Is it raining/snowing? (yes/no): ").lower() == "yes"
visibility = float(input("Visibility (miles): "))

print(f"\n=== Weather Analysis ===")
print(f"Temperature: {temperature}°F")
print(f"Humidity: {humidity}%")
print(f"Wind Speed: {wind_speed} mph")
print(f"Precipitation: {'Yes' if is_precipitation else 'No'}")
print(f"Visibility: {visibility} miles")

print(f"\n=== Advisories ===")

# Temperature advisories
if temperature > 95:
    print("🔥 EXTREME HEAT WARNING - Stay indoors, drink water")

if temperature > 85 and humidity > 70:
    print("🌡️ Heat index high - Avoid strenuous outdoor activities")

if temperature < 32:
    print("🧊 FREEZING CONDITIONS - Watch for ice")

if temperature < 10:
    print("❄️ EXTREME COLD WARNING - Frostbite risk")

# Wind advisories
if wind_speed > 50:
    print("💨 HIGH WIND WARNING - Avoid driving high-profile vehicles")

if wind_speed > 25:
    print("🌬️ Wind advisory - Secure loose objects")

# Visibility advisories
if visibility < 0.25:
    print("🌫️ FOG WARNING - Extremely dangerous driving conditions")

if visibility < 1.0:
    print("🌫️ Dense fog - Drive slowly with headlights")

# Precipitation advisories
if is_precipitation and temperature < 35:
    print("🌨️ WINTER WEATHER - Expect ice and snow accumulation")

if is_precipitation and wind_speed > 20:
    print("⛈️ Stormy conditions - Avoid unnecessary travel")

# Comfort index
if temperature >= 70 and temperature <= 80 and humidity < 60 and wind_speed < 15 and not is_precipitation:
    print("☀️ PERFECT WEATHER - Great day to be outside!")

if temperature > 80 or humidity > 70:
    print("😓 Uncomfortable conditions - Stay cool and hydrated")

if temperature < 60:
    print("🧥 Cool weather - Dress warmly")

print("\n=== End of Weather Report ===")
```

## Common Mistakes to Avoid

### 1. Forgetting the Colon
```python
# Wrong:
if age >= 18
    print("Adult")

# Right:
if age >= 18:
    print("Adult")
```

### 2. Wrong Indentation
```python
# Wrong:
if age >= 18:
print("Adult")  # Not indented!

# Right:
if age >= 18:
    print("Adult")  # Properly indented
```

### 3. Using = Instead of ==
```python
# Wrong (this assigns, doesn't compare):
if name = "Alice":

# Right:
if name == "Alice":
```

### 4. Confusing `and` with `or`
```python
age = 20
has_id = True

# Wrong logic:
if age >= 18 or has_id:  # This allows entry with ID even if under 18
    print("Can enter")

# Right logic:
if age >= 18 and has_id:  # Needs both conditions
    print("Can enter")
```

## Challenge Problems (Optional)

### Challenge 5.1: Password Validator
```python
# Create a password validator that checks:
# 1. At least 8 characters long
# 2. Contains at least one number
# 3. Contains at least one uppercase letter
# 4. Contains at least one lowercase letter
# Give specific feedback for each requirement

password = input("Enter a password to validate: ")

# Your code here - use if statements to check each requirement
# Hint: Use len(password), password.isalnum(), etc.
```

### Challenge 5.2: Triangle Type Checker
```python
# Get three sides of a triangle and determine:
# 1. If it's a valid triangle (sum of any two sides > third side)
# 2. If it's equilateral (all sides equal)
# 3. If it's isosceles (two sides equal)
# 4. If it's scalene (no sides equal)
# 5. If it's a right triangle (Pythagorean theorem)

side1 = float(input("Enter first side: "))
side2 = float(input("Enter second side: "))
side3 = float(input("Enter third side: "))

# Your code here
```

## Lesson Summary

✅ **What we learned:**
- Basic if statement syntax with proper indentation
- Using comparison operators in conditions
- Combining conditions with `and`, `or`, `not`
- Nesting if statements for complex logic
- Common mistakes and how to avoid them

✅ **Key takeaways:**
- Every if statement needs a colon `:` at the end
- Code inside if blocks must be indented (4 spaces)
- Use `==` for comparison, not `=`
- `and` requires all conditions to be True
- `or` requires at least one condition to be True
- `not` flips True/False

## Next Lesson Preview
In Lesson 6, we'll learn about `elif` and `else` statements. These will let us create decision trees where only one path is taken, making our logic more efficient and powerful!

## Self-Check Questions
Before moving on, make sure you can answer:
1. What punctuation mark goes at the end of an if statement?
2. How do you indent code inside an if block?
3. What's the difference between `=` and `==`?
4. When does an `and` condition return True?
5. When does an `or` condition return True?

Excellent progress! You've mastered the foundation of conditional logic. In the next lesson, we'll learn how to make our programs even smarter with `elif` and `else`!