# Python Learning Exercises and Projects

## Overview
This document contains comprehensive exercises and projects organized by skill level and concept. Each exercise includes clear instructions, expected outcomes, and learning objectives.

## Exercise Categories

### 🟢 Beginner Exercises (Lessons 1-4)
Basic programming concepts and syntax

### 🟡 Intermediate Exercises (Lessons 5-9)
Conditional logic and data structures

### 🟠 Advanced Exercises (Lessons 10+)
Loops, functions, and complex problem solving

### 🔴 Challenge Projects
Real-world applications combining multiple concepts

---

## 🟢 Beginner Exercises

### Exercise B1: Personal Information Processor
**Concepts**: Variables, data types, input/output, basic operations

**Task**: Create a program that collects personal information and generates a formatted profile.

**Requirements**:
- Get user's name, age, height (in inches), favorite color, and hometown
- Calculate age in months and days
- Convert height to feet and inches
- Display a nicely formatted profile card
- Include validation for reasonable age ranges (0-120)

**Expected Output**:
```
=== Personal Profile ===
Name: Alice Johnson
Age: 25 years (300 months, 9,125 days)
Height: 5'8" (68 inches)
Favorite Color: Blue
Hometown: Seattle
Profile Complete!
```

**Learning Objectives**:
- Practice with all basic data types
- User input validation
- Mathematical calculations
- String formatting

---

### Exercise B2: Shopping Calculator
**Concepts**: Variables, operations, conditional logic basics

**Task**: Build a shopping calculator that handles multiple items with tax and discounts.

**Requirements**:
- Allow input of 5 different items with prices
- Calculate subtotal
- Apply 8.5% tax
- Apply 10% discount if subtotal > $100
- Display itemized receipt
- Show savings if discount applied

**Bonus Features**:
- Handle invalid prices (negative numbers)
- Add tip calculation (15%, 18%, or 20%)
- Calculate change from amount paid

---

### Exercise B3: Unit Converter Suite
**Concepts**: Mathematical operations, conditionals, input validation

**Task**: Create a multi-unit converter with a menu system.

**Conversions to Include**:
- Temperature (F ↔ C ↔ K)
- Length (inches ↔ feet ↔ meters ↔ kilometers)
- Weight (pounds ↔ kilograms ↔ ounces)
- Volume (cups ↔ liters ↔ gallons)

**Features**:
- Menu-driven interface
- Input validation
- Formatted output with appropriate decimal places
- Option to perform multiple conversions

---

## 🟡 Intermediate Exercises

### Exercise I1: Grade Management System
**Concepts**: Lists, conditionals, basic loops, data processing

**Task**: Build a comprehensive grade management system for teachers.

**Core Features**:
- Add students and their grades
- Calculate individual and class averages
- Assign letter grades (A, B, C, D, F)
- Generate class statistics
- Find top and bottom performers
- Create grade distribution report

**Advanced Features**:
- Weight different assignment types (tests 40%, homework 30%, participation 30%)
- Handle dropped lowest grade
- Predict final grade based on current performance
- Generate improvement recommendations

---

### Exercise I2: Inventory Management System
**Concepts**: Lists, dictionaries (preview), conditional logic, data validation

**Task**: Create a simple inventory system for a small business.

**Required Functionality**:
- Add new items with name, quantity, price
- Update item quantities (restock/sale)
- Search for items by name
- Display inventory summary
- Calculate total inventory value
- Alert for low stock items
- Generate sales reports

**Data to Track**:
- Item name, quantity, unit price, supplier, reorder level

---

### Exercise I3: Student Database with Search
**Concepts**: Nested lists, advanced conditionals, string processing

**Task**: Build a student information system with search capabilities.

**Student Information**:
- Name, age, grade level, GPA, courses, contact info

**Required Features**:
- Add/remove students
- Search by name (partial matching)
- Filter by grade level or GPA range
- Display formatted student lists
- Calculate academic statistics
- Generate transcripts

**Advanced Features**:
- Sort students by different criteria
- Export data to formatted text files
- Handle duplicate names
- Course enrollment tracking

---

## 🟠 Advanced Exercises

### Exercise A1: Weather Data Analyzer
**Concepts**: File processing, data analysis, loops, statistics

**Task**: Process and analyze weather data from multiple sources.

**Data Processing**:
- Daily temperature, humidity, precipitation data
- Calculate weekly/monthly averages
- Identify trends and patterns
- Generate weather summaries
- Create simple visualizations using text charts

**Analysis Features**:
- Temperature extremes and ranges
- Precipitation totals and averages
- Humidity patterns
- Heat index calculations
- Weather pattern predictions

---

### Exercise A2: Text Analysis Tool
**Concepts**: String processing, dictionaries, file handling, algorithms

**Task**: Create a comprehensive text analysis tool.

**Analysis Features**:
- Word frequency counting
- Sentence and paragraph analysis
- Reading level assessment
- Keyword extraction
- Text summarization
- Language pattern detection

**Input Sources**:
- User text input
- Text file processing
- Multiple document comparison

---

### Exercise A3: Personal Finance Tracker
**Concepts**: Data persistence, calculations, reporting, user interface

**Task**: Build a personal finance management system.

**Core Features**:
- Income and expense tracking
- Category-based budgeting
- Monthly/yearly reports
- Savings goal tracking
- Bill reminder system
- Financial health scoring

