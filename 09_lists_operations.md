# Lesson 9: Lists Operations

## Learning Objectives
By the end of this lesson, you will:
- Master list slicing to extract portions of lists
- Use list comprehensions for elegant data processing
- Work with nested lists (lists of lists)
- Copy lists correctly to avoid reference issues
- Combine lists using various techniques
- Apply advanced list operations to solve complex problems

## List Slicing

Slicing lets you extract portions of a list using the syntax `list[start:end:step]`:

### Basic Slicing
```python
fruits = ["apple", "banana", "cherry", "date", "elderberry", "fig"]
#          0        1         2        3      4             5

# Get elements from index 1 to 4 (end is exclusive)
print(fruits[1:4])    # ["banana", "cherry", "date"]

# Get first 3 elements
print(fruits[:3])     # ["apple", "banana", "cherry"]

# Get last 3 elements
print(fruits[3:])     # ["date", "elderberry", "fig"]

# Get all elements (makes a copy)
print(fruits[:])      # ["apple", "banana", "cherry", "date", "elderberry", "fig"]
```

### Advanced Slicing
```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Step parameter - every 2nd element
print(numbers[::2])   # [0, 2, 4, 6, 8]

# Every 3rd element starting from index 1
print(numbers[1::3])  # [1, 4, 7]

# Reverse a list
print(numbers[::-1])  # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

# Last 5 elements in reverse
print(numbers[-5:][::-1])  # [9, 8, 7, 6, 5]

# Negative indices in slicing
print(numbers[-3:-1])      # [7, 8] (from 3rd last to 2nd last)
```

### Modifying Lists with Slicing
```python
grades = [85, 90, 78, 92, 88]

# Replace multiple elements
grades[1:3] = [95, 82]  # Replace elements at indices 1 and 2
print(grades)           # [85, 95, 82, 92, 88]

# Insert elements
grades[2:2] = [77, 89]  # Insert at index 2
print(grades)           # [85, 95, 77, 89, 82, 92, 88]

# Delete elements
del grades[1:3]         # Delete elements at indices 1 and 2
print(grades)           # [85, 89, 82, 92, 88]
```

## Quick Practice Exercises

### Exercise 9.1: Data Processing with Slicing
```python
# Weather data for a week (temperatures in Fahrenheit)
daily_temps = [72, 75, 68, 71, 74, 78, 80]
days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]

print("=== Weekly Weather Analysis ===")

# First half of week
first_half = daily_temps[:4]  # Mon-Thu
first_half_avg = sum(first_half) / len(first_half)
print(f"First half average: {first_half_avg:.1f}°F")

# Weekend temperatures
weekend = daily_temps[5:]     # Sat-Sun
weekend_avg = sum(weekend) / len(weekend)
print(f"Weekend average: {weekend_avg:.1f}°F")

# Every other day starting with Monday
alternating_days = daily_temps[::2]  # Mon, Wed, Fri, Sun
alt_avg = sum(alternating_days) / len(alternating_days)
print(f"Alternating days average: {alt_avg:.1f}°F")

# Warmest 3 days
sorted_temps = sorted(daily_temps, reverse=True)
warmest_3 = sorted_temps[:3]
print(f"Warmest 3 temperatures: {warmest_3}")

# Temperature trend (compare each day to previous)
print("\nDaily temperature changes:")
for i in range(1, len(daily_temps)):
    change = daily_temps[i] - daily_temps[i-1]
    direction = "↑" if change > 0 else "↓" if change < 0 else "→"
    print(f"{days[i]}: {daily_temps[i]}°F ({change:+.0f}°F {direction})")
```

## List Comprehensions

List comprehensions provide a concise way to create lists based on existing lists:

### Basic List Comprehensions
```python
# Traditional way
numbers = [1, 2, 3, 4, 5]
squares = []
for num in numbers:
    squares.append(num ** 2)
print(squares)  # [1, 4, 9, 16, 25]

# List comprehension way
numbers = [1, 2, 3, 4, 5]
squares = [num ** 2 for num in numbers]
print(squares)  # [1, 4, 9, 16, 25]

# General syntax: [expression for item in iterable]
```

