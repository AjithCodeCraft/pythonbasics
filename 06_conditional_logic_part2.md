# Lesson 6: Conditional Logic Part 2 - elif and else

## Learning Objectives
By the end of this lesson, you will:
- Use `else` statements for alternative actions
- Master `elif` (else if) for multiple conditions
- Create decision trees that take only one path
- Understand when to use if vs elif vs else
- Build more efficient conditional logic

## The Problem with Multiple if Statements

In the previous lesson, we used multiple `if` statements:

```python
score = 85

if score >= 90:
    print("A grade")
if score >= 80:
    print("B grade")  # This ALSO prints for score = 85!
if score >= 70:
    print("C grade")  # This ALSO prints for score = 85!
```

**Problem**: All applicable conditions run! For score = 85, you get "B grade" AND "C grade" printed.

## The `else` Statement

`else` runs when the `if` condition is False:

```python
age = 16

if age >= 18:
    print("You can vote")
else:
    print("You cannot vote yet")

# Only ONE of these messages will print
```

### More `else` Examples
```python
# Password check
password = input("Enter password: ")

if password == "secret123":
    print("Access granted!")
else:
    print("Access denied!")

# Temperature check
temperature = 65

if temperature > 70:
    print("It's warm today")
else:
    print("It's cool today")

# Even or odd
number = 7

if number % 2 == 0:
    print(f"{number} is even")
else:
    print(f"{number} is odd")
```

## The `elif` Statement

`elif` (else if) lets you check multiple conditions, but only the first True condition runs:

```python
score = 85

if score >= 90:
    print("A grade")
elif score >= 80:
    print("B grade")      # This prints for score = 85
elif score >= 70:
    print("C grade")      # This does NOT print
elif score >= 60:
    print("D grade")
else:
    print("F grade")

# Only ONE message prints!
```

### How elif Works
1. Check the first `if` condition
2. If False, check the first `elif` condition
3. If False, check the next `elif` condition
4. Continue until one is True, then STOP
5. If none are True, run the `else` (if present)

## Quick Practice Exercises

### Exercise 6.1: Age Categories (Corrected)
```python
# Using elif to fix the age category problem
age = int(input("Enter your age: "))

if age < 13:
    print("You are a child")
elif age < 18:
    print("You are a teenager")
elif age < 65:
    print("You are an adult")
else:
    print("You are a senior citizen")

# Only ONE category will print!
```

### Exercise 6.2: Grade Letter Assignment
```python
# Convert numeric grade to letter grade
score = float(input("Enter your grade (0-100): "))

if score >= 90:
    letter = "A"
elif score >= 80:
    letter = "B"
elif score >= 70:
    letter = "C"
elif score >= 60:
    letter = "D"
else:
    letter = "F"

print(f"Your grade: {score} = {letter}")
```

## When to Use if vs elif vs else

### Use Multiple `if` Statements When:
- You want ALL applicable conditions to execute
- Conditions are independent of each other

```python
# Health warnings - all applicable warnings should show
temperature = 95
humidity = 80

if temperature > 90:
    print("Heat warning!")
if humidity > 75:
    print("High humidity warning!")
if temperature > 85 and humidity > 70:
    print("Heat index warning!")
# All three might print!
```

### Use `if/elif/else` When:
- Only one action should happen
- Conditions are mutually exclusive
- You want to categorize something

```python
# Day type - only one category applies
day = input("What day is it? ").lower()

if day in ["saturday", "sunday"]:
    print("It's the weekend!")
elif day in ["monday", "tuesday", "wednesday", "thursday", "friday"]:
    print("It's a weekday")
else:
    print("Invalid day entered")
```

## Complex Conditions in elif

You can use complex conditions with `elif`:

```python
age = 25
has_license = True
has_car = False

if age < 16:
    print("Too young to drive")
elif age >= 16 and not has_license:
    print("Need to get a license first")
elif age >= 16 and has_license and not has_car:
    print("Can drive but need a car")
elif age >= 16 and has_license and has_car:
    print("Ready to drive!")
else:
    print("Unexpected situation")
```

## Hands-On Coding Exercise

### Exercise 6.3: BMI Calculator with Categories
```python
print("=== BMI Calculator ===")

# Get user information
weight = float(input("Enter your weight in pounds: "))
height_feet = int(input("Enter your height (feet): "))
height_inches = int(input("Enter additional inches: "))

# Convert to metric
weight_kg = weight * 0.453592
height_total_inches = (height_feet * 12) + height_inches
height_meters = height_total_inches * 0.0254

# Calculate BMI
bmi = weight_kg / (height_meters ** 2)

print(f"\nYour BMI: {bmi:.1f}")

# Categorize BMI
if bmi < 18.5:
    category = "Underweight"
    advice = "Consider consulting a healthcare provider about healthy weight gain"
elif bmi < 25:
    category = "Normal weight"
    advice = "Great! Maintain your current lifestyle"
elif bmi < 30:
    category = "Overweight"
    advice = "Consider a balanced diet and regular exercise"
else:
    category = "Obese"
    advice = "Consult a healthcare provider for a personalized plan"

print(f"Category: {category}")
print(f"Advice: {advice}")

# Additional specific advice
if bmi < 16:
    print("⚠️ Severely underweight - seek medical attention")
elif bmi > 40:
    print("⚠️ Severely obese - seek medical attention")
elif 18.5 <= bmi <= 24.9:
    print("✅ Healthy BMI range")
```

