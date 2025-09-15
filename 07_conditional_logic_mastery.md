# Lesson 7: Conditional Logic Mastery

## Learning Objectives
By the end of this lesson, you will:
- Master complex conditional logic patterns
- Use the ternary operator for concise conditions
- Understand short-circuit evaluation
- Handle edge cases and validation properly
- Write clean, readable conditional code
- Solve complex decision-making problems

## Advanced Conditional Patterns

### The Ternary Operator (Conditional Expression)
A concise way to write simple if/else statements:

```python
# Traditional if/else
age = 20
if age >= 18:
    status = "adult"
else:
    status = "minor"

# Ternary operator - same result in one line
status = "adult" if age >= 18 else "minor"

# General syntax: value_if_true if condition else value_if_false
```

#### Ternary Operator Examples
```python
# Simple examples
temperature = 75
weather = "warm" if temperature > 70 else "cool"

score = 85
grade = "pass" if score >= 60 else "fail"

number = 7
type_description = "even" if number % 2 == 0 else "odd"

# With user input
age = int(input("Enter age: "))
message = f"You can vote!" if age >= 18 else f"Wait {18 - age} more years to vote"
print(message)

# Nested ternary (use sparingly!)
score = 85
grade = "A" if score >= 90 else "B" if score >= 80 else "C" if score >= 70 else "F"
```

### Short-Circuit Evaluation
Python stops evaluating conditions as soon as the result is determined:

```python
# AND short-circuit: if first is False, second isn't checked
age = 15
has_license = True

# If age < 18 is True, has_license is never checked
if age >= 18 and has_license:
    print("Can drive")

# OR short-circuit: if first is True, second isn't checked
is_weekend = True
is_holiday = False

# If is_weekend is True, is_holiday is never checked
if is_weekend or is_holiday:
    print("No work today!")

# Practical use - avoiding errors
name = input("Enter name (or press Enter to skip): ")
if name and len(name) > 0:  # Check name exists before checking length
    print(f"Hello, {name}!")
```

### Chaining Comparisons
Python allows elegant comparison chaining:

```python
# Traditional way
score = 85
if score >= 80 and score < 90:
    print("B grade")

# Python's elegant way
if 80 <= score < 90:
    print("B grade")

# More examples
age = 25
if 18 <= age <= 65:
    print("Working age")

temperature = 72
if 68 <= temperature <= 78:
    print("Comfortable temperature")

# Multiple comparisons
x = 5
if 0 < x < 10 < 20:  # x is between 0 and 10, and 10 is less than 20
    print("x is in range")
```

## Advanced Validation Patterns

### Input Validation with Loops (Preview)
```python
# Robust input validation
while True:
    age_input = input("Enter your age (18-100): ")

    # Check if input is numeric
    if not age_input.isdigit():
        print("Please enter a valid number")
        continue

    age = int(age_input)

    # Check if age is in valid range
    if not (18 <= age <= 100):
        print("Age must be between 18 and 100")
        continue

    # If we get here, input is valid
    break

print(f"Valid age entered: {age}")
```

### Handling Multiple Input Types
```python
def validate_user_input():
    # Get and validate name
    while True:
        name = input("Enter your name: ").strip()
        if name and name.isalpha():
            break
        print("Name must contain only letters and not be empty")

    # Get and validate email
    while True:
        email = input("Enter email: ").strip()
        if "@" in email and "." in email and len(email) > 5:
            break
        print("Please enter a valid email address")

    # Get and validate age
    while True:
        try:
            age = int(input("Enter age (13-120): "))
            if 13 <= age <= 120:
                break
            else:
                print("Age must be between 13 and 120")
        except ValueError:
            print("Please enter a valid number")

    return name, email, age

# name, email, age = validate_user_input()
```

## Quick Practice Exercises

