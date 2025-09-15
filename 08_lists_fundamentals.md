# Lesson 8: Lists Fundamentals

## Learning Objectives
By the end of this lesson, you will:
- Understand what lists are and why they're useful
- Create and access list elements
- Modify lists by adding, removing, and changing items
- Use list methods for common operations
- Work with lists of different data types
- Solve problems using lists

## What Are Lists?

So far, we've stored single values in variables:
```python
name = "Alice"
age = 25
score = 95.5
```

But what if you need to store multiple related values? That's where **lists** come in!

```python
# Instead of this:
student1 = "Alice"
student2 = "Bob"
student3 = "Charlie"

# Use this:
students = ["Alice", "Bob", "Charlie"]
```

### Why Lists Are Useful
- Store multiple related items in one variable
- Keep data organized
- Process multiple items with less code
- Items stay in the order you put them
- Can grow and shrink as needed

## Creating Lists

### Basic List Creation
```python
# Empty list
empty_list = []

# List of numbers
ages = [25, 30, 22, 35, 28]
scores = [95.5, 87.2, 92.0, 78.5]

# List of strings
names = ["Alice", "Bob", "Charlie", "Diana"]
colors = ["red", "green", "blue", "yellow"]

# List of booleans
results = [True, False, True, True]

# Mixed data types (possible but use carefully)
mixed = ["Alice", 25, 95.5, True]
```

### Lists from User Input
```python
# Get multiple items from user
shopping_list = []
shopping_list.append(input("Item 1: "))
shopping_list.append(input("Item 2: "))
shopping_list.append(input("Item 3: "))

# Or create from a string
items_text = input("Enter items separated by commas: ")
shopping_list = items_text.split(",")
```

## Accessing List Elements

Lists use **index numbers** starting from 0:

```python
fruits = ["apple", "banana", "cherry", "date"]
#          0        1         2        3

# Access by index
print(fruits[0])    # "apple"
print(fruits[1])    # "banana"
print(fruits[2])    # "cherry"
print(fruits[3])    # "date"

# Negative indexing (counts from end)
print(fruits[-1])   # "date" (last item)
print(fruits[-2])   # "cherry" (second to last)
print(fruits[-3])   # "banana"
print(fruits[-4])   # "apple" (first item)
```

### List Length
```python
fruits = ["apple", "banana", "cherry"]
print(len(fruits))  # 3

# Use length to avoid index errors
last_index = len(fruits) - 1
print(fruits[last_index])  # "cherry"
```

## Quick Practice Exercises

### Exercise 8.1: Creating and Accessing Lists
```python
# Create lists for different data
favorite_movies = ["The Matrix", "Inception", "Interstellar"]
lucky_numbers = [7, 13, 21, 42]
grades = [85.5, 92.0, 78.5, 95.0]

# Access specific elements
print("First movie:", favorite_movies[0])
print("Last lucky number:", lucky_numbers[-1])
print("Second grade:", grades[1])

# Calculate with list elements
average_grade = sum(grades) / len(grades)
print(f"Average grade: {average_grade:.1f}")

# Check list properties
print(f"You have {len(favorite_movies)} favorite movies")
print(f"Highest grade: {max(grades)}")
print(f"Lowest grade: {min(grades)}")
```

### Exercise 8.2: Personal Information Lists
```python
# Create personal data lists
family_names = ["Mom", "Dad", "Sister", "Brother"]
family_ages = [45, 48, 22, 20]
family_hobbies = ["reading", "golf", "painting", "gaming"]

print("=== Family Information ===")
for i in range(len(family_names)):
    print(f"{family_names[i]} is {family_ages[i]} years old and likes {family_hobbies[i]}")

# Find specific information
oldest_index = family_ages.index(max(family_ages))
youngest_index = family_ages.index(min(family_ages))

print(f"\nOldest: {family_names[oldest_index]} ({family_ages[oldest_index]})")
print(f"Youngest: {family_names[youngest_index]} ({family_ages[youngest_index]})")
```

## Modifying Lists

### Adding Elements
```python
# Start with empty list
shopping_cart = []

# Add items one by one
shopping_cart.append("milk")
shopping_cart.append("eggs")
shopping_cart.append("bread")
print(shopping_cart)  # ["milk", "eggs", "bread"]

# Insert at specific position
shopping_cart.insert(0, "apples")  # Insert at beginning
shopping_cart.insert(2, "cheese")  # Insert at index 2
print(shopping_cart)  # ["apples", "milk", "cheese", "eggs", "bread"]

# Add multiple items
more_items = ["butter", "juice"]
shopping_cart.extend(more_items)
print(shopping_cart)  # ["apples", "milk", "cheese", "eggs", "bread", "butter", "juice"]
```

### Removing Elements
```python
fruits = ["apple", "banana", "cherry", "banana", "date"]

# Remove by value (removes first occurrence)
fruits.remove("banana")
print(fruits)  # ["apple", "cherry", "banana", "date"]

# Remove by index
removed_item = fruits.pop(1)  # Removes and returns item at index 1
print(f"Removed: {removed_item}")  # "cherry"
print(fruits)  # ["apple", "banana", "date"]

# Remove last item
last_item = fruits.pop()
print(f"Last item: {last_item}")  # "date"
print(fruits)  # ["apple", "banana"]

# Delete by index (doesn't return the item)
del fruits[0]
print(fruits)  # ["banana"]

# Clear entire list
fruits.clear()
print(fruits)  # []
```

### Changing Elements
```python
grades = [85, 90, 78, 92]

# Change single element
grades[2] = 82  # Change 78 to 82
print(grades)   # [85, 90, 82, 92]

# Change multiple elements
grades[0:2] = [88, 94]  # Change first two grades
print(grades)   # [88, 94, 82, 92]
```

## Hands-On Coding Exercise

### Exercise 8.3: Student Grade Manager
```python
print("=== Student Grade Manager ===")

# Initialize empty lists
student_names = []
student_grades = []

# Get number of students
num_students = int(input("How many students? "))

# Collect student information
for i in range(num_students):
    print(f"\nStudent {i + 1}:")
    name = input("Name: ")
    grade = float(input("Grade: "))

    student_names.append(name)
    student_grades.append(grade)

# Display all students and grades
print(f"\n=== Grade Report ===")
print(f"{'Name':<15} {'Grade':<8} {'Letter'}")
print("-" * 30)

for i in range(len(student_names)):
    name = student_names[i]
    grade = student_grades[i]

    # Calculate letter grade
    if grade >= 90:
        letter = "A"
    elif grade >= 80:
        letter = "B"
    elif grade >= 70:
        letter = "C"
    elif grade >= 60:
        letter = "D"
    else:
        letter = "F"

    print(f"{name:<15} {grade:<8.1f} {letter}")

# Calculate statistics
if student_grades:
    average = sum(student_grades) / len(student_grades)
    highest = max(student_grades)
    lowest = min(student_grades)

    # Find student with highest grade
    highest_index = student_grades.index(highest)
    top_student = student_names[highest_index]

    print(f"\n=== Statistics ===")
    print(f"Class average: {average:.1f}")
    print(f"Highest grade: {highest} ({top_student})")
    print(f"Lowest grade: {lowest}")
    print(f"Grade range: {highest - lowest}")

    # Count letter grades
    a_count = sum(1 for grade in student_grades if grade >= 90)
    b_count = sum(1 for grade in student_grades if 80 <= grade < 90)
    c_count = sum(1 for grade in student_grades if 70 <= grade < 80)
    d_count = sum(1 for grade in student_grades if 60 <= grade < 70)
    f_count = sum(1 for grade in student_grades if grade < 60)

    print(f"\nGrade Distribution:")
    print(f"A's: {a_count}")
    print(f"B's: {b_count}")
    print(f"C's: {c_count}")
    print(f"D's: {d_count}")
    print(f"F's: {f_count}")
```

## Common List Methods

### Useful List Methods
```python
numbers = [3, 1, 4, 1, 5, 9, 2]

# Count occurrences
count_1 = numbers.count(1)  # 2

# Find index of value
index_4 = numbers.index(4)  # 2

# Sort list (modifies original)
numbers.sort()
print(numbers)  # [1, 1, 2, 3, 4, 5, 9]

# Sort in reverse
numbers.sort(reverse=True)
print(numbers)  # [9, 5, 4, 3, 2, 1, 1]

# Reverse list order
numbers.reverse()
print(numbers)  # [1, 1, 2, 3, 4, 5, 9]

# Create sorted copy (doesn't modify original)
original = [3, 1, 4, 1, 5]
sorted_copy = sorted(original)
print(original)     # [3, 1, 4, 1, 5] (unchanged)
print(sorted_copy)  # [1, 1, 3, 4, 5]
```

### String Methods with Lists
```python
# Split string into list
sentence = "The quick brown fox"
words = sentence.split()  # Split on spaces
print(words)  # ["The", "quick", "brown", "fox"]

csv_data = "apple,banana,cherry,date"
fruits = csv_data.split(",")  # Split on commas
print(fruits)  # ["apple", "banana", "cherry", "date"]

# Join list into string
words = ["Python", "is", "awesome"]
sentence = " ".join(words)
print(sentence)  # "Python is awesome"

items = ["milk", "eggs", "bread"]
shopping_list = ", ".join(items)
print(shopping_list)  # "milk, eggs, bread"
```

## Working with Different Data Types

### Lists of Numbers
```python
# Test scores
test_scores = [85, 92, 78, 96, 88]

# Mathematical operations
total = sum(test_scores)
average = total / len(test_scores)
highest = max(test_scores)
lowest = min(test_scores)

print(f"Total points: {total}")
print(f"Average: {average:.1f}")
print(f"Highest: {highest}")
print(f"Lowest: {lowest}")
print(f"Range: {highest - lowest}")

# Add bonus points to all scores
bonus = 5
for i in range(len(test_scores)):
    test_scores[i] += bonus

print(f"Scores with bonus: {test_scores}")
```

### Lists of Strings
```python
# Student names
students = ["Alice Johnson", "Bob Smith", "Charlie Brown"]

# String operations on list elements
print("Student initials:")
for name in students:
    parts = name.split()
    first_initial = parts[0][0]
    last_initial = parts[1][0]
    print(f"{name}: {first_initial}.{last_initial}.")

# Find students with specific criteria
long_names = []
for name in students:
    if len(name) > 10:
        long_names.append(name)

print(f"Students with long names: {long_names}")
```

## Live Exercise: Inventory Management System

We'll work through this together:

```python
print("=== Simple Inventory Management ===")

# Initialize inventory
inventory_items = []
inventory_quantities = []
inventory_prices = []

def display_inventory():
    """Display current inventory"""
    if not inventory_items:
        print("Inventory is empty")
        return

    print(f"\n{'Item':<15} {'Quantity':<10} {'Price':<10} {'Value'}")
    print("-" * 50)

    total_value = 0
    for i in range(len(inventory_items)):
        item = inventory_items[i]
        quantity = inventory_quantities[i]
        price = inventory_prices[i]
        value = quantity * price
        total_value += value

        print(f"{item:<15} {quantity:<10} ${price:<9.2f} ${value:.2f}")

    print("-" * 50)
    print(f"Total Inventory Value: ${total_value:.2f}")

def add_item():
    """Add new item to inventory"""
    item_name = input("Item name: ").strip()

    # Check if item already exists
    if item_name in inventory_items:
        index = inventory_items.index(item_name)
        additional_qty = int(input(f"Add quantity to existing {item_name}: "))
        inventory_quantities[index] += additional_qty
        print(f"Updated {item_name} quantity to {inventory_quantities[index]}")
    else:
        # New item
        quantity = int(input("Quantity: "))
        price = float(input("Price per unit: $"))

        inventory_items.append(item_name)
        inventory_quantities.append(quantity)
        inventory_prices.append(price)

        print(f"Added {quantity} {item_name}(s) at ${price:.2f} each")

def remove_item():
    """Remove or reduce item quantity"""
    if not inventory_items:
        print("No items in inventory")
        return

    item_name = input("Item to remove/reduce: ").strip()

    if item_name not in inventory_items:
        print("Item not found in inventory")
        return

    index = inventory_items.index(item_name)
    current_qty = inventory_quantities[index]

    print(f"Current quantity of {item_name}: {current_qty}")
    reduce_qty = int(input("Quantity to remove: "))

    if reduce_qty >= current_qty:
        # Remove item completely
        removed_item = inventory_items.pop(index)
        removed_qty = inventory_quantities.pop(index)
        removed_price = inventory_prices.pop(index)
        print(f"Removed all {removed_item} from inventory")
    else:
        # Reduce quantity
        inventory_quantities[index] -= reduce_qty
        print(f"Reduced {item_name} quantity to {inventory_quantities[index]}")

def search_item():
    """Search for items"""
    if not inventory_items:
        print("No items in inventory")
        return

    search_term = input("Search for item (partial name ok): ").lower()

    found_items = []
    for i, item in enumerate(inventory_items):
        if search_term in item.lower():
            found_items.append((i, item))

    if found_items:
        print(f"\nFound {len(found_items)} item(s):")
        for index, item in found_items:
            qty = inventory_quantities[index]
            price = inventory_prices[index]
            print(f"- {item}: {qty} units at ${price:.2f} each")
    else:
        print("No items found matching your search")

def low_stock_alert():
    """Show items with low stock"""
    threshold = int(input("Low stock threshold: "))

    low_stock_items = []
    for i in range(len(inventory_items)):
        if inventory_quantities[i] <= threshold:
            low_stock_items.append((inventory_items[i], inventory_quantities[i]))

    if low_stock_items:
        print(f"\n⚠️ Items with {threshold} or fewer units:")
        for item, qty in low_stock_items:
            print(f"- {item}: {qty} units")
    else:
        print(f"✅ No items below {threshold} units")

# Main program loop
while True:
    print(f"\n=== Inventory Management Menu ===")
    print("1. Display Inventory")
    print("2. Add Item")
    print("3. Remove/Reduce Item")
    print("4. Search Items")
    print("5. Low Stock Alert")
    print("6. Exit")

    choice = input("\nSelect option (1-6): ")

    if choice == "1":
        display_inventory()
    elif choice == "2":
        add_item()
    elif choice == "3":
        remove_item()
    elif choice == "4":
        search_item()
    elif choice == "5":
        low_stock_alert()
    elif choice == "6":
        print("\n=== Final Inventory Report ===")
        display_inventory()
        print("Goodbye!")
        break
    else:
        print("Invalid option. Please select 1-6.")
```

## Common Mistakes to Avoid

### 1. Index Out of Range
```python
# Wrong - causes error if list is empty or index too high
numbers = [1, 2, 3]
print(numbers[5])  # IndexError!

# Right - check length first
if len(numbers) > 5:
    print(numbers[5])
else:
    print("Index 5 is out of range")
```

### 2. Modifying List While Iterating
```python
# Wrong - can skip elements
numbers = [1, 2, 3, 4, 5]
for i, num in enumerate(numbers):
    if num % 2 == 0:
        numbers.remove(num)  # Don't do this!

# Right - iterate backwards or create new list
numbers = [1, 2, 3, 4, 5]
odd_numbers = [num for num in numbers if num % 2 != 0]
```

### 3. Confusing append() and extend()
```python
# append() adds one element (even if it's a list)
list1 = [1, 2, 3]
list1.append([4, 5])
print(list1)  # [1, 2, 3, [4, 5]]

# extend() adds each element from iterable
list2 = [1, 2, 3]
list2.extend([4, 5])
print(list2)  # [1, 2, 3, 4, 5]
```

## Challenge Problems (Optional)

### Challenge 8.1: Grade Book Analyzer
```python
# Create a program that:
# 1. Stores multiple students with multiple test scores each
# 2. Calculates each student's average
# 3. Finds class statistics
# 4. Identifies improvement/decline trends
# 5. Suggests interventions for struggling students

# Use lists to store: student names, and lists of scores for each student
```

### Challenge 8.2: Simple Database
```python
# Create a contact database using lists:
# - Names, phone numbers, emails, ages
# - Add/remove contacts
# - Search by any field
# - Sort by different criteria
# - Export to formatted text
```

## Lesson Summary

✅ **What we learned:**
- Creating lists with different data types
- Accessing elements by index (positive and negative)
- Adding elements with append(), insert(), extend()
- Removing elements with remove(), pop(), del, clear()
- Modifying existing elements
- Using list methods: sort(), reverse(), count(), index()
- Converting between strings and lists

✅ **Key takeaways:**
- Lists are ordered collections that can grow and shrink
- Indexing starts at 0
- Negative indexing counts from the end
- Lists are mutable (can be changed)
- Many built-in functions work with lists: len(), sum(), min(), max()
- Always check list length to avoid index errors

## Next Lesson Preview
In Lesson 9, we'll dive deeper into list operations - slicing, list comprehensions, nested lists, and advanced techniques that will make you a list power user!

## Self-Check Questions
Before moving on, make sure you can answer:
1. How do you access the last element of a list?
2. What's the difference between append() and extend()?
3. How do you find the index of a specific value in a list?
4. What happens if you try to access an index that doesn't exist?
5. How do you add an element at a specific position in a list?

Great job! You now understand the fundamentals of lists - one of Python's most useful data structures. You're ready to learn more advanced list techniques!