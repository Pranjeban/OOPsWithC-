# Assignment 3 Solutions

## 3.1 Employee Class for Salary Calculation

This program defines an `Employee` class to manage the salary and work hours of an employee. It includes methods to adjust the salary based on certain conditions.

```cpp
#include <iostream>
using namespace std;

class Employee {
private:
    float salary;
    int workHours;

public:
    void getInfo(float sal, int hours) {
        salary = sal;
        workHours = hours;
    }

    void AddSal() {
        if (salary < 500) {
            salary += 10;
        }
    }

    void AddWork() {
        if (workHours > 6) {
            salary += 5;
        }
    }

    void printSalary() const {
        cout << "Final Salary: " << salary << endl;
    }
};

int main() {
    Employee emp;
    emp.getInfo(450, 7);
    emp.AddSal();
    emp.AddWork();
    emp.printSalary();
    return 0;
}
```

## Task 3.2: Handling Multiple Employee Objects
This task extends the `Employee` class from Task 3.1 to handle multiple employees, specifically 10 managers, using the concept of arrays of objects. The program demonstrates how to create an array of `Employee` objects, initialize them with data, and then apply operations on each object to calculate and print their final salaries.
```cpp
#include <iostream>
using namespace std;

class Employee {
private:
    float salary;
    int workHoursPerDay;

public:
    // Function to get the salary and number of work hours per day
    void getInfo(float sal, int hours) {
        salary = sal;
        workHoursPerDay = hours;
    }

    // Function to add Rs.10 to salary if it is less than Rs.500
    void AddSal() {
        if (salary < 500) {
            salary += 10;
        }
    }

    // Function to add Rs.5 to salary if work hours per day are more than 6
    void AddWork() {
        if (workHoursPerDay > 6) {
            salary += 5;
        }
    }

    // Function to print the final salary
    void printSalary() {
        cout << "Final Salary: Rs." << salary << endl;
    }
};

int main() {
    Employee managers[10]; // Array to store 10 Employee objects
    float salary;
    int hours;

    // Loop to get information for each manager and apply salary modifications
    for (int i = 0; i < 10; i++) {
        cout << "Enter salary and work hours per day for manager " << (i + 1) << ": ";
        cin >> salary >> hours;
        managers[i].getInfo(salary, hours);
        managers[i].AddSal();
        managers[i].AddWork();
    }

    // Loop to print the final salary of each manager
    for (int i = 0; i < 10; i++) {
        cout << "Manager " << (i + 1) << ": ";
        managers[i].printSalary();
    }

    return 0;
}
```
# Task 3.3: Addition of Time Using Objects

## Description
This task involves writing a C++ program that performs the addition of time in hours and minutes. It demonstrates the use of objects as function arguments to facilitate the addition operation. The program defines a `Time` class that encapsulates hours and minutes and provides a method to add two `Time` objects together.


```cpp
#include <iostream>
using namespace std;

class Time {
private:
    int hours;
    int minutes;

public:
    Time() : hours(0), minutes(0) {} // Default constructor

    // Constructor to initialize hours and minutes
    Time(int h, int m) : hours(h), minutes(m) {}

    // Function to add two Time objects
    void addTime(Time t1, Time t2) {
        minutes = t1.minutes + t2.minutes;
        hours = t1.hours + t2.hours + (minutes / 60);
        minutes = minutes % 60;
    }

    // Function to display the time in hours and minutes
    void displayTime() {
        cout << "Total Time = " << hours << " hours and " << minutes << " minutes" << endl;
    }
};

int main() {
    Time T1(2, 45), T2(3, 30), T3;

    T3.addTime(T1, T2); // Adding T1 and T2
    T3.displayTime(); // Displaying the result

    return 0;
}
```
## Task 3.4: Implementing Employee Performance Evaluation

This task involves extending the `Employee` class to include a method for evaluating employee performance. The performance is evaluated based on the number of hours worked per day and the current salary. Employees meeting certain criteria receive a performance bonus.


```cpp
#include <iostream>
using namespace std;

class Employee {
private:
    float salary;
    int workHoursPerDay;
    float performanceBonus;

public:
    // Existing methods not shown for brevity

    // New method to evaluate performance and add bonus
    void evaluatePerformance() {
        if (workHoursPerDay > 8 && salary < 1000) {
            performanceBonus = 100; // Flat bonus for simplicity
        } else {
            performanceBonus = 0;
        }
    }

    // Modified function to print the final salary including performance bonus
    void printSalary() {
        cout << "Final Salary including Performance Bonus: Rs." << (salary + performanceBonus) << endl;
    }
};

```

## Task 3.5: Enhancing the Time Class with Subtraction Capability

This task extends the `Time` class by adding a method to subtract one `Time` object from another, handling cases where the result might involve negative time values.

```cpp
#include <iostream>
using namespace std;

class Time {
private:
    int hours;
    int minutes;

public:
    // Existing constructors and methods not shown for brevity

    // Function to subtract two Time objects
    void subtractTime(Time t1, Time t2) {
        int t1_minutes = t1.hours * 60 + t1.minutes;
        int t2_minutes = t2.hours * 60 + t2.minutes;
        int diff = t1_minutes - t2_minutes;

        if (diff < 0) {
            cout << "Time difference cannot be negative!" << endl;
            return;
        }

        hours = diff / 60;
        minutes = diff % 60;
    }

    // Existing displayTime method not shown for brevity
};
```

# Task 3.6: Creating a Simple Calculator Class

This task involves creating a `Calculator` class that can perform basic arithmetic operations such as addition, subtraction, multiplication, and division.


```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    // Function to add two numbers
    float add(float a, float b) {
        return a + b;
    }

    // Function to subtract two numbers
    float subtract(float a, float b) {
        return a - b;
    }

    // Function to multiply two numbers
    float multiply(float a, float b) {
        return a * b;
    }

    // Function to divide two numbers
    float divide(float a, float b) {
        if (b == 0) {
            cout << "Error: Division by zero!" << endl;
            return 0;
        }
        return a / b;
    }
};

int main() {
    Calculator calc;
    cout << "Addition: " << calc.add(10, 5) << endl;
    cout << "Subtraction: " << calc.subtract(10, 5) << endl;
    cout << "Multiplication: " << calc.multiply(10, 5) << endl;
    cout << "Division: " << calc.divide(10, 5) << endl;
    return 0;
}
```