### Exercise 7.1: Ternary Operator Practice
```python
# Rewrite these if/else statements using ternary operators

# 1. Temperature check
temp = 65
# if temp > 70:
#     clothing = "shorts"
# else:
#     clothing = "pants"
clothing = "shorts" if temp > 70 else "pants"

# 2. Grade check
score = 75
# if score >= 60:
#     result = "passed"
# else:
#     result = "failed"
result = "passed" if score >= 60 else "failed"

# 3. Even/odd check
number = 42
# if number % 2 == 0:
#     parity = "even"
# else:
#     parity = "odd"
parity = "even" if number % 2 == 0 else "odd"

print(f"Temperature {temp}: wear {clothing}")
print(f"Score {score}: {result}")
print(f"Number {number}: {parity}")
```

### Exercise 7.2: Chained Comparisons
```python
# Use chained comparisons for these scenarios

# 1. Check if test score is a B grade (80-89)
score = 85
is_b_grade = 80 <= score <= 89
print(f"Score {score} is B grade: {is_b_grade}")

# 2. Check if temperature is comfortable (65-75°F)
temp = 70
is_comfortable = 65 <= temp <= 75
print(f"Temperature {temp}°F is comfortable: {is_comfortable}")

# 3. Check if age is teen (13-19)
age = 16
is_teen = 13 <= age <= 19
print(f"Age {age} is teen: {is_teen}")

# 4. Check if number is in range 1-100
number = 50
in_range = 1 <= number <= 100
print(f"Number {number} in range 1-100: {in_range}")
```

## Hands-On Coding Exercise

### Exercise 7.3: Advanced ATM System
```python
print("=== Advanced ATM System ===")
print()

# Initialize account
account_balance = 1000.00
daily_limit = 500.00
daily_withdrawn = 0.00
pin_attempts = 0
max_pin_attempts = 3
correct_pin = "1234"

# PIN validation
while pin_attempts < max_pin_attempts:
    pin = input("Enter your PIN: ")

    if pin == correct_pin:
        print("✅ PIN accepted")
        break
    else:
        pin_attempts += 1
        remaining_attempts = max_pin_attempts - pin_attempts
        if remaining_attempts > 0:
            print(f"❌ Incorrect PIN. {remaining_attempts} attempts remaining.")
        else:
            print("❌ Account locked due to too many incorrect attempts.")
            exit()

print(f"\nWelcome! Your current balance: ${account_balance:.2f}")

# Main ATM menu
while True:
    print(f"\n=== ATM Menu ===")
    print("1. Check Balance")
    print("2. Withdraw Money")
    print("3. Deposit Money")
    print("4. Exit")

    choice = input("\nSelect an option (1-4): ")

    if choice == "1":
        # Check Balance
        print(f"\nCurrent Balance: ${account_balance:.2f}")
        remaining_daily_limit = daily_limit - daily_withdrawn
        print(f"Remaining daily withdrawal limit: ${remaining_daily_limit:.2f}")

    elif choice == "2":
        # Withdraw Money
        print(f"\nCurrent balance: ${account_balance:.2f}")
        remaining_daily_limit = daily_limit - daily_withdrawn

        # Get withdrawal amount
        try:
            amount = float(input("Enter withdrawal amount: $"))
        except ValueError:
            print("❌ Invalid amount. Please enter a number.")
            continue

        # Validation checks
        if amount <= 0:
            print("❌ Withdrawal amount must be positive.")
        elif amount > account_balance:
            print(f"❌ Insufficient funds. Available balance: ${account_balance:.2f}")
        elif amount > remaining_daily_limit:
            print(f"❌ Daily limit exceeded. Remaining limit: ${remaining_daily_limit:.2f}")
        elif amount % 20 != 0:
            print("❌ Amount must be in multiples of $20.")
        else:
            # Successful withdrawal
            account_balance -= amount
            daily_withdrawn += amount
            print(f"✅ Withdrawal successful!")
            print(f"Amount withdrawn: ${amount:.2f}")
            print(f"New balance: ${account_balance:.2f}")
            print(f"Remaining daily limit: ${daily_limit - daily_withdrawn:.2f}")

    elif choice == "3":
        # Deposit Money
        try:
            amount = float(input("Enter deposit amount: $"))
        except ValueError:
            print("❌ Invalid amount. Please enter a number.")
            continue

        if amount <= 0:
            print("❌ Deposit amount must be positive.")
        elif amount > 10000:
            print("❌ Maximum deposit per transaction is $10,000.")
        else:
            # Successful deposit
            account_balance += amount
            print(f"✅ Deposit successful!")
            print(f"Amount deposited: ${amount:.2f}")
            print(f"New balance: ${account_balance:.2f}")

    elif choice == "4":
        # Exit
        print(f"\nThank you for using our ATM!")
        print(f"Final balance: ${account_balance:.2f}")
        break

    else:
        print("❌ Invalid option. Please select 1-4.")
```

