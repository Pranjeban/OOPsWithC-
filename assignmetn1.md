# Assignment 1 Solutions

This document outlines the solutions for the given programming tasks, focusing on various aspects of C++ programming. Each solution demonstrates key programming concepts such as loops, functions, default arguments, dynamic memory allocation, function overloading, and mathematical calculations.

## Denomination Calculator

This program calculates the denomination details for a given amount.


```cpp
#include <iostream>
using namespace std;

int main() {
    int amount;
    cout << "Enter the amount to be tendered:\n";
    cin >> amount;

    int denominations[] = {2000, 500, 100, 50, 10, 5, 2, 1};
    int count[8] = {0};

    for (int i = 0; i < 8; i++) {
        if (amount >= denominations[i]) {
            count[i] = amount / denominations[i];
            amount = amount % denominations[i];
        }
    }

    cout << "Denomination details:\n";
    for (int i = 0; i < 8; i++) {
        if (count[i] != 0) {
            cout << denominations[i] << " x " << count[i] << " = " << denominations[i] * count[i] << endl;
        }
    }

    return 0;
}
```
## Curious Number
```cpp
#include <iostream>
using namespace std;

int factorial(int n) {
    return (n == 1 || n == 0) ? 1 : factorial(n - 1) * n;
}

int main() {
    for (int i = 10; i <= 10000; i++) {
        int sum = 0;
        int number = i;
        while (number > 0) {
            int digit = number % 10;
            sum += factorial(digit);
            number /= 10;
        }
        if (sum == i) {
            cout << i << " is a curious number.\n";
        }
    }
    return 0;
}
```
## Trailing Zeros Finder

This program calculates the number of trailing zeros in the factorial of a given number.


```cpp
#include <iostream>
using namespace std;

int findTrailingZeros(int n) {
    int count = 0;
    for (int i = 5; n / i >= 1; i *= 5) {
        count += n / i;
    }
    return count;
}

int main() {
    int n;
    cout << "Enter a non-negative number:\n";
    cin >> n;
    cout << "No. of zeros at the end of " << n << "! = " << findTrailingZeros(n) << endl;
    return 0;
}
```
## Cardino Triple Finder
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool isCardanoTriplet(int a, int b, int c) {
    double term = cbrt(a + b * sqrt(c)) + cbrt(a - b * sqrt(c));
    return fabs(term - 1) < 1e-6;
}

int main() {
    for (int a = 1; a <= 100; a++) {
        for (int b = 1; b <= 100; b++) {
            for (int c = 1; c <= 100; c++) {
                if ((a + b + c) <= 100 && isCardanoTriplet(a, b, c)) {
                    cout << "(" << a << "," << b << "," << c << ")" << endl;
                }
            }
        }
    }
    return 0;
}
```
## Fibonacci Digit Finder

This program finds the index of the first term in the Fibonacci sequence to contain 10 digits.


```cpp
#include <iostream>
using namespace std;

int main() {
    long long a = 1, b = 1, c;
    int index = 2;

    while (true) {
        c = a + b;
        index++;
        a = b;
        b = c;
        if (to_string(c).length() == 10) {
            cout << "The index of the first term in the Fibonacci sequence to contain 10 digits is " << index << ".\n";
            break;
        }
    }

    return 0;
}
```
## Voting System
```cpp
#include <iostream>
using namespace std;

int main() {
    int votes[6] = {0}; // Index 0 for spoilt ballots
    int vote;
    cout << "Enter the votes (1-5), any other number to stop:\n";
    while (cin >> vote) {
        if (vote >= 1 && vote <= 5) {
            votes[vote]++;
        } else {
            votes[0]++; // Count as spoilt ballot
        }
    }

    for (int i = 1; i <= 5; i++) {
        cout << "Candidate " << i << ": " << votes[i] << " votes\n";
    }
    cout << "Spoilt ballots: " << votes[0] << endl;

    return 0;
}
```
## Number Pattern Printer

This program prints a simple number pattern.


```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        for (int j = 1; j <= i; j++) {
            cout << i;
        }
        cout << endl;
    }
    // Extend as needed
    return 0;
}
```

## Electricity Bill
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string name;
    int units;
    cout << "Enter the name of the user and number of units consumed:\n";
    cin >> name >> units;

    double bill = 50; // Minimum charge
    if (units > 300) {
        bill += (units - 300) * 0.9 + 200 * 0.8 + 100 * 0.6;
    } else if (units > 200) {
        bill += (units - 200) * 0.8 + 100 * 0.6;
    } else if (units > 100) {
        bill += (units - 100) * 0.6;
    } else {
        bill += units * 0.6;
    }

    if (bill > 300) {
        bill += bill * 0.15; // Surcharge
    }

    cout << name << "'s bill: Rs. " << bill << endl;

    return 0;
}
```