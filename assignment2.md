# Assignment 2 Solutions

This document outlines the solutions for the given programming tasks, focusing on various aspects of C++ programming, including loops, functions, default arguments, dynamic memory allocation, function overloading, and mathematical calculations.

## 2.1 Investment Equation Program

This program calculates the future value of an investment over a range of principal amounts, interest rates, and years.


```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    for (int P = 1000; P <= 10000; P += 1000) {
        for (double r = 0.10; r <= 0.20; r += 0.01) {
            cout << "P = " << P << ", r = " << r << endl;
            for (int n = 1; n <= 10; ++n) {
                double V = P * pow(1 + r, n);
                cout << "n = " << n << ", V = " << V << endl;
            }
            cout << endl;
        }
    }
    return 0;
}
```
## 2.2 Function with Default Arguments
Function with Default Arguments

```cpp
#include <iostream>
using namespace std;

void display(char c, int i, float f, double d = 6.28) {
    cout << c << " " << i << " " << f << " " << d << endl;
}

int main() {
    display('A', 1, 2.3f, 4.56);
    display('B', 2, 3.4f); // Uses default for double
    // Note: The attempt to call display with only two arguments will result in a compilation error.
    return 0;
}
```

## 2.3 Power Funtion
```cpp
#include <iostream>
#include <cmath>
using namespace std;

double power(double m, int n = 2) {
    return pow(m, n);
}

int main() {
    double m;
    int n;
    cout << "Enter m and n: ";
    cin >> m >> n;
    cout << "Result: " << power(m, n) << endl;
    cout << "Square of m: " << power(m) << endl; // Uses default n=2
    return 0;
}
```

## 2.4 Vector Creation with New Operator

This program shows how to dynamically allocate memory for an array using the `new` operator.


```cpp
#include <iostream>
using namespace std;

int* createVector(int M) {
    return new int[M];
}

int main() {
    int M = 5;
    int* myVector = createVector(M);
    // Remember to delete the allocated memory
    delete[] myVector;
    return 0;
}
```

## 2.5 Function Overloading for Power Calculation

This section demonstrates the use of function overloading in C++ to calculate the power of a number. Function overloading allows multiple functions to have the same name with different parameters. In this case, we create two versions of a `power` function: one that takes a `double` as the base and an `int` for the exponent, and another that takes both the base and the exponent as `int`. This allows for flexibility in handling different data types for mathematical operations.

### Code


```cpp
#include <iostream>
#include <cmath>
using namespace std;

// Function to calculate power when base is double
double power(double m, int n = 2) {
    return pow(m, n);
}

// Overloaded function to calculate power when both base and exponent are integers
double power(int m, int n = 2) {
    return pow(m, n);
}

int main() {
    // Demonstrating the use of the power function with a double base
    cout << "Double: " << power(5.5) << endl; // Expected output: 30.25

    // Demonstrating the use of the overloaded power function with an integer base
    cout << "Int: " << power(5) << endl; // Expected output: 25

    return 0;
}
```

## 2.6 Variance and Standard Deviation

This program calculates the variance and standard deviation of a set of numbers.

```cpp
#include <iostream>
#include <cmath>
#include <vector>
using namespace std;

void calculateVarianceAndStdDev(const vector<int>& nums) {
    double mean = 0;
    for (int num : nums) mean += num;
    mean /= nums.size();

    double variance = 0;
    for (int num : nums) variance += pow(num - mean, 2);
    variance /= nums.size();

    double stdDev = sqrt(variance);

    cout << "Variance: " << variance << ", Standard Deviation: " << stdDev << endl;
}

int main() {
    vector<int> nums = {1, 2, 3, 4, 5};
    calculateVarianceAndStdDev(nums);
    return 0;
}
```
## 2.7 Arithmetic or Geometric Progression

This final program checks whether a given array of integers follows an arithmetic or geometric progression.

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool isArithmetic(const vector<int>& arr) {
    if (arr.size() < 2) return true;
    int diff = arr[1] - arr[0];
    for (size_t i = 2; i < arr.size(); ++i) {
        if (arr[i] - arr[i - 1] != diff) return false;
    }
    return true;
}

bool isGeometric(const vector<int>& arr) {
    if (arr.size() < 2) return true;
    if (arr[0] == 0) return false; // Prevent division by zero
    double ratio = double(arr[1]) / arr[0];
    for (size_t i = 2; i < arr.size(); ++i) {
        if (double(arr[i]) / arr[i - 1] != ratio) return false;
    }
    return true;
}

int main() {
    vector<int> arr = {2, 4, 8, 16};
    cout << "Arithmetic: " << isArithmetic(arr) << ", Geometric: " << isGeometric(arr) << endl;
    return 0;
}
```