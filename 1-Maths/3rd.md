# Q3 Sum of Digits of a Number

Given an integer `n`, calculate the sum of all its digits.

### Example 1

Input: `n = 1234`

Output: `10`

Explanation: `1 + 2 + 3 + 4 = 10`.

### Example 2

Input: `n = 0`

Output: `0`

Explanation: The sum of digits of `0` is `0`.

### Example 3

Input: `n = -567`

Output: `18`

Explanation: We ignore the negative sign. `5 + 6 + 7 = 18`.

## Approach

### Core Idea

- Use `% 10` to get the last digit.
- Add it to the sum.
- Use `/ 10` to remove the last digit.

### Simple Steps

1. Read the value of `n`.
2. If `n` is `0`, print `0`.
3. Convert negative numbers to positive.
4. Extract each digit and add it to the sum.

## Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void addDigit(int n) {
    // Special case: sum of digits of 0 is 0.
    if (n == 0) {
        cout << 0;
        return;
    }

    // Convert negative numbers to positive.
    long long num = abs((long long)n);
    int sum = 0;

    while (num > 0) {
        // Extract the last digit and add it to the sum.
        int lastDigit = num % 10;
        sum += lastDigit;

        // Remove the last digit.
        num /= 10;
    }

    // Print the final sum of digits.
    cout << sum;
}

int main() {
    int n;
    cin >> n;

    // Find and print the sum of digits.
    addDigit(n);
    return 0;
}
```
