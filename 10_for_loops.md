# Lesson 10: For Loops

## Learning Objectives
By the end of this lesson, you will:
- Understand what loops are and why they're essential
- Master for loop syntax and iteration patterns
- Loop through lists, strings, and ranges
- Use enumerate() and zip() for advanced iteration
- Apply nested loops for complex problems
- Write efficient, readable loop code

## What Are Loops?

Loops let you repeat code multiple times without writing it over and over:

```python
# Without loops (repetitive and inefficient)
print("Welcome student 1")
print("Welcome student 2")
print("Welcome student 3")
# ... what if you have 100 students?

# With loops (elegant and scalable)
for i in range(1, 4):
    print(f"Welcome student {i}")
```

### Why Loops Are Essential
- Avoid code repetition
- Process collections of data
- Handle variable amounts of data
- Make programs scalable and maintainable

## Basic For Loop Syntax

The `for` loop iterates through a sequence of items:

```python
# Basic syntax: for variable in sequence:
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(f"I like {fruit}")

# Output:
# I like apple
# I like banana
# I like cherry
```

### For Loops with Different Data Types

```python
# Loop through a string
word = "Python"
for letter in word:
    print(letter)

# Loop through numbers
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    print(f"Number: {num}")
    print(f"Squared: {num ** 2}")

# Loop through mixed data
student_info = ["Alice", 20, "Computer Science", 3.8]
for item in student_info:
    print(f"Info: {item} (type: {type(item).__name__})")
```

## The range() Function

`range()` creates sequences of numbers for loops:

```python
# range(stop) - numbers from 0 to stop-1
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4

# range(start, stop) - numbers from start to stop-1
for i in range(2, 8):
    print(i)  # 2, 3, 4, 5, 6, 7

# range(start, stop, step) - numbers with custom step
for i in range(0, 10, 2):
    print(i)  # 0, 2, 4, 6, 8

# Counting backwards
for i in range(10, 0, -1):
    print(i)  # 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

### Practical range() Examples
```python
# Print multiplication table
number = 7
for i in range(1, 11):
    print(f"{number} x {i} = {number * i}")

# Count down timer
print("Countdown:")
for i in range(5, 0, -1):
    print(i)
print("Blast off!")

# Generate even numbers
even_numbers = []
for i in range(2, 21, 2):
    even_numbers.append(i)
print(even_numbers)  # [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

## Quick Practice Exercises

### Exercise 10.1: Basic For Loop Practice
```python
# 1. Print all numbers from 1 to 10
print("Numbers 1 to 10:")
for i in range(1, 11):
    print(i)

# 2. Calculate sum of numbers 1 to 100
total = 0
for i in range(1, 101):
    total += i
print(f"Sum of 1 to 100: {total}")

# 3. Print each character in your name with its position
name = "Alice"
for i in range(len(name)):
    print(f"Position {i}: {name[i]}")

# 4. Create a list of squares
squares = []
for i in range(1, 11):
    squares.append(i ** 2)
print(f"Squares: {squares}")

# 5. Print every third number from 3 to 30
print("Every third number from 3 to 30:")
for i in range(3, 31, 3):
    print(i)
```

### Exercise 10.2: Processing Lists with Loops
```python
# Student grades analysis
grades = [85, 92, 78, 96, 88, 79, 94, 87]

# Calculate total and average
total_points = 0
for grade in grades:
    total_points += grade

average = total_points / len(grades)
print(f"Average grade: {average:.1f}")

# Count grades above average
above_average = 0
for grade in grades:
    if grade > average:
        above_average += 1

print(f"Grades above average: {above_average}")

# Find highest and lowest grades manually (without min/max)
highest = grades[0]  # Start with first grade
lowest = grades[0]

for grade in grades:
    if grade > highest:
        highest = grade
    if grade < lowest:
        lowest = grade

print(f"Highest grade: {highest}")
print(f"Lowest grade: {lowest}")
print(f"Grade range: {highest - lowest}")
```

## Looping with Indexes using enumerate()

Sometimes you need both the item and its position:

```python
# Without enumerate (not recommended)
fruits = ["apple", "banana", "cherry"]
for i in range(len(fruits)):
    print(f"{i}: {fruits[i]}")

# With enumerate (recommended)
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# Start enumerate at different number
for position, fruit in enumerate(fruits, 1):  # Start at 1
    print(f"#{position}: {fruit}")
```