### List Comprehensions with Conditions
```python
# Only even numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
evens = [num for num in numbers if num % 2 == 0]
print(evens)  # [2, 4, 6, 8, 10]

# Square only positive numbers
numbers = [-3, -1, 0, 2, 5, -2]
positive_squares = [num ** 2 for num in numbers if num > 0]
print(positive_squares)  # [4, 25]

# String processing
names = ["alice", "BOB", "Charlie", "DIANA"]
proper_names = [name.title() for name in names]
print(proper_names)  # ["Alice", "Bob", "Charlie", "Diana"]

# Conditional expression in comprehension
numbers = [1, 2, 3, 4, 5]
labels = ["even" if num % 2 == 0 else "odd" for num in numbers]
print(labels)  # ["odd", "even", "odd", "even", "odd"]
```

### Practical List Comprehensions
```python
# Extract data from strings
emails = ["john@email.com", "jane@company.org", "bob@school.edu"]
domains = [email.split("@")[1] for email in emails]
print(domains)  # ["email.com", "company.org", "school.edu"]

# Process grades
raw_grades = ["85%", "92%", "78%", "96%", "88%"]
numeric_grades = [int(grade[:-1]) for grade in raw_grades]
print(numeric_grades)  # [85, 92, 78, 96, 88]

# Filter and transform
words = ["python", "java", "javascript", "go", "rust"]
long_words_upper = [word.upper() for word in words if len(word) > 4]
print(long_words_upper)  # ["PYTHON", "JAVASCRIPT"]
```

## Nested Lists

Lists can contain other lists, creating two-dimensional structures:

### Creating and Accessing Nested Lists
```python
# Grade book - each student has multiple test scores
grades = [
    [85, 92, 78],  # Student 1
    [90, 88, 95],  # Student 2
    [76, 82, 89],  # Student 3
    [94, 91, 87]   # Student 4
]

# Access specific elements
print(grades[0])      # [85, 92, 78] - first student's grades
print(grades[0][1])   # 92 - first student's second grade
print(grades[2][2])   # 89 - third student's third grade

# Modify nested elements
grades[1][0] = 93     # Change second student's first grade
print(grades[1])      # [93, 88, 95]
```

### Working with Nested Lists
```python
# Student information system
students = [
    ["Alice", 20, [85, 92, 78]],
    ["Bob", 19, [90, 88, 95]],
    ["Charlie", 21, [76, 82, 89]]
]

print("=== Student Report ===")
for student in students:
    name = student[0]
    age = student[1]
    grades = student[2]
    average = sum(grades) / len(grades)

    print(f"{name} (age {age}): {grades} - Average: {average:.1f}")

# Calculate class statistics
all_grades = []
for student in students:
    all_grades.extend(student[2])  # Add all grades to one list

class_average = sum(all_grades) / len(all_grades)
print(f"\nClass average: {class_average:.1f}")
```

## Hands-On Coding Exercise

### Exercise 9.2: Sales Data Analyzer
```python
print("=== Sales Data Analyzer ===")

# Sales data: [month, product_sales_list]
sales_data = [
    ["January", [1200, 850, 950, 1100, 750]],
    ["February", [1350, 920, 1020, 1250, 800]],
    ["March", [1100, 780, 890, 1050, 720]],
    ["April", [1450, 980, 1150, 1300, 900]],
    ["May", [1600, 1100, 1250, 1400, 950]]
]

products = ["Widget A", "Widget B", "Widget C", "Widget D", "Widget E"]

# Display monthly summaries
print("=== Monthly Sales Summary ===")
monthly_totals = []

for month_data in sales_data:
    month = month_data[0]
    sales = month_data[1]
    total = sum(sales)
    average = total / len(sales)
    best_seller_index = sales.index(max(sales))
    best_product = products[best_seller_index]

    monthly_totals.append(total)

    print(f"\n{month}:")
    print(f"  Total sales: ${total:,}")
    print(f"  Average per product: ${average:,.0f}")
    print(f"  Best seller: {best_product} (${sales[best_seller_index]:,})")

    # Product breakdown
    print("  Product details:")
    for i, sale in enumerate(sales):
        print(f"    {products[i]}: ${sale:,}")

# Overall analysis
print(f"\n=== Overall Analysis ===")
total_sales = sum(monthly_totals)
best_month_index = monthly_totals.index(max(monthly_totals))
best_month = sales_data[best_month_index][0]

print(f"Total 5-month sales: ${total_sales:,}")
print(f"Best month: {best_month} (${monthly_totals[best_month_index]:,})")

# Product performance across all months
print(f"\n=== Product Performance ===")
for i, product in enumerate(products):
    product_total = sum(month[1][i] for month in sales_data)
    product_avg = product_total / len(sales_data)
    print(f"{product}: ${product_total:,} total, ${product_avg:,.0f} average")

# Growth analysis
print(f"\n=== Growth Analysis ===")
for i in range(1, len(sales_data)):
    current_month = sales_data[i][0]
    current_total = sum(sales_data[i][1])
    previous_total = sum(sales_data[i-1][1])
    growth = ((current_total - previous_total) / previous_total) * 100

    trend = "📈" if growth > 0 else "📉" if growth < 0 else "📊"
    print(f"{current_month}: {growth:+.1f}% {trend}")

# Top performing products by month
print(f"\n=== Monthly Winners ===")
for month_data in sales_data:
    month = month_data[0]
    sales = month_data[1]
    winner_index = sales.index(max(sales))
    winner = products[winner_index]
    winner_sales = sales[winner_index]
    print(f"{month}: {winner} (${winner_sales:,})")
```