### Exercise 6.4: Shipping Cost Calculator
```python
print("=== Shipping Cost Calculator ===")

# Get package information
weight = float(input("Package weight (lbs): "))
distance = float(input("Shipping distance (miles): "))
is_express = input("Express shipping? (yes/no): ").lower() == "yes"
is_fragile = input("Fragile item? (yes/no): ").lower() == "yes"

# Base cost calculation
if weight <= 1:
    base_cost = 5.00
elif weight <= 5:
    base_cost = 10.00
elif weight <= 20:
    base_cost = 20.00
else:
    base_cost = 35.00

print(f"\nBase cost: ${base_cost:.2f}")

# Distance modifier
if distance <= 100:
    distance_multiplier = 1.0
elif distance <= 500:
    distance_multiplier = 1.5
else:
    distance_multiplier = 2.0

cost_with_distance = base_cost * distance_multiplier
print(f"With distance ({distance} miles): ${cost_with_distance:.2f}")

# Express shipping
if is_express:
    express_cost = cost_with_distance * 0.5  # 50% extra
    total_cost = cost_with_distance + express_cost
    print(f"Express shipping fee: ${express_cost:.2f}")
else:
    total_cost = cost_with_distance

# Fragile handling
if is_fragile:
    fragile_fee = 10.00
    total_cost += fragile_fee
    print(f"Fragile handling fee: ${fragile_fee:.2f}")

print(f"\nTOTAL SHIPPING COST: ${total_cost:.2f}")

# Delivery time estimate
if is_express:
    if distance <= 500:
        delivery_days = "1-2"
    else:
        delivery_days = "2-3"
else:
    if distance <= 100:
        delivery_days = "2-3"
    elif distance <= 500:
        delivery_days = "3-5"
    else:
        delivery_days = "5-7"

print(f"Estimated delivery: {delivery_days} business days")
```

## Nested elif Structures

You can nest if/elif/else inside other conditions:

```python
age = int(input("Enter age: "))
income = float(input("Enter annual income: "))

if age >= 18:
    print("Adult")

    if income < 20000:
        tax_rate = 0.0
        print("No taxes owed")
    elif income < 50000:
        tax_rate = 0.15
        print("15% tax bracket")
    elif income < 100000:
        tax_rate = 0.22
        print("22% tax bracket")
    else:
        tax_rate = 0.35
        print("35% tax bracket")

    taxes_owed = income * tax_rate
    print(f"Estimated taxes: ${taxes_owed:,.2f}")

else:
    print("Minor - no taxes")
```

## Live Exercise: Restaurant Recommendation System

We'll work through this together:

```python
print("=== Restaurant Recommendation System ===")
print()

# Get preferences
budget = float(input("What's your budget per person? $"))
cuisine = input("Preferred cuisine (italian/chinese/mexican/american): ").lower()
group_size = int(input("How many people in your group? "))
is_vegetarian = input("Any vegetarians in group? (yes/no): ").lower() == "yes"
occasion = input("What's the occasion? (date/family/business/casual): ").lower()

print(f"\n=== Finding restaurants for your {occasion} ===")

# Budget categories
if budget < 15:
    budget_category = "budget"
elif budget < 30:
    budget_category = "mid-range"
else:
    budget_category = "upscale"

print(f"Budget category: {budget_category}")

# Restaurant recommendations based on cuisine and budget
if cuisine == "italian":
    if budget_category == "budget":
        restaurant = "Tony's Pizza Palace"
        description = "Great pizza and pasta, family-friendly"
    elif budget_category == "mid-range":
        restaurant = "Bella Vista"
        description = "Authentic Italian with romantic atmosphere"
    else:
        restaurant = "Il Magnifico"
        description = "Fine dining Italian with extensive wine list"

elif cuisine == "chinese":
    if budget_category == "budget":
        restaurant = "Golden Dragon"
        description = "Traditional Chinese, large portions"
    elif budget_category == "mid-range":
        restaurant = "Bamboo Garden"
        description = "Modern Chinese cuisine, great for groups"
    else:
        restaurant = "Imperial Palace"
        description = "Upscale Chinese with private dining rooms"

elif cuisine == "mexican":
    if budget_category == "budget":
        restaurant = "Casa Tacos"
        description = "Authentic street tacos, casual atmosphere"
    elif budget_category == "mid-range":
        restaurant = "Fiesta Grill"
        description = "Full-service Mexican with margaritas"
    else:
        restaurant = "Hacienda Real"
        description = "Fine Mexican dining with tableside guacamole"

elif cuisine == "american":
    if budget_category == "budget":
        restaurant = "Main Street Diner"
        description = "Classic American comfort food"
    elif budget_category == "mid-range":
        restaurant = "The Grill House"
        description = "Steaks and burgers, sports bar atmosphere"
    else:
        restaurant = "Metropolitan Bistro"
        description = "Contemporary American fine dining"

else:
    restaurant = "The Food Court"
    description = "Multiple cuisine options available"

print(f"\nRecommended: {restaurant}")
print(f"Description: {description}")

# Additional considerations
if group_size > 8:
    print("⚠️ Recommendation: Call ahead for large group seating")

if is_vegetarian:
    print("🥗 Note: Ask about vegetarian options when making reservation")

if occasion == "date":
    print("💕 Tip: Request a quiet, romantic table")
elif occasion == "business":
    print("💼 Tip: Request a table suitable for conversation")
elif occasion == "family":
    print("👨‍👩‍👧‍👦 Tip: Ask about kids menu and high chairs")

# Final budget check
estimated_total = budget * group_size
if estimated_total > 200:
    print(f"💰 Total estimated cost: ${estimated_total:.2f}")
    print("Consider splitting the bill or adjusting group size")

print(f"\nEnjoy your {occasion} at {restaurant}!")
```

