# Q2 Count Digits in a Number

Given an integer `n`, count the total number of digits in it.

### Example 1

Input: `n = 1234`

Output: `4`

Explanation: The number `1234` has 4 digits.

### Example 2

Input: `n = 0`

Output: `1`

Explanation: The number `0` is considered a single-digit number.

### Example 3

Input: `n = -567`

Output: `3`

Explanation: We ignore the negative sign. The number `567` has 3 digits.

## Approach

### Core Idea

- Remove the last digit using `/ 10`.
- Count how many times this can be done before the number becomes `0`.

### Simple Steps

1. Read the value of `n`.
2. If `n` is `0`, return `1`.
3. Convert negative numbers to positive.
4. Keep dividing by `10` and increase the count.

## Code 1: Using Loop

```cpp
#include <bits/stdc++.h>
using namespace std;

void countDigits(int n) {
    // Special case: 0 is a one-digit number.
    if (n == 0) {
        cout << 1;
        return;
    }

    // Use absolute value so negative numbers are handled correctly.
    long long num = abs((long long)n);
    int count = 0;

    while (num > 0) {
        // One division by 10 removes one digit.
        count++;
        num /= 10;
    }

    // Print the total number of digits.
    cout << count;
}

int main() {
    int n;
    cin >> n;

    // Count and print the digits of n.
    countDigits(n);
    return 0;
}
```

## Code 2: Using String Conversion

```cpp
#include <bits/stdc++.h>
using namespace std;

void countDigits(int n) {
    // Special case: 0 is a one-digit number.
    if (n == 0) {
        cout << 1;
        return;
    }

    // Convert to string and get length.
    string s = to_string(abs((long long)n));
    cout << s.length();
}

int main() {
    int n;
    cin >> n;

    // Count and print the digits of n.
    countDigits(n);
    return 0;
}
```