### Exercise 7.4: Smart Home Security System
```python
print("=== Smart Home Security System ===")
print()

# System state
is_armed = False
is_home = True
door_sensors = {"front": False, "back": False, "garage": False}
motion_sensors = {"living_room": False, "kitchen": False, "bedroom": False}
security_code = "9876"

def check_sensors():
    """Check all sensors and return status"""
    any_door_open = any(door_sensors.values())
    any_motion = any(motion_sensors.values())
    return any_door_open, any_motion

def get_sensor_status():
    """Get current sensor readings from user"""
    print("\n--- Sensor Status Check ---")

    # Check door sensors
    for door in door_sensors:
        response = input(f"Is {door} door open? (yes/no): ").lower()
        door_sensors[door] = response in ["yes", "y", "true"]

    # Check motion sensors
    for room in motion_sensors:
        response = input(f"Motion detected in {room}? (yes/no): ").lower()
        motion_sensors[room] = response in ["yes", "y", "true"]

def display_status():
    """Display current system status"""
    print(f"\n=== System Status ===")
    print(f"Armed: {'Yes' if is_armed else 'No'}")
    print(f"Home: {'Yes' if is_home else 'No'}")

    print(f"\nDoor Sensors:")
    for door, is_open in door_sensors.items():
        status = "OPEN" if is_open else "CLOSED"
        print(f"  {door.title()}: {status}")

    print(f"\nMotion Sensors:")
    for room, has_motion in motion_sensors.items():
        status = "MOTION" if has_motion else "CLEAR"
        print(f"  {room.title().replace('_', ' ')}: {status}")

# Main system loop
while True:
    print(f"\n=== Smart Home Security ===")
    print("1. Arm System")
    print("2. Disarm System")
    print("3. Check Status")
    print("4. Update Sensors")
    print("5. Test Security")
    print("6. Exit")

    choice = input("\nSelect option (1-6): ")

    if choice == "1":
        # Arm System
        if is_armed:
            print("❌ System is already armed")
        else:
            code = input("Enter security code: ")
            if code == security_code:
                # Check if safe to arm
                any_door_open, any_motion = check_sensors()

                if any_door_open:
                    print("❌ Cannot arm: doors are open")
                    print("Close all doors before arming")
                elif any_motion and is_home:
                    response = input("Motion detected but you're home. Arm anyway? (yes/no): ")
                    if response.lower() in ["yes", "y"]:
                        is_armed = True
                        print("✅ System armed (home mode)")
                elif any_motion and not is_home:
                    print("❌ Cannot arm: motion detected and you're not home")
                    print("Wait for motion to clear or check the house")
                else:
                    is_armed = True
                    mode = "home" if is_home else "away"
                    print(f"✅ System armed ({mode} mode)")
            else:
                print("❌ Incorrect security code")

    elif choice == "2":
        # Disarm System
        if not is_armed:
            print("❌ System is not armed")
        else:
            code = input("Enter security code: ")
            if code == security_code:
                is_armed = False
                print("✅ System disarmed")
            else:
                print("❌ Incorrect security code")

    elif choice == "3":
        # Check Status
        display_status()

    elif choice == "4":
        # Update Sensors
        get_sensor_status()
        is_home = input("Are you currently home? (yes/no): ").lower() in ["yes", "y"]
        print("✅ Sensor status updated")

    elif choice == "5":
        # Test Security
        get_sensor_status()
        any_door_open, any_motion = check_sensors()

        print(f"\n=== Security Analysis ===")

        if is_armed:
            # Check for security breaches
            if any_door_open and not is_home:
                print("🚨 ALARM: Door opened while away and armed!")
            elif any_motion and not is_home:
                print("🚨 ALARM: Motion detected while away and armed!")
            elif any_door_open and is_home:
                print("⚠️ Notice: Door opened (home mode)")
            elif any_motion and is_home:
                print("✅ Motion detected (normal - home mode)")
            else:
                print("✅ All secure")
        else:
            # System not armed
            if any_door_open or any_motion:
                print("ℹ️ Activity detected but system not armed")
            else:
                print("✅ No activity detected")

    elif choice == "6":
        # Exit
        final_status = "ARMED" if is_armed else "DISARMED"
        print(f"\nGoodbye! System is {final_status}")
        break

    else:
        print("❌ Invalid option. Please select 1-6.")
```

