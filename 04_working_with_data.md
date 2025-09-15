# Lesson 4: Working with Data

## Learning Objectives
By the end of this lesson, you will:
- Combine multiple data types in meaningful ways
- Build more complex programs using what you've learned
- Practice data validation and conversion
- Create programs that solve real-world problems
- Prepare for conditional logic (next lesson)

## Bringing It All Together

Now that you know data types, operations, and input/output, let's create more sophisticated programs.

### Working with Mixed Data
```python
# Personal information system
name = input("Full name: ")
birth_year = int(input("Birth year: "))
height_feet = int(input("Height (feet): "))
height_inches = int(input("Additional inches: "))
favorite_color = input("Favorite color: ")
is_student = input("Are you a student? (yes/no): ").lower() == "yes"

# Calculations
current_year = 2024
age = current_year - birth_year
total_height_inches = (height_feet * 12) + height_inches
height_cm = total_height_inches * 2.54

# Display information
print(f"\n=== Personal Profile ===")
print(f"Name: {name}")
print(f"Age: {age} years old")
print(f"Height: {height_feet}'{height_inches}\" ({height_cm:.1f} cm)")
print(f"Favorite color: {favorite_color}")
print(f"Student status: {is_student}")
```

### Data Validation Examples
```python
# Temperature converter with validation
print("=== Temperature Converter ===")

temp_input = input("Enter temperature: ")
scale = input("Is this Celsius or Fahrenheit? (C/F): ").upper()

# Convert input to number
try:
    temperature = float(temp_input)
except ValueError:
    print("Invalid temperature entered!")
    exit()

# Validate scale
if scale not in ["C", "F"]:
    print("Please enter C for Celsius or F for Fahrenheit")
    exit()

# Convert temperature
if scale == "C":
    fahrenheit = (temperature * 9/5) + 32
    print(f"{temperature}°C = {fahrenheit:.1f}°F")
else:
    celsius = (temperature - 32) * 5/9
    print(f"{temperature}°F = {celsius:.1f}°C")
```

## Quick Practice Exercises

### Exercise 4.1: Shopping List Calculator
```python
# Create a shopping calculator
print("=== Shopping List Calculator ===")

item1 = input("Item 1 name: ")
price1 = float(input("Item 1 price: $"))
quantity1 = int(input("Item 1 quantity: "))

item2 = input("Item 2 name: ")
price2 = float(input("Item 2 price: $"))
quantity2 = int(input("Item 2 quantity: "))

item3 = input("Item 3 name: ")
price3 = float(input("Item 3 price: $"))
quantity3 = int(input("Item 3 quantity: "))

# Calculate totals
total1 = price1 * quantity1
total2 = price2 * quantity2
total3 = price3 * quantity3
subtotal = total1 + total2 + total3

# Apply discount if over $50
discount_rate = 0.10 if subtotal > 50 else 0
discount = subtotal * discount_rate
final_total = subtotal - discount

# Display receipt
print(f"\n=== SHOPPING RECEIPT ===")
print(f"{item1:<15} ${price1:>6.2f} x {quantity1} = ${total1:>7.2f}")
print(f"{item2:<15} ${price2:>6.2f} x {quantity2} = ${total2:>7.2f}")
print(f"{item3:<15} ${price3:>6.2f} x {quantity3} = ${total3:>7.2f}")
print("-" * 40)
print(f"{'Subtotal':<30} ${subtotal:>7.2f}")
if discount > 0:
    print(f"{'Discount (10%)':<30} -${discount:>6.2f}")
print("=" * 40)
print(f"{'TOTAL':<30} ${final_total:>7.2f}")
```

### Exercise 4.2: Travel Time Calculator
```python
# Calculate travel time and costs
print("=== Travel Planner ===")

destination = input("Where are you traveling to? ")
distance = float(input("Distance in miles: "))
speed = float(input("Average speed (mph): "))
mpg = float(input("Car's miles per gallon: "))
gas_price = float(input("Price per gallon: $"))

# Calculations
travel_time_hours = distance / speed
travel_time_minutes = travel_time_hours * 60
gallons_needed = distance / mpg
gas_cost = gallons_needed * gas_price

# Convert time to hours and minutes
hours = int(travel_time_hours)
minutes = int((travel_time_hours - hours) * 60)

print(f"\n=== Trip to {destination} ===")
print(f"Distance: {distance} miles")
print(f"Travel time: {hours}h {minutes}m")
print(f"Gas needed: {gallons_needed:.1f} gallons")
print(f"Gas cost: ${gas_cost:.2f}")
print(f"Cost per mile: ${gas_cost/distance:.3f}")
```