### Practical enumerate() Examples
```python
# Grade book with student positions
students = ["Alice", "Bob", "Charlie", "Diana"]
grades = [92, 87, 94, 89]

print("=== Grade Report ===")
for i, student in enumerate(students):
    print(f"{i+1}. {student}: {grades[i]}%")

# Find position of specific items
shopping_list = ["milk", "eggs", "bread", "apples", "cheese"]
search_item = "bread"

for index, item in enumerate(shopping_list):
    if item == search_item:
        print(f"Found {search_item} at position {index}")
        break

# Modify list based on position
numbers = [10, 20, 30, 40, 50]
for index, number in enumerate(numbers):
    if index % 2 == 0:  # Even positions
        numbers[index] = number * 2

print(numbers)  # [20, 20, 60, 40, 100]
```

## Looping Through Multiple Lists with zip()

Use `zip()` to loop through multiple lists simultaneously:

```python
# Basic zip usage
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 22]
cities = ["New York", "London", "Tokyo"]

for name, age, city in zip(names, ages, cities):
    print(f"{name} is {age} years old and lives in {city}")

# Zip stops at shortest list
list1 = [1, 2, 3, 4, 5]
list2 = ['a', 'b', 'c']  # Shorter list

for num, letter in zip(list1, list2):
    print(f"{num}-{letter}")  # Only prints 3 pairs
```

### Practical zip() Examples
```python
# Calculate total scores across multiple tests
test1_scores = [85, 92, 78, 96]
test2_scores = [88, 94, 82, 93]
test3_scores = [90, 89, 85, 98]
students = ["Alice", "Bob", "Charlie", "Diana"]

print("=== Total Scores ===")
for student, t1, t2, t3 in zip(students, test1_scores, test2_scores, test3_scores):
    total = t1 + t2 + t3
    average = total / 3
    print(f"{student}: {total} points (avg: {average:.1f})")

# Create dictionary from two lists
keys = ["name", "age", "occupation"]
values = ["Alice", 25, "Engineer"]
person = {}

for key, value in zip(keys, values):
    person[key] = value

print(person)  # {'name': 'Alice', 'age': 25, 'occupation': 'Engineer'}
```

## Hands-On Coding Exercise

### Exercise 10.3: Sales Report Generator
```python
print("=== Monthly Sales Report Generator ===")

# Sales data
months = ["January", "February", "March", "April", "May", "June"]
sales = [45000, 52000, 48000, 58000, 61000, 55000]
targets = [50000, 50000, 50000, 55000, 60000, 58000]

print("=== Monthly Performance ===")
print(f"{'Month':<10} {'Sales':<10} {'Target':<10} {'Difference':<12} {'Status'}")
print("-" * 55)

total_sales = 0
total_target = 0
months_above_target = 0

for month, sale, target in zip(months, sales, targets):
    difference = sale - target
    status = "✓ Met" if difference >= 0 else "✗ Missed"

    if difference >= 0:
        months_above_target += 1

    total_sales += sale
    total_target += target

    print(f"{month:<10} ${sale:<9,} ${target:<9,} ${difference:<11,} {status}")

# Summary statistics
print("-" * 55)
print(f"{'TOTALS':<10} ${total_sales:<9,} ${total_target:<9,} ${total_sales-total_target:<11,}")

print(f"\n=== Summary Statistics ===")
print(f"Total Sales: ${total_sales:,}")
print(f"Total Target: ${total_target:,}")
print(f"Overall Performance: {(total_sales/total_target*100):.1f}% of target")
print(f"Months Meeting Target: {months_above_target}/{len(months)}")

# Find best and worst months
best_month_index = 0
worst_month_index = 0

for i, sale in enumerate(sales):
    if sale > sales[best_month_index]:
        best_month_index = i
    if sale < sales[worst_month_index]:
        worst_month_index = i

print(f"Best Month: {months[best_month_index]} (${sales[best_month_index]:,})")
print(f"Worst Month: {months[worst_month_index]} (${sales[worst_month_index]:,})")

# Calculate month-over-month growth
print(f"\n=== Growth Analysis ===")
for i in range(1, len(months)):
    current_sales = sales[i]
    previous_sales = sales[i-1]
    growth = ((current_sales - previous_sales) / previous_sales) * 100

    trend = "📈" if growth > 0 else "📉" if growth < 0 else "📊"
    print(f"{months[i]}: {growth:+.1f}% vs {months[i-1]} {trend}")

# Forecast next month (simple average of last 3 months)
recent_avg = sum(sales[-3:]) / 3
print(f"\nNext Month Forecast (3-month avg): ${recent_avg:,.0f}")
```

## Nested Loops

Loops inside loops for complex iterations:

```python
# Basic nested loop
for i in range(3):
    for j in range(2):
        print(f"i={i}, j={j}")

# Practical example: multiplication table
print("Multiplication Table (1-5):")
print("   ", end="")
for j in range(1, 6):
    print(f"{j:4}", end="")
print()

for i in range(1, 6):
    print(f"{i}: ", end="")
    for j in range(1, 6):
        print(f"{i*j:4}", end="")
    print()
```