**Advanced Features**:
- Trend analysis and predictions
- Budget variance reporting
- Investment tracking
- Tax calculation assistance
- Export to spreadsheet format

---

## 🔴 Challenge Projects

### Project C1: Library Management System
**Concepts**: Object-oriented programming, file I/O, search algorithms, data modeling

**Task**: Create a complete library management system.

**System Components**:
- Book catalog with ISBN, title, author, genre, availability
- Member registration and management
- Check-out/check-in system with due dates
- Fine calculation for overdue books
- Search and filter capabilities
- Report generation

**Advanced Features**:
- Reservation system for popular books
- Reading recommendation engine
- Inventory management for librarians
- Statistics and analytics dashboard
- Multiple library branch support

**Technical Requirements**:
- Data persistence (save/load from files)
- Error handling and validation
- User-friendly command-line interface
- Modular code structure

---

### Project C2: Student Course Registration System
**Concepts**: Complex data relationships, scheduling algorithms, constraint handling

**Task**: Build a university course registration system.

**Core Functionality**:
- Course catalog with prerequisites, schedules, capacity
- Student profiles with academic history
- Registration with conflict detection
- Waitlist management
- Grade recording and transcript generation
- Academic advisor recommendations

**Complex Features**:
- Schedule optimization
- Prerequisite checking
- Credit hour limitations
- Time conflict resolution
- Degree requirement tracking
- Registration priority systems

---

### Project C3: Small Business POS System
**Concepts**: Real-time processing, inventory integration, financial calculations

**Task**: Create a point-of-sale system for retail businesses.

**System Features**:
- Product catalog with barcodes and prices
- Real-time inventory updates
- Customer management
- Sales transaction processing
- Receipt generation
- Daily sales reporting

**Advanced Capabilities**:
- Discount and promotion handling
- Tax calculation by jurisdiction
- Employee management and permissions
- Sales analytics and trending
- Integration with inventory system
- Customer loyalty program

---

## Live Coding Exercises

### Live Exercise 1: Real-Time Chat Analyzer
**Duration**: 45-60 minutes
**Concepts**: String processing, real-time data, pattern recognition

Work together to build a system that analyzes chat messages for:
- Sentiment analysis (positive/negative)
- Keyword trending
- User activity patterns
- Message filtering and moderation
- Conversation summaries

### Live Exercise 2: Game Score Tracker
**Duration**: 30-45 minutes
**Concepts**: Data structures, game logic, statistics

Build a system to track scores across multiple games:
- Multiple game support (different scoring systems)
- Player statistics and rankings
- Tournament bracket management
- Performance analytics
- Achievement system

### Live Exercise 3: Recipe Calculator
**Duration**: 30-45 minutes
**Concepts**: Mathematical operations, unit conversions, user interface

Create a cooking assistant that:
- Scales recipes up or down
- Converts between measurement units
- Calculates nutritional information
- Suggests ingredient substitutions
- Manages shopping lists

---

## Project Guidelines

### Code Quality Standards
- Use meaningful variable and function names
- Include comments explaining complex logic
- Handle errors gracefully with try/except blocks
- Validate all user input
- Follow PEP 8 style guidelines

### Testing Requirements
- Test with various input types and ranges
- Include edge cases (empty data, extreme values)
- Verify calculations with known examples
- Test error handling paths

### Documentation Standards
- Include a README with setup and usage instructions
- Document all functions and classes
- Provide example usage and sample data
- List any assumptions or limitations

### Submission Format
- Well-organized code files
- Sample input/output files
- Test data sets
- User manual or help documentation

---

## Assessment Rubrics

### Beginner Projects (🟢)
- **Functionality (40%)**: Does it work as specified?
- **Code Quality (30%)**: Clean, readable, well-structured?
- **User Experience (20%)**: Easy to use and understand?
- **Problem Solving (10%)**: Creative solutions to challenges?

### Intermediate Projects (🟡)
- **Functionality (35%)**: Complete feature implementation
- **Code Quality (25%)**: Professional coding standards
- **Data Handling (20%)**: Proper data management and validation
- **User Interface (10%)**: Intuitive and user-friendly
- **Innovation (10%)**: Creative enhancements or solutions

### Advanced Projects (🟠)
- **System Design (25%)**: Well-architected solution
- **Code Quality (25%)**: Professional-grade code
- **Functionality (25%)**: Complete and robust features
- **Performance (15%)**: Efficient algorithms and data usage
- **Innovation (10%)**: Creative problem-solving approaches

### Challenge Projects (🔴)
- **Architecture (30%)**: Scalable, maintainable design
- **Implementation (25%)**: Complete, robust functionality
- **Code Quality (20%)**: Professional standards throughout
- **User Experience (15%)**: Polished, intuitive interface
- **Innovation (10%)**: Creative solutions and enhancements

---

## Getting Help

### Before Starting Any Exercise
1. Read through all requirements carefully
2. Plan your approach and data structures
3. Identify which concepts you'll need to use
4. Break the problem into smaller, manageable parts

### While Working
1. Test frequently with small examples
2. Use print statements to debug logic
3. Validate inputs early and often
4. Don't hesitate to ask questions about requirements

### Code Review Checklist
- Does the code handle all specified requirements?
- Are error cases handled appropriately?
- Is the user interface clear and helpful?
- Is the code readable and well-commented?
- Have you tested with various inputs?

Remember: The goal is learning, not just completing assignments. Focus on understanding the concepts and building good programming habits!