## Hands-On Coding Exercise

### Exercise 4.3: Student Grade Analyzer
Create a comprehensive grade analysis program:

```python
print("=== Student Grade Analyzer ===")
print()

# Get student information
student_name = input("Student name: ")
class_name = input("Class name: ")
semester = input("Semester: ")

print(f"\nEntering grades for {student_name} in {class_name}")
print("Enter all scores as percentages (0-100)")

# Get assignment scores
quiz1 = float(input("Quiz 1 score: "))
quiz2 = float(input("Quiz 2 score: "))
quiz3 = float(input("Quiz 3 score: "))

midterm = float(input("Midterm exam score: "))
final = float(input("Final exam score: "))

project1 = float(input("Project 1 score: "))
project2 = float(input("Project 2 score: "))

participation = float(input("Participation score: "))

# Calculate category averages
quiz_average = (quiz1 + quiz2 + quiz3) / 3
exam_average = (midterm + final) / 2
project_average = (project1 + project2) / 2

# Calculate weighted final grade
# Quizzes: 20%, Exams: 40%, Projects: 30%, Participation: 10%
final_grade = (quiz_average * 0.20) + (exam_average * 0.40) + (project_average * 0.30) + (participation * 0.10)

# Determine letter grade
if final_grade >= 97:
    letter = "A+"
elif final_grade >= 93:
    letter = "A"
elif final_grade >= 90:
    letter = "A-"
elif final_grade >= 87:
    letter = "B+"
elif final_grade >= 83:
    letter = "B"
elif final_grade >= 80:
    letter = "B-"
elif final_grade >= 77:
    letter = "C+"
elif final_grade >= 73:
    letter = "C"
elif final_grade >= 70:
    letter = "C-"
elif final_grade >= 67:
    letter = "D+"
elif final_grade >= 63:
    letter = "D"
elif final_grade >= 60:
    letter = "D-"
else:
    letter = "F"

# Calculate how close to next grade level
if letter == "F":
    points_needed = 60 - final_grade
    next_grade = "D-"
elif letter.startswith("D"):
    points_needed = 70 - final_grade
    next_grade = "C-"
elif letter.startswith("C"):
    points_needed = 80 - final_grade
    next_grade = "B-"
elif letter.startswith("B"):
    points_needed = 90 - final_grade
    next_grade = "A-"
else:
    points_needed = 0
    next_grade = "Perfect!"

# Display comprehensive report
print()
print("=" * 50)
print(f"GRADE REPORT FOR {student_name.upper()}")
print(f"Class: {class_name} | Semester: {semester}")
print("=" * 50)

print("\nINDIVIDUAL SCORES:")
print(f"Quiz 1:         {quiz1:>6.1f}%")
print(f"Quiz 2:         {quiz2:>6.1f}%")
print(f"Quiz 3:         {quiz3:>6.1f}%")
print(f"Midterm Exam:   {midterm:>6.1f}%")
print(f"Final Exam:     {final:>6.1f}%")
print(f"Project 1:      {project1:>6.1f}%")
print(f"Project 2:      {project2:>6.1f}%")
print(f"Participation:  {participation:>6.1f}%")

print("\nCATEGORY AVERAGES:")
print(f"Quizzes (20%):    {quiz_average:>6.1f}%")
print(f"Exams (40%):      {exam_average:>6.1f}%")
print(f"Projects (30%):   {project_average:>6.1f}%")
print(f"Participation (10%): {participation:>6.1f}%")

print("-" * 50)
print(f"FINAL GRADE:      {final_grade:>6.1f}% ({letter})")
print("-" * 50)

if points_needed > 0:
    print(f"Need {points_needed:.1f} more points for {next_grade}")
else:
    print("Excellent work!")

print("=" * 50)
```

## Working with String Data