### Practical Nested Loop Examples
```python
# Process nested data
classes = [
    ["Math", "Science", "English"],
    ["History", "Art", "Music"],
    ["PE", "Computer Science"]
]

print("=== Class Schedule ===")
for day, subjects in enumerate(classes, 1):
    print(f"Day {day}:")
    for period, subject in enumerate(subjects, 1):
        print(f"  Period {period}: {subject}")

# Create coordinate pairs
coordinates = []
for x in range(3):
    for y in range(3):
        coordinates.append((x, y))
print(coordinates)  # [(0,0), (0,1), (0,2), (1,0), (1,1), ...]

# Pattern printing
print("Triangle pattern:")
for i in range(1, 6):
    for j in range(i):
        print("*", end="")
    print()  # New line after each row
```

## Loop Control: break and continue

Control loop execution with `break` and `continue`:

### The break Statement
```python
# Stop loop when condition is met
numbers = [1, 3, 7, 2, 9, 4, 6]
target = 7

for i, num in enumerate(numbers):
    if num == target:
        print(f"Found {target} at position {i}")
        break
    print(f"Checking {num}")

# Search with validation
shopping_list = ["milk", "eggs", "bread", "apples"]
search_item = input("What are you looking for? ")

found = False
for item in shopping_list:
    if item.lower() == search_item.lower():
        print(f"✓ Found {item} in your list!")
        found = True
        break

if not found:
    print(f"✗ {search_item} is not in your list")
```

### The continue Statement
```python
# Skip certain iterations
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print("Odd numbers only:")
for num in numbers:
    if num % 2 == 0:  # If even
        continue  # Skip to next iteration
    print(num)

# Process valid data only
test_scores = [85, -1, 92, 150, 78, 96, -5, 88]

print("Valid test scores:")
total = 0
count = 0

for score in test_scores:
    if score < 0 or score > 100:  # Invalid score
        print(f"Skipping invalid score: {score}")
        continue

    print(f"Valid score: {score}")
    total += score
    count += 1

if count > 0:
    average = total / count
    print(f"Average of valid scores: {average:.1f}")
```

## Live Exercise: Data Analysis Dashboard

We'll work through this together:

```python
print("=== Data Analysis Dashboard ===")

# Sample data: website traffic
dates = ["2024-01-01", "2024-01-02", "2024-01-03", "2024-01-04", "2024-01-05", "2024-01-06", "2024-01-07"]
page_views = [1250, 1380, 1420, 1190, 1650, 1820, 1450]
unique_visitors = [980, 1050, 1120, 920, 1300, 1450, 1150]
bounce_rates = [0.35, 0.32, 0.28, 0.41, 0.25, 0.23, 0.29]  # Percentage who leave immediately

print("=== Weekly Website Analytics Report ===")
print(f"{'Date':<12} {'Views':<8} {'Visitors':<10} {'Bounce %':<9} {'Engagement':<12}")
print("-" * 60)

total_views = 0
total_visitors = 0
total_bounce = 0
best_day_views = 0
best_day_index = 0

for i, (date, views, visitors, bounce) in enumerate(zip(dates, page_views, unique_visitors, bounce_rates)):
    # Calculate engagement score (lower bounce rate = higher engagement)
    engagement = "High" if bounce < 0.3 else "Medium" if bounce < 0.4 else "Low"

    # Track totals
    total_views += views
    total_visitors += visitors
    total_bounce += bounce

    # Find best day
    if views > best_day_views:
        best_day_views = views
        best_day_index = i

    # Display row
    print(f"{date:<12} {views:<8,} {visitors:<10,} {bounce*100:<8.1f}% {engagement:<12}")

# Calculate averages
avg_views = total_views / len(page_views)
avg_visitors = total_visitors / len(unique_visitors)
avg_bounce = total_bounce / len(bounce_rates)

print("-" * 60)
print(f"{'AVERAGES':<12} {avg_views:<8.0f} {avg_visitors:<10.0f} {avg_bounce*100:<8.1f}%")

print(f"\n=== Key Insights ===")
print(f"Total page views: {total_views:,}")
print(f"Total unique visitors: {total_visitors:,}")
print(f"Average pages per visitor: {total_views/total_visitors:.1f}")
print(f"Best traffic day: {dates[best_day_index]} ({best_day_views:,} views)")

# Day-over-day growth analysis
print(f"\n=== Growth Trends ===")
for i in range(1, len(page_views)):
    previous_views = page_views[i-1]
    current_views = page_views[i]
    growth = ((current_views - previous_views) / previous_views) * 100

    trend_symbol = "📈" if growth > 0 else "📉" if growth < 0 else "📊"
    print(f"{dates[i]}: {growth:+.1f}% change from previous day {trend_symbol}")

# Performance categories
print(f"\n=== Performance Analysis ===")
high_traffic_days = 0
low_bounce_days = 0
problem_days = []

for i, (date, views, bounce) in enumerate(zip(dates, page_views, bounce_rates)):
    if views > avg_views:
        high_traffic_days += 1

    if bounce < 0.3:
        low_bounce_days += 1

    # Flag problematic days (low traffic AND high bounce)
    if views < avg_views * 0.8 and bounce > 0.35:
        problem_days.append((date, views, bounce))

print(f"High traffic days: {high_traffic_days}/{len(dates)}")
print(f"Low bounce rate days: {low_bounce_days}/{len(dates)}")

if problem_days:
    print(f"\n⚠️ Days needing attention:")
    for date, views, bounce in problem_days:
        print(f"  {date}: {views:,} views, {bounce*100:.1f}% bounce rate")

# Weekly goals check
weekly_goal_views = 10000
weekly_goal_bounce = 0.30

if total_views >= weekly_goal_views:
    print(f"\n✅ Weekly view goal achieved! ({total_views:,} >= {weekly_goal_views:,})")
else:
    shortfall = weekly_goal_views - total_views
    print(f"\n❌ Weekly view goal missed by {shortfall:,} views")

if avg_bounce <= weekly_goal_bounce:
    print(f"✅ Bounce rate goal achieved! ({avg_bounce*100:.1f}% <= {weekly_goal_bounce*100:.1f}%)")
else:
    excess = (avg_bounce - weekly_goal_bounce) * 100
    print(f"❌ Bounce rate too high by {excess:.1f} percentage points")

print(f"\n=== End of Report ===")
```