## Complex Decision Trees

### Multi-Factor Authentication Example
```python
def authenticate_user():
    print("=== Multi-Factor Authentication ===")

    # Step 1: Username/Password
    username = input("Username: ")
    password = input("Password: ")

    if not (username == "admin" and password == "secure123"):
        print("❌ Invalid credentials")
        return False

    print("✅ Credentials accepted")

    # Step 2: Security Questions
    answer1 = input("What's your mother's maiden name? ").lower()
    if answer1 != "smith":
        print("❌ Incorrect security answer")
        return False

    # Step 3: Two-Factor Authentication
    import random
    code = str(random.randint(100000, 999999))
    print(f"📱 SMS code sent: {code}")  # In real life, this would be sent

    user_code = input("Enter 6-digit code: ")
    if user_code != code:
        print("❌ Incorrect verification code")
        return False

    # Step 4: Device Recognition
    device_id = input("Enter device ID: ")
    known_devices = ["laptop123", "phone456", "tablet789"]

    if device_id not in known_devices:
        trust_device = input("Unknown device. Do you want to trust it? (yes/no): ")
        if trust_device.lower() != "yes":
            print("❌ Device not trusted")
            return False
        else:
            known_devices.append(device_id)
            print("✅ Device added to trusted list")

    print("🎉 Authentication successful!")
    return True

# authenticate_user()
```

## Live Exercise: Advanced Grade Management System

We'll work through this together:

```python
print("=== Advanced Grade Management System ===")
print()

# Course configuration
course_name = input("Enter course name: ")
total_points_possible = 1000
grade_weights = {
    "quizzes": 0.20,      # 20%
    "assignments": 0.30,   # 30%
    "midterm": 0.20,      # 20%
    "final": 0.20,        # 20%
    "participation": 0.10  # 10%
}

print(f"\n=== {course_name} Grade Configuration ===")
for category, weight in grade_weights.items():
    print(f"{category.title()}: {weight:.0%}")

students = []

while True:
    print(f"\n=== Grade Management Menu ===")
    print("1. Add Student")
    print("2. View Student Grades")
    print("3. Calculate Final Grades")
    print("4. Grade Distribution")
    print("5. Exit")

    choice = input("\nSelect option (1-5): ")

    if choice == "1":
        # Add Student
        print(f"\n--- Adding New Student ---")
        student_name = input("Student name: ")

        # Get scores for each category
        scores = {}
        for category in grade_weights:
            while True:
                try:
                    if category == "participation":
                        max_score = 100
                    elif category in ["midterm", "final"]:
                        max_score = 200
                    else:
                        max_score = 100

                    score = float(input(f"{category.title()} score (0-{max_score}): "))

                    if 0 <= score <= max_score:
                        scores[category] = score
                        break
                    else:
                        print(f"Score must be between 0 and {max_score}")
                except ValueError:
                    print("Please enter a valid number")

        students.append({"name": student_name, "scores": scores})
        print(f"✅ Added {student_name} to gradebook")

    elif choice == "2":
        # View Student Grades
        if not students:
            print("❌ No students in gradebook")
            continue

        print(f"\n--- Student List ---")
        for i, student in enumerate(students, 1):
            print(f"{i}. {student['name']}")

        try:
            selection = int(input("Select student number: ")) - 1
            if 0 <= selection < len(students):
                student = students[selection]
                print(f"\n=== Grades for {student['name']} ===")

                total_weighted_score = 0
                for category, score in student['scores'].items():
                    weight = grade_weights[category]
                    weighted_score = score * weight
                    total_weighted_score += weighted_score

                    print(f"{category.title()}: {score} (weight: {weight:.0%}, contributes: {weighted_score:.1f})")

                # Calculate letter grade
                percentage = total_weighted_score
                if percentage >= 97:
                    letter = "A+"
                elif percentage >= 93:
                    letter = "A"
                elif percentage >= 90:
                    letter = "A-"
                elif percentage >= 87:
                    letter = "B+"
                elif percentage >= 83:
                    letter = "B"
                elif percentage >= 80:
                    letter = "B-"
                elif percentage >= 77:
                    letter = "C+"
                elif percentage >= 73:
                    letter = "C"
                elif percentage >= 70:
                    letter = "C-"
                elif percentage >= 67:
                    letter = "D+"
                elif percentage >= 63:
                    letter = "D"
                elif percentage >= 60:
                    letter = "D-"
                else:
                    letter = "F"

                print(f"\nFinal Score: {total_weighted_score:.1f} ({letter})")

                # Improvement suggestions
                if percentage < 70:
                    print("\n📚 Improvement needed:")
                    lowest_category = min(student['scores'], key=student['scores'].get)
                    print(f"Focus on {lowest_category} (lowest score: {student['scores'][lowest_category]})")

            else:
                print("❌ Invalid selection")
        except ValueError:
            print("❌ Please enter a valid number")

    elif choice == "3":
        # Calculate Final Grades
        if not students:
            print("❌ No students in gradebook")
            continue

        print(f"\n=== Final Grades for {course_name} ===")
        print(f"{'Name':<20} {'Score':<8} {'Grade':<5} {'Status'}")
        print("-" * 40)

        passing_count = 0
        total_score = 0

        for student in students:
            # Calculate weighted score
            weighted_score = sum(
                student['scores'][category] * grade_weights[category]
                for category in grade_weights
            )

            # Determine letter grade
            if weighted_score >= 97:
                letter = "A+"
            elif weighted_score >= 93:
                letter = "A"
            elif weighted_score >= 90:
                letter = "A-"
            elif weighted_score >= 87:
                letter = "B+"
            elif weighted_score >= 83:
                letter = "B"
            elif weighted_score >= 80:
                letter = "B-"
            elif weighted_score >= 77:
                letter = "C+"
            elif weighted_score >= 73:
                letter = "C"
            elif weighted_score >= 70:
                letter = "C-"
            elif weighted_score >= 67:
                letter = "D+"
            elif weighted_score >= 63:
                letter = "D"
            elif weighted_score >= 60:
                letter = "D-"
            else:
                letter = "F"

            status = "Pass" if weighted_score >= 60 else "Fail"
            if weighted_score >= 60:
                passing_count += 1

            total_score += weighted_score

            print(f"{student['name']:<20} {weighted_score:>6.1f}  {letter:<5} {status}")

        # Class statistics
        if students:
            avg_score = total_score / len(students)
            pass_rate = (passing_count / len(students)) * 100

            print(f"\n=== Class Statistics ===")
            print(f"Total students: {len(students)}")
            print(f"Average score: {avg_score:.1f}")
            print(f"Pass rate: {pass_rate:.1f}%")

    elif choice == "4":
        # Grade Distribution
        if not students:
            print("❌ No students in gradebook")
            continue

        grade_counts = {"A": 0, "B": 0, "C": 0, "D": 0, "F": 0}

        for student in students:
            weighted_score = sum(
                student['scores'][category] * grade_weights[category]
                for category in grade_weights
            )

            if weighted_score >= 90:
                grade_counts["A"] += 1
            elif weighted_score >= 80:
                grade_counts["B"] += 1
            elif weighted_score >= 70:
                grade_counts["C"] += 1
            elif weighted_score >= 60:
                grade_counts["D"] += 1
            else:
                grade_counts["F"] += 1

        print(f"\n=== Grade Distribution ===")
        for grade, count in grade_counts.items():
            percentage = (count / len(students)) * 100 if students else 0
            bar = "█" * (count * 2)  # Simple bar chart
            print(f"{grade}: {count:2d} students ({percentage:4.1f}%) {bar}")

    elif choice == "5":
        # Exit
        print(f"\n=== Final Report for {course_name} ===")
        if students:
            total_students = len(students)
            passing = sum(1 for student in students if sum(
                student['scores'][category] * grade_weights[category]
                for category in grade_weights
            ) >= 60)
            print(f"Total students processed: {total_students}")
            print(f"Students passing: {passing}")
            print(f"Pass rate: {(passing/total_students)*100:.1f}%")
        print("Goodbye!")
        break

    else:
        print("❌ Invalid option. Please select 1-5.")
```