### Text Processing Examples
```python
# Analyzing user input
full_name = input("Enter your full name: ")

# String analysis
name_length = len(full_name)
name_upper = full_name.upper()
name_lower = full_name.lower()
name_title = full_name.title()
word_count = len(full_name.split())

# First and last name extraction
name_parts = full_name.split()
first_name = name_parts[0] if name_parts else ""
last_name = name_parts[-1] if len(name_parts) > 1 else ""

print(f"\n=== Name Analysis ===")
print(f"Original: '{full_name}'")
print(f"Length: {name_length} characters")
print(f"Words: {word_count}")
print(f"First name: {first_name}")
print(f"Last name: {last_name}")
print(f"Uppercase: {name_upper}")
print(f"Title case: {name_title}")
```

## Live Exercise: Personal Finance Calculator

We'll work through this together:

```python
print("=== Personal Finance Calculator ===")
print()

# Get financial information
name = input("Your name: ")
monthly_income = float(input("Monthly gross income: $"))
tax_rate = float(input("Tax rate (as decimal, e.g., 0.22): "))

print("\nMonthly Expenses:")
rent = float(input("Rent/Mortgage: $"))
utilities = float(input("Utilities: $"))
food = float(input("Food: $"))
transportation = float(input("Transportation: $"))
entertainment = float(input("Entertainment: $"))
other = float(input("Other expenses: $"))

print("\nSavings Goals:")
emergency_goal = float(input("Emergency fund goal: $"))
current_savings = float(input("Current savings: $"))

# Calculations
monthly_tax = monthly_income * tax_rate
net_income = monthly_income - monthly_tax
total_expenses = rent + utilities + food + transportation + entertainment + other
monthly_surplus = net_income - total_expenses
annual_surplus = monthly_surplus * 12

# Savings analysis
emergency_needed = emergency_goal - current_savings
months_to_goal = emergency_needed / monthly_surplus if monthly_surplus > 0 else float('inf')

# Category percentages
rent_percent = (rent / net_income) * 100
food_percent = (food / net_income) * 100
savings_percent = (monthly_surplus / net_income) * 100 if monthly_surplus > 0 else 0

# Financial health indicators
is_healthy_rent = rent_percent <= 30
is_healthy_savings = savings_percent >= 20
is_surplus = monthly_surplus > 0

# Display report
print()
print("=" * 50)
print(f"FINANCIAL REPORT FOR {name.upper()}")
print("=" * 50)

print(f"\nINCOME:")
print(f"Gross monthly income:    ${monthly_income:>10,.2f}")
print(f"Taxes ({tax_rate:.1%}):            -${monthly_tax:>10,.2f}")
print(f"Net monthly income:      ${net_income:>10,.2f}")

print(f"\nEXPENSES:")
print(f"Rent/Mortgage:           ${rent:>10,.2f} ({rent_percent:.1f}%)")
print(f"Utilities:               ${utilities:>10,.2f}")
print(f"Food:                    ${food:>10,.2f} ({food_percent:.1f}%)")
print(f"Transportation:          ${transportation:>10,.2f}")
print(f"Entertainment:           ${entertainment:>10,.2f}")
print(f"Other:                   ${other:>10,.2f}")
print(f"Total expenses:          ${total_expenses:>10,.2f}")

print(f"\nCASH FLOW:")
if monthly_surplus > 0:
    print(f"Monthly surplus:         ${monthly_surplus:>10,.2f} ({savings_percent:.1f}%)")
    print(f"Annual surplus:          ${annual_surplus:>10,.2f}")
else:
    deficit = abs(monthly_surplus)
    print(f"Monthly deficit:        -${deficit:>10,.2f}")
    print(f"Annual deficit:         -${abs(annual_surplus):>10,.2f}")

print(f"\nSAVINGS ANALYSIS:")
print(f"Current savings:         ${current_savings:>10,.2f}")
print(f"Emergency fund goal:     ${emergency_goal:>10,.2f}")
if emergency_needed > 0:
    print(f"Amount needed:           ${emergency_needed:>10,.2f}")
    if months_to_goal != float('inf') and months_to_goal > 0:
        print(f"Months to reach goal:    {months_to_goal:>10.1f}")

print(f"\nFINANCIAL HEALTH CHECK:")
print(f"Rent/Housing <= 30%:     {'✓ GOOD' if is_healthy_rent else '✗ HIGH'}")
print(f"Savings >= 20%:          {'✓ GOOD' if is_healthy_savings else '✗ LOW'}")
print(f"Positive cash flow:      {'✓ YES' if is_surplus else '✗ NO'}")

print("=" * 50)
```

