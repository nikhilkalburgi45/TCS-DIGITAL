# Q1 Extract and Print Digits of a Number

Given an integer `n`, extract and print all its digits one by one.

### Example 1

Input: `n = 1234`


Explanation: We keep taking the last digit of `1234`, so the digits are printed as `4 3 2 1`.

### Example 2

Input: `n = 0`

Output: `0`

Explanation: The number is already `0`, so we print `0`.

### Example 3

Input: `n = -567`

Output: `7 6 5`

Explanation: We ignore the negative sign and print the digits of `567` from last to first.

## Approach

### Core Idea

- Use `% 10` to get the last digit.
- Use `/ 10` to remove the last digit.
- Repeat until the number becomes `0`.

### Simple Steps

1. Read the value of `n`.
2. If `n` is `0`, print `0`.
3. If `n` is negative, convert it to positive.
4. Extract and print digits until the number becomes `0`.

## Code 1: Digits From Last to First

```cpp
#include <bits/stdc++.h>
using namespace std;

void extractAndPrintDigits(int n) {
    // Special case: 0 has only one digit.
    if (n == 0) {
        cout << 0;
        return;
    }

    // Convert negative numbers to positive before processing.
    long long num = abs((long long)n);

    while (num > 0) {
        // Take the last digit and print it.
        int lastDigit = num % 10;
        cout << lastDigit << " ";

        // Remove the last digit.
        num /= 10;
    }
}

int main() {
    int n;
    cin >> n;

    // Print digits from last to first.
    extractAndPrintDigits(n);
    return 0;
}
```

## Code 2: Digits From Left to Right

```cpp
#include <bits/stdc++.h>
using namespace std;

void printDigitsInOrder(int n) {
    // Convert the number into a string to read digits left to right.
    string s = to_string(n);

    for (char c : s) {
        // Skip the negative sign for negative numbers.
        if (c == '-') continue;

        // Print each digit character.
        cout << c << " ";
    }
}

int main() {
    int n;
    cin >> n;

    // Print digits in normal order.
    printDigitsInOrder(n);
    return 0;
}
```