## Common Loop Patterns

### Processing and Collecting Results
```python
# Transform data
prices = [19.99, 25.50, 15.75, 32.00]
discounted_prices = []

for price in prices:
    discounted_price = price * 0.8  # 20% off
    discounted_prices.append(discounted_price)

print(f"Original: {prices}")
print(f"Discounted: {discounted_prices}")

# Filter data
grades = [85, 92, 67, 78, 96, 54, 88, 91]
passing_grades = []
failing_grades = []

for grade in grades:
    if grade >= 70:
        passing_grades.append(grade)
    else:
        failing_grades.append(grade)

print(f"Passing: {passing_grades}")
print(f"Failing: {failing_grades}")
```

### Counting and Accumulating
```python
# Count occurrences
text = "hello world"
vowel_count = 0

for char in text:
    if char.lower() in "aeiou":
        vowel_count += 1

print(f"Vowels in '{text}': {vowel_count}")

# Running totals
monthly_expenses = [1200, 1450, 1320, 1180, 1650]
running_total = 0

print("Monthly expense tracking:")
for month, expense in enumerate(monthly_expenses, 1):
    running_total += expense
    print(f"Month {month}: ${expense:,} (Total so far: ${running_total:,})")
```

## Challenge Problems (Optional)

### Challenge 10.1: Prime Number Finder
```python
# Find all prime numbers between 2 and 50
# A prime number is only divisible by 1 and itself

def is_prime(n):
    if n < 2:
        return False

    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

primes = []
for num in range(2, 51):
    if is_prime(num):
        primes.append(num)

print(f"Prime numbers 2-50: {primes}")
```

### Challenge 10.2: Text Analysis
```python
# Analyze a paragraph of text:
text = """Python is a powerful programming language. It is easy to learn and
versatile. Many companies use Python for web development, data science, and
automation. Python's syntax is clear and readable."""

# Count:
# 1. Words
# 2. Sentences (periods)
# 3. Characters (excluding spaces)
# 4. Most frequent word
# 5. Average word length

# Your solution here using for loops
```

## Lesson Summary

✅ **What we mastered:**
- For loop syntax and iteration through sequences
- Using range() for number sequences
- enumerate() for index-value pairs
- zip() for multiple list iteration
- Nested loops for complex problems
- Loop control with break and continue
- Common loop patterns and best practices

✅ **Key takeaways:**
- Loops eliminate repetitive code
- Choose the right iteration method for your data
- enumerate() and zip() make loops more powerful
- Nested loops multiply iterations (be careful with large data)
- break and continue give you fine control
- Always consider readability when writing loops

## Next Lesson Preview
In Lesson 11, we'll learn about **while loops** - loops that continue until a condition becomes false. These are perfect for scenarios where you don't know in advance how many times to loop!

## Self-Check Questions
Before moving on, make sure you can answer:
1. What's the difference between `range(5)` and `range(1, 6)`?
2. When would you use `enumerate()` instead of a regular for loop?
3. What does `zip()` do when lists have different lengths?
4. How do `break` and `continue` differ?
5. What's a common use case for nested loops?

Fantastic progress! You now have powerful tools for processing data and automating repetitive tasks. For loops are one of the most frequently used features in Python programming!