## Copying Lists

Understanding how to properly copy lists is crucial:

### Reference vs Copy
```python
# Shallow copy issues
original = [1, 2, 3]
reference = original        # This creates a reference, not a copy!
reference.append(4)
print(original)            # [1, 2, 3, 4] - original is modified!

# Proper copying methods
original = [1, 2, 3]
copy1 = original.copy()    # Method 1
copy2 = original[:]        # Method 2
copy3 = list(original)     # Method 3

copy1.append(4)
print(original)            # [1, 2, 3] - original unchanged
print(copy1)               # [1, 2, 3, 4]
```

### Deep Copy for Nested Lists
```python
import copy

# Shallow copy problem with nested lists
original = [[1, 2], [3, 4]]
shallow = original.copy()
shallow[0].append(3)
print(original)            # [[1, 2, 3], [3, 4]] - inner list changed!

# Deep copy solution
original = [[1, 2], [3, 4]]
deep = copy.deepcopy(original)
deep[0].append(3)
print(original)            # [[1, 2], [3, 4]] - original unchanged
print(deep)                # [[1, 2, 3], [3, 4]]
```

## Combining Lists

### Different Ways to Combine Lists
```python
# Concatenation with +
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined = list1 + list2
print(combined)            # [1, 2, 3, 4, 5, 6]

# Extending (modifies original)
list1 = [1, 2, 3]
list2 = [4, 5, 6]
list1.extend(list2)
print(list1)               # [1, 2, 3, 4, 5, 6]

# Unpacking (Python 3.5+)
list1 = [1, 2, 3]
list2 = [4, 5, 6]
list3 = [7, 8]
combined = [*list1, *list2, *list3]
print(combined)            # [1, 2, 3, 4, 5, 6, 7, 8]

# Zip for combining parallel lists
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 22]
combined = list(zip(names, ages))
print(combined)            # [("Alice", 25), ("Bob", 30), ("Charlie", 22)]
```

## Live Exercise: Student Database Manager

We'll work through this together:

```python
print("=== Student Database Manager ===")

# Database structure: [name, age, grades, courses, contact_info]
student_database = []

def add_student():
    """Add a new student to database"""
    print("\n--- Adding New Student ---")
    name = input("Student name: ")
    age = int(input("Age: "))

    # Get grades
    grades = []
    while True:
        grade_input = input("Enter grade (or 'done' to finish): ")
        if grade_input.lower() == 'done':
            break
        try:
            grade = float(grade_input)
            if 0 <= grade <= 100:
                grades.append(grade)
            else:
                print("Grade must be between 0 and 100")
        except ValueError:
            print("Please enter a valid number")

    # Get courses
    courses_input = input("Enter courses (comma-separated): ")
    courses = [course.strip() for course in courses_input.split(",")]

    # Get contact info
    email = input("Email: ")
    phone = input("Phone: ")
    contact_info = {"email": email, "phone": phone}

    # Create student record
    student = [name, age, grades, courses, contact_info]
    student_database.append(student)
    print(f"✅ Added {name} to database")

def display_all_students():
    """Display all students with summary info"""
    if not student_database:
        print("No students in database")
        return

    print(f"\n=== Student Database ({len(student_database)} students) ===")
    print(f"{'Name':<15} {'Age':<5} {'Avg Grade':<10} {'Courses':<8} {'Contact'}")
    print("-" * 60)

    for student in student_database:
        name = student[0]
        age = student[1]
        grades = student[2]
        courses = student[3]
        contact = student[4]

        avg_grade = sum(grades) / len(grades) if grades else 0
        num_courses = len(courses)
        has_contact = "Yes" if contact["email"] else "No"

        print(f"{name:<15} {age:<5} {avg_grade:<10.1f} {num_courses:<8} {has_contact}")

def search_students():
    """Search students by various criteria"""
    if not student_database:
        print("No students in database")
        return

    print("\nSearch options:")
    print("1. By name")
    print("2. By age range")
    print("3. By course")
    print("4. By grade range")

    choice = input("Select search type (1-4): ")

    results = []

    if choice == "1":
        search_name = input("Enter name (partial match): ").lower()
        results = [s for s in student_database if search_name in s[0].lower()]

    elif choice == "2":
        min_age = int(input("Minimum age: "))
        max_age = int(input("Maximum age: "))
        results = [s for s in student_database if min_age <= s[1] <= max_age]

    elif choice == "3":
        search_course = input("Enter course name: ").lower()
        results = [s for s in student_database
                  if any(search_course in course.lower() for course in s[3])]

    elif choice == "4":
        if all(not s[2] for s in student_database):  # No grades recorded
            print("No grade data available")
            return

        min_grade = float(input("Minimum average grade: "))
        max_grade = float(input("Maximum average grade: "))
        results = []
        for s in student_database:
            if s[2]:  # Has grades
                avg = sum(s[2]) / len(s[2])
                if min_grade <= avg <= max_grade:
                    results.append(s)

    # Display results
    if results:
        print(f"\nFound {len(results)} student(s):")
        for student in results:
            name, age, grades, courses, contact = student
            avg_grade = sum(grades) / len(grades) if grades else 0
            print(f"- {name} (age {age}): {avg_grade:.1f} average, courses: {', '.join(courses)}")
    else:
        print("No students match your search criteria")

def analyze_performance():
    """Analyze class performance statistics"""
    if not student_database:
        print("No students in database")
        return

    # Collect all grades
    all_grades = []
    student_averages = []

    for student in student_database:
        if student[2]:  # Has grades
            student_avg = sum(student[2]) / len(student[2])
            student_averages.append((student[0], student_avg))
            all_grades.extend(student[2])

    if not all_grades:
        print("No grade data available")
        return

    # Calculate statistics
    class_avg = sum(all_grades) / len(all_grades)
    highest_grade = max(all_grades)
    lowest_grade = min(all_grades)

    # Grade distribution
    a_count = len([g for g in all_grades if g >= 90])
    b_count = len([g for g in all_grades if 80 <= g < 90])
    c_count = len([g for g in all_grades if 70 <= g < 80])
    d_count = len([g for g in all_grades if 60 <= g < 70])
    f_count = len([g for g in all_grades if g < 60])

    print(f"\n=== Performance Analysis ===")
    print(f"Total grades recorded: {len(all_grades)}")
    print(f"Class average: {class_avg:.1f}")
    print(f"Highest grade: {highest_grade}")
    print(f"Lowest grade: {lowest_grade}")
    print(f"Grade range: {highest_grade - lowest_grade}")

    print(f"\nGrade Distribution:")
    print(f"A (90-100): {a_count} ({a_count/len(all_grades)*100:.1f}%)")
    print(f"B (80-89):  {b_count} ({b_count/len(all_grades)*100:.1f}%)")
    print(f"C (70-79):  {c_count} ({c_count/len(all_grades)*100:.1f}%)")
    print(f"D (60-69):  {d_count} ({d_count/len(all_grades)*100:.1f}%)")
    print(f"F (0-59):   {f_count} ({f_count/len(all_grades)*100:.1f}%)")

    # Top performers
    if student_averages:
        student_averages.sort(key=lambda x: x[1], reverse=True)
        print(f"\nTop 3 Students:")
        for i, (name, avg) in enumerate(student_averages[:3], 1):
            print(f"{i}. {name}: {avg:.1f}")

def manage_courses():
    """Show course enrollment statistics"""
    if not student_database:
        print("No students in database")
        return

    # Count course enrollments
    course_counts = {}
    for student in student_database:
        for course in student[3]:
            course_counts[course] = course_counts.get(course, 0) + 1

    if not course_counts:
        print("No courses recorded")
        return

    print(f"\n=== Course Enrollment ===")
    sorted_courses = sorted(course_counts.items(), key=lambda x: x[1], reverse=True)

    for course, count in sorted_courses:
        print(f"{course}: {count} student(s)")

    print(f"\nTotal unique courses: {len(course_counts)}")
    print(f"Most popular course: {sorted_courses[0][0]} ({sorted_courses[0][1]} students)")

# Main program loop
while True:
    print(f"\n=== Student Database Menu ===")
    print("1. Add Student")
    print("2. Display All Students")
    print("3. Search Students")
    print("4. Performance Analysis")
    print("5. Course Management")
    print("6. Exit")

    choice = input("\nSelect option (1-6): ")

    if choice == "1":
        add_student()
    elif choice == "2":
        display_all_students()
    elif choice == "3":
        search_students()
    elif choice == "4":
        analyze_performance()
    elif choice == "5":
        manage_courses()
    elif choice == "6":
        print(f"\n=== Database Summary ===")
        print(f"Total students: {len(student_database)}")
        if student_database:
            total_grades = sum(len(s[2]) for s in student_database)
            print(f"Total grades recorded: {total_grades}")
        print("Goodbye!")
        break
    else:
        print("Invalid option. Please select 1-6.")
```

## Advanced List Techniques

### List Comprehensions with Multiple Conditions
```python
# Multiple conditions
numbers = range(1, 21)
special_numbers = [n for n in numbers
                  if n % 2 == 0    # even
                  and n % 3 == 0   # divisible by 3
                  and n > 5]       # greater than 5
print(special_numbers)  # [6, 12, 18]

# Nested list comprehension
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [num for row in matrix for num in row]
print(flattened)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### Working with Parallel Lists
```python
# Keep multiple lists in sync
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 22]
salaries = [50000, 60000, 45000]

# Sort all lists by age
sorted_data = sorted(zip(names, ages, salaries), key=lambda x: x[1])
names_sorted, ages_sorted, salaries_sorted = zip(*sorted_data)

print(list(names_sorted))    # ["Charlie", "Alice", "Bob"]
print(list(ages_sorted))     # [22, 25, 30]
print(list(salaries_sorted)) # [45000, 50000, 60000]
```

## Challenge Problems (Optional)

### Challenge 9.1: Matrix Operations
```python
# Create a 3x3 matrix using nested lists
# Implement functions for:
# - Matrix addition
# - Matrix multiplication
# - Transpose
# - Find determinant

matrix1 = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
matrix2 = [[9, 8, 7], [6, 5, 4], [3, 2, 1]]

# Your matrix operations here
```

### Challenge 9.2: Data Cleaning Pipeline
```python
# Given messy data, create a cleaning pipeline:
messy_data = [
    "  Alice Johnson, 25, Engineer  ",
    "Bob Smith,30,Teacher",
    "  Charlie Brown, , Designer",
    "Diana Prince,28,Doctor  ",
    "",
    "Eve Adams,32,Nurse"
]

# Clean the data:
# 1. Remove empty strings
# 2. Strip whitespace
# 3. Handle missing age data
# 4. Standardize format
# 5. Sort by age
```

## Lesson Summary

✅ **What we mastered:**
- List slicing with start, end, and step parameters
- List comprehensions for elegant data processing
- Nested lists for complex data structures
- Proper list copying (shallow vs deep)
- Combining lists with various methods
- Advanced list operations and techniques

✅ **Key takeaways:**
- Slicing creates new list objects
- List comprehensions are powerful but should remain readable
- Be careful with list references vs copies
- Nested lists enable complex data modeling
- zip() is great for working with parallel data
- Always consider performance with large lists

## Next Lesson Preview
In Lesson 10, we'll learn about **for loops** - the perfect companion to lists! You'll discover how to iterate through lists efficiently and perform operations on every element.

## Self-Check Questions
Before moving on, make sure you can answer:
1. What does `my_list[2:8:2]` return?
2. How do you create a list of squares using list comprehension?
3. What's the difference between shallow and deep copy?
4. How do you access the third element of the second row in a nested list?
5. What does `zip()` do with multiple lists?

Excellent work! You now have advanced list skills that will make your Python programming much more powerful and elegant. Ready to learn loops and make your list processing even more efficient!