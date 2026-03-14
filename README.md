# Python Lab Exam Solutions

This document contains the **problem statements and Python solutions**
for the Python Lab Exam.

------------------------------------------------------------------------

## Q1. Check three consecutive increasing numbers in a list

**Problem Statement:**\
Write a Python program to check if a list contains three consecutive
increasing numbers. If yes, print all such sequences.

``` python
lst = [1, 2, 3, 5, 6, 7, 9]

for i in range(len(lst) - 2):
    if lst[i] + 1 == lst[i+1] and lst[i] + 2 == lst[i+2]:
        print(lst[i], lst[i+1], lst[i+2])
```

------------------------------------------------------------------------

## Q2. Electricity Bill Calculation System

**Problem Statement:**\
Write a Python program to calculate the monthly electricity bill of a
consumer using the following tariff: 
- First 100 units → ₹1.5/unit\
- Next 100 units → ₹2.5/unit\
- Remaining units → ₹4.0/unit\
- Fixed meter charge → ₹50
Use conditional statements to compute the bill. 
Use a function to calculate the total bill. 
Display a formatted bill summary.

``` python
def calculate_bill(units):
    bill = 0
    if units <= 100:
        bill = units * 1.5
    elif units <= 200:
        bill = (100 * 1.5) + (units - 100) * 2.5
    else:
        bill = (100 * 1.5) + (100 * 2.5) + (units - 200) * 4
    bill += 50
    return bill

name = input("Enter consumer name: ")
units = int(input("Enter units consumed: "))

print("Total Bill:", calculate_bill(units))
```

------------------------------------------------------------------------

## Q3. Find subarrays whose sum equals target

**Problem Statement:**\
Given a list of positive numbers and a target sum, find all subarrays
whose sum equals the target.

``` python
arr = [1,2,3,4,5]
target = 5

for i in range(len(arr)):
    s = 0
    for j in range(i, len(arr)):
        s += arr[j]
        if s == target:
            print(arr[i:j+1])
```

------------------------------------------------------------------------

## Q4. Student Result Processing System

**Problem Statement:**\
Accept marks of students in three subjects, calculate total and average
marks, assign grades using match-case, and display the student with the
highest average.
- Requirements : 
- Accept marks of N students in three subjects and store them in a list. 
- Calculate total and average marks for each student. 
- Assign grades using match-case: 
- -  Average ≥ 90 → Grade A 
- - Average ≥ 75 → Grade B 
- - Average ≥ 60 → Grade C 
- -  Else → Grade D 
-  Display the details of the student who scored the highest average. 


``` python
n = int(input("Enter number of students: "))
students = []

for i in range(n):
    m1 = int(input("Marks1: "))
    m2 = int(input("Marks2: "))
    m3 = int(input("Marks3: "))

    total = m1 + m2 + m3
    avg = total / 3

    match True:
        case _ if avg >= 90:
            grade = "A"
        case _ if avg >= 75:
            grade = "B"
        case _ if avg >= 60:
            grade = "C"
        case _:
            grade = "D"

    students.append((avg, grade))

top = max(students)
print("Highest Average:", top[0], "Grade:", top[1])
```

------------------------------------------------------------------------

## Q5. Fibonacci Sequence

**Problem Statement:**\
Write a Python program to print the Fibonacci sequence up to n.

``` python
n = int(input("Enter n: "))
a, b = 0, 1

for i in range(n):
    print(a, end=" ")
    a, b = b, a + b
```

------------------------------------------------------------------------

## Q6. Banking System Using OOP

**Problem Statement:**\
Create a BankAccount class with account number, name, and balance.
Implement methods to deposit, withdraw, and display balance.

- Requirements:
- Create a BankAccount class with account number, name, and balance.
- Implement methods to deposit, withdraw, and display balance.
-  Ensure withdrawal does not exceed balance using conditional statements.
-   reate at least two account objects and demonstrate all operations.

``` python
class BankAccount:
    def __init__(self, acc_no, name, balance):
        self.acc_no = acc_no
        self.name = name
        self.balance = balance

    def deposit(self, amt):
        self.balance += amt

    def withdraw(self, amt):
        if amt > self.balance:
            print("Insufficient balance")
        else:
            self.balance -= amt

    def display(self):
        print(self.acc_no, self.name, self.balance)

a1 = BankAccount(101, "Subha", 5000)
a1.deposit(1000)
a1.withdraw(2000)
a1.display()
```