## Best Practices Summary

### 1. Code Organization
- Keep conditions simple and readable
- Use meaningful variable names
- Group related conditions together
- Comment complex logic

### 2. Error Handling
- Always validate user input
- Provide clear error messages
- Have fallback options
- Test edge cases

### 3. Performance Considerations
- Use short-circuit evaluation
- Order conditions by likelihood
- Avoid repeating expensive calculations

### 4. Readability
- Use ternary operators for simple cases only
- Break complex conditions into variables
- Use consistent formatting
- Add comments for business logic

## Challenge Problems (Optional)

### Challenge 7.1: Smart Traffic Light System
Create a traffic light system that considers:
- Time of day (rush hour vs off-peak)
- Day of week (weekday vs weekend)
- Traffic sensors on each direction
- Emergency vehicle detection
- Pedestrian crossing requests

### Challenge 7.2: Dynamic Pricing System
Create a pricing system for a ride-sharing app that considers:
- Distance and time of trip
- Current demand (surge pricing)
- Time of day and day of week
- Weather conditions
- User loyalty level
- Special events in the area

## Lesson Summary

✅ **What we mastered:**
- Ternary operator for concise conditions
- Short-circuit evaluation optimization
- Chained comparisons for elegant range checks
- Complex validation patterns
- Advanced decision trees
- Real-world conditional logic applications

✅ **Key takeaways:**
- Conditional logic is the foundation of intelligent programs
- Always validate user input thoroughly
- Use the right tool: if/elif/else vs ternary vs chained comparisons
- Consider edge cases and error conditions
- Write readable code that others can understand
- Test your logic with different scenarios

## Course Milestone Achieved! 🎉
**Congratulations!** You have now **mastered conditional logic** - one of the most important programming concepts. You can make your programs intelligent and responsive to different situations.

## Next Steps in Your Python Journey
With conditional logic mastered, you're ready to:
1. **Lists and Data Structures** (Lesson 8) - Store and organize multiple pieces of data
2. **Loops** (Lessons 10-11) - Repeat actions efficiently
3. **Functions** (Lessons 12-13) - Create reusable code blocks

## Self-Check: Conditional Logic Mastery
You have mastered conditional logic if you can:
- ✅ Write clean if/elif/else chains
- ✅ Use comparison and logical operators correctly
- ✅ Validate user input effectively
- ✅ Handle edge cases and errors
- ✅ Choose the right conditional pattern for each situation
- ✅ Debug conditional logic problems
- ✅ Create complex decision-making programs

**Perfect!** You're now ready to tackle more advanced Python concepts. The foundation you've built with data types, operations, input/output, and conditional logic will serve you well in everything that follows.

Keep coding and practicing - you're doing great! 🚀