## Common Patterns and Best Practices

### 1. Range Checking Pattern
```python
# Good pattern for ranges
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:  # Automatically means 80-89
    grade = "B"
elif score >= 70:  # Automatically means 70-79
    grade = "C"
elif score >= 60:  # Automatically means 60-69
    grade = "D"
else:              # Automatically means below 60
    grade = "F"
```

### 2. Early Return Pattern
```python
def check_eligibility(age, income):
    if age < 18:
        return "Too young"

    if income < 30000:
        return "Income too low"

    if age > 65:
        return "Senior discount available"

    return "Eligible for standard rate"
```

### 3. Input Validation Pattern
```python
response = input("Continue? (yes/no): ").lower().strip()

if response in ["yes", "y", "true", "1"]:
    print("Continuing...")
elif response in ["no", "n", "false", "0"]:
    print("Stopping...")
else:
    print("Invalid response")
```

## Common Mistakes to Avoid

### 1. Wrong Order of Conditions
```python
# Wrong - will never reach the specific conditions
score = 85

if score >= 60:    # This catches everything >= 60!
    print("D or better")
elif score >= 70:  # Never reached!
    print("C or better")

# Right - start with most specific
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
elif score >= 60:
    print("D")
```

### 2. Forgetting the Final else
```python
# Risky - what if none of the conditions are met?
grade_input = input("Enter grade: ")

if grade_input == "A":
    points = 4.0
elif grade_input == "B":
    points = 3.0
elif grade_input == "C":
    points = 2.0
# What if they enter "X"? points won't be defined!

# Better - always have a fallback
else:
    print("Invalid grade")
    points = 0.0
```

## Challenge Problems (Optional)

### Challenge 6.1: Tax Calculator
```python
# Create a progressive tax calculator:
# Income $0-$10,000: 0% tax
# Income $10,001-$40,000: 12% tax
# Income $40,001-$85,000: 22% tax
# Income $85,001+: 35% tax
# Calculate taxes owed and after-tax income

income = float(input("Enter annual income: $"))

# Calculate progressive tax
# Hint: You might need to calculate tax for each bracket separately
```

### Challenge 6.2: Student Housing Assignment
```python
# Assign students to dorms based on:
# - Grade level (freshman, sophomore, junior, senior)
# - GPA (< 2.0, 2.0-3.0, 3.0-3.5, > 3.5)
# - Special requests (quiet, social, study-focused)
# Create a decision tree that assigns appropriate housing

grade_level = input("Grade level: ").lower()
gpa = float(input("GPA: "))
preference = input("Housing preference (quiet/social/study): ").lower()

# Your decision tree here
```

## Lesson Summary

✅ **What we learned:**
- `else` statement for alternative actions
- `elif` for multiple mutually exclusive conditions
- When to use if vs elif vs else
- Complex conditions in elif statements
- Common patterns and best practices

✅ **Key takeaways:**
- `elif` and `else` create decision trees where only one path executes
- Order matters in elif chains - most specific conditions first
- Always consider having a final `else` as a safety net
- Use multiple `if` when all applicable conditions should run
- Use `if/elif/else` when only one condition should execute

## Next Lesson Preview
In Lesson 7, we'll master advanced conditional logic patterns, learn about the `match` statement (Python's newest feature), and practice complex decision-making scenarios. You'll become a conditional logic expert!

## Self-Check Questions
Before moving on, make sure you can answer:
1. What's the difference between multiple `if` statements and `if/elif/else`?
2. In an `elif` chain, what happens after the first True condition is found?
3. Why does order matter in `elif` chains?
4. When should you use a final `else` statement?
5. How do you check if a value is in a specific range using elif?

Outstanding work! You now understand the core of conditional logic. In the next lesson, we'll polish your skills with advanced patterns and real-world applications!