------------------------------------------------------------------------

## Q7. Sum of Digits

**Problem Statement:**\
Create a function `find_sum_of_digit()` to find the sum of digits of a
given number.

``` python
def find_sum_of_digit(n):
    s = 0
    while n > 0:
        s += n % 10
        n //= 10
    return s

num = int(input("Enter number: "))
print("Sum:", find_sum_of_digit(num))
```

------------------------------------------------------------------------

## Q8. String Encryption and Decryption

**Problem Statement:**\
Write a Python program to print sum of the following factorial series:
1!+2!+3!+4!+ ⋯ + 𝑛! 

- Requirements:
- Accept n (number of terms) from the user.
- Use a function to calculate factorial.
- Print each factorial term in the series.
- Calculate and display the sum of the series.
``` python
def factorial(num):
    fact = 1
    for i in range(1, num + 1):
        fact *= i
    return fact


def factorial_series(n):
    total = 0
    print("Series:", end=" ")

    for i in range(1, n + 1):
        f = factorial(i)
        print(f, end=" ")
        total += f

    print("\nSum of the series:", total)


n = int(input("Enter number of terms: "))
factorial_series(n)
```

------------------------------------------------------------------------

## Q9. Factorial Function

**Problem Statement:**\
Create a function `find_factorial()` to calculate factorial of a number.

``` python
def find_factorial(n):
    f = 1
    for i in range(1, n + 1):
        f *= i
    return f

num = int(input("Enter number: "))
print("Factorial:", find_factorial(num))
```

------------------------------------------------------------------------

## Q10. Inventory Management System

**Problem Statement:**\
- Requirements:
- Store product ID, name, price, and quantity using a list of objects.
- Apply a 10% discount if quantity > 50.
-  Allow searching for a product using product ID.
-   isplay updated product details. 
``` python
class Product:
    def __init__(self, pid, name, price, qty):
        self.pid = pid
        self.name = name
        self.price = price
        self.qty = qty

    def discount(self):
        if self.qty > 50:
            self.price *= 0.9

    def display(self):
        print(self.pid, self.name, self.price, self.qty)

products = [
    Product(1, "Pen", 10, 60),
    Product(2, "Book", 50, 30)
]

pid = int(input("Enter product id: "))

for p in products:
    if p.pid == pid:
        p.discount()
        p.display()
```

------------------------------------------------------------------------

## Q11. Strong Number

**Problem Statement:**\
Create a function `check_strong_number()` to check whether a number is a
strong number.

``` python
import math

def check_strong_number(n):
    temp = n
    s = 0

    while n > 0:
        d = n % 10
        s += math.factorial(d)
        n //= 10

    if s == temp:
        print("Strong Number")
    else:
        print("Not Strong Number")

num = int(input("Enter number: "))
check_strong_number(num)
```

------------------------------------------------------------------------

## Q12. Library Management System Using OOP

**Problem Statement:**\
Create a Book class with book ID, title, and availability status. Allow
issuing and returning books.
- Requirements: 
- - Create a Book class with book ID, title, and availability status. 
- - Allow issuing and returning books. 
- - Prevent issuing unavailable books using conditions. 
- - Display current book status.

``` python
class Book:
    def __init__(self, bid, title):
        self.bid = bid
        self.title = title
        self.available = True

    def issue(self):
        if self.available:
            self.available = False
            print("Book Issued")
        else:
            print("Not Available")

    def return_book(self):
        self.available = True

    def status(self):
        print(self.bid, self.title, self.available)

b1 = Book(1, "Python")
b1.issue()
b1.status()
```

------------------------------------------------------------------------

## Q13. Count uppercase, lowercase, digits, and special characters

**Problem Statement:**\
Given a string, count uppercase letters, lowercase letters, digits, and
special characters.

``` python
s = input("Enter string: ")

upper = lower = digit = special = 0

for ch in s:
    if ch.isupper():
        upper += 1
    elif ch.islower():
        lower += 1
    elif ch.isdigit():
        digit += 1
    else:
        special += 1

print("Upper:", upper)
print("Lower:", lower)
print("Digits:", digit)
print("Special:", special)
```

------------------------------------------------------------------------

## Q14. Employee Payroll System

**Problem Statement:**\
Requirements: 
-  Accept employee ID, name, and basic salary. 
- Calculate: 
- -  HRA = 20% of basic 
- -  DA = 10% of basic 
-  Deduct tax: 
- -  Salary > ₹50,000 → 10% 
- Display net salary using a function.

``` python
def net_salary(basic):
    hra = basic * 0.20
    da = basic * 0.10
    gross = basic + hra + da

    tax = 0
    if gross > 50000:
        tax = gross * 0.10

    return gross - tax

basic = float(input("Enter basic salary: "))
print("Net Salary:", net_salary(basic))
```

------------------------------------------------------------------------

## Q15. Sum of Prime Numbers

**Problem Statement:**\
Write a Python program to find the sum of all prime numbers between 1
and n.

``` python
n = int(input("Enter n: "))
sum_prime = 0

for num in range(2, n + 1):
    prime = True
    for i in range(2, num):
        if num % i == 0:
            prime = False
            break
    if prime:
        sum_prime += num

print("Sum:", sum_prime)
```

------------------------------------------------------------------------

## Q16. Online Shopping Cart System

**Problem Statement:**\
Design a shopping cart program. 
- Requirements: 
- -  Display menu using match-case. 
- -  Allow adding and removing items from a list. 
- -  Calculate total bill using loops. 
- -  Exit only when the user chooses to quit.

``` python
cart = []

while True:
    print("1 Add Item")
    print("2 Remove Item")
    print("3 Show Cart")
    print("4 Exit")

    ch = int(input("Choice: "))

    match ch:
        case 1:
            item = input("Item: ")
            cart.append(item)

        case 2:
            item = input("Remove item: ")
            if item in cart:
                cart.remove(item)

        case 3:
            print(cart)

        case 4:
            break
```

------------------------------------------------------------------------

## Q17. Palindrome Number

**Problem Statement:**\
Write a Python program to check whether a number is palindrome.

``` python
num = int(input("Enter number: "))

temp = num
rev = 0

while num > 0:
    rev = rev * 10 + num % 10
    num //= 10

if temp == rev:
    print("Palindrome")
else:
    print("Not Palindrome")
```

------------------------------------------------------------------------

## Q18. Hotel Room Booking System Using OOP

**Problem Statement:**\
Design a hotel booking system. 
- Requirements: 
- -  Create a Room class with room number, type, and price. 
- -  Book rooms based on availability. 
- -  Calculate total bill using conditional logic. 
- -  Display booking summary.

``` python
class Room:
    def __init__(self, no, type, price):
        self.no = no
        self.type = type
        self.price = price
        self.booked = False

    def book(self):
        if not self.booked:
            self.booked = True
            print("Room booked")
        else:
            print("Not available")

r1 = Room(101, "AC", 2000)
r1.book()
```

------------------------------------------------------------------------

## Q19. Remove duplicates from a list

**Problem Statement:**\
Write a Python program to remove duplicates from a list.

``` python
lst = [1,2,2,3,4,4,5]
unique = list(set(lst))
print(unique)
```

------------------------------------------------------------------------

## Q20. Bus Fare Calculation

**Problem Statement:**\
Write a Python program to calculate the fare for a passenger using a city bus 
service. 
Problem Requirements: 
1. Accept the following inputs from the user: 
-  Passenger name 
- Passenger age 
-  Distance travelled (in kilometers) 
2. Fare calculation rules: 
  - Fare rate is ₹2.5 per kilometer 
  - Calculate the total fare based on distance travelled 
3. Use a user-defined function to calculate the final fare.
- Output Requirements: 
- -  Display the passenger name 
- -  Display the distance travelled 
- -  Display the total fare amount

``` python
def calculate_fare(distance):
    return distance * 2.5

name = input("Passenger name: ")
distance = float(input("Distance travelled: "))

fare = calculate_fare(distance)

print("Name:", name)
print("Distance:", distance)
print("Total Fare:", fare)
```