## Data Validation Techniques

### Input Validation Patterns
```python
# Validating numeric input
def get_valid_number(prompt, min_val=None, max_val=None):
    while True:
        try:
            value = float(input(prompt))
            if min_val is not None and value < min_val:
                print(f"Value must be at least {min_val}")
                continue
            if max_val is not None and value > max_val:
                print(f"Value must be no more than {max_val}")
                continue
            return value
        except ValueError:
            print("Please enter a valid number")

# Validating yes/no input
def get_yes_no(prompt):
    while True:
        response = input(prompt + " (yes/no): ").lower().strip()
        if response in ["yes", "y", "true", "1"]:
            return True
        elif response in ["no", "n", "false", "0"]:
            return False
        else:
            print("Please enter yes or no")

# Using the functions
age = get_valid_number("Enter age (0-120): ", 0, 120)
is_student = get_yes_no("Are you a student?")
```

## Common Patterns and Best Practices

### Organizing Your Code
```python
# Good organization example
print("=== Program Title ===")

# 1. Get all input first
name = input("Name: ")
age = int(input("Age: "))

# 2. Do all calculations
birth_year = 2024 - age
retirement_age = 65
years_to_retirement = retirement_age - age

# 3. Display all output
print(f"\nResults for {name}:")
print(f"Born in: {birth_year}")
print(f"Years until retirement: {years_to_retirement}")
```

### Error Prevention
```python
# Check for division by zero
denominator = float(input("Enter denominator: "))
if denominator != 0:
    result = 10 / denominator
    print(f"Result: {result}")
else:
    print("Cannot divide by zero!")

# Validate ranges
percentage = float(input("Enter percentage (0-100): "))
if 0 <= percentage <= 100:
    decimal = percentage / 100
    print(f"As decimal: {decimal}")
else:
    print("Percentage must be between 0 and 100")
```

## Challenge Problems (Optional)

### Challenge 4.1: Loan Calculator
```python
# Create a comprehensive loan calculator that calculates:
# 1. Monthly payment using loan formula
# 2. Total interest paid
# 3. Payment schedule (first few payments)
# Formula: M = P * [r(1+r)^n] / [(1+r)^n - 1]
# Where: M = monthly payment, P = principal, r = monthly rate, n = number of payments

principal = float(input("Loan amount: $"))
annual_rate = float(input("Annual interest rate (%): ")) / 100
years = int(input("Loan term (years): "))

# Calculate and display results
```

### Challenge 4.2: GPA Calculator
```python
# Create a GPA calculator that:
# 1. Gets course names and credit hours
# 2. Gets letter grades (A, B, C, D, F)
# 3. Converts to grade points (A=4, B=3, C=2, D=1, F=0)
# 4. Calculates cumulative GPA
# 5. Shows how many credit hours of A's needed to reach target GPA
```

## Lesson Summary

✅ **What we learned:**
- Combining data types in complex programs
- Data validation and error prevention
- Creating professional-looking output
- Organizing code for readability
- Building real-world applications

✅ **Key takeaways:**
- Always validate user input when possible
- Organize code: input → calculations → output
- Use meaningful variable names
- Format output for professional appearance
- Test with different types of input

## Next Lesson Preview
Now we're ready for the big topic: **Conditional Logic**! In the next three lessons, we'll master if statements, elif chains, and complex conditions. This is where your programs really start to make decisions!

## Self-Check Questions
Before moving on, make sure you can answer:
1. How do you validate that a number is within a certain range?
2. What's the best way to organize a program's structure?
3. How do you handle division by zero?
4. What's the difference between getting input and validating input?
5. How do you format numbers to show as currency?

Excellent work! You now have all the foundational skills needed to start making your programs intelligent with conditional logic. Let's dive into decision-making in the next lesson!