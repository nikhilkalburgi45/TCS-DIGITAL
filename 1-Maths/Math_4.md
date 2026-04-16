# Q4 Convert Number to Single Digit (Digital Root)

Given an integer `n`, repeatedly add its digits until the result becomes a single digit.

### Example 1

Input: `n = 1234`

Output: `1`

Explanation: `1 + 2 + 3 + 4 = 10`, then `1 + 0 = 1`.

### Example 2

Input: `n = 0`

Output: `0`

Explanation: The number is already a single digit.

### Example 3

Input: `n = -567`

Output: `9`

Explanation: We ignore the negative sign. `5 + 6 + 7 = 18`, then `1 + 8 = 9`.

## Approach

### Core Idea

- Keep summing the digits until the number becomes smaller than `10`.

### Simple Steps

1. Read the value of `n`.
2. Convert negative numbers to positive.
3. While the number has more than one digit, find the digit sum.
4. Replace the number with that sum.

## Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int singleDigit(int n) {
    // Convert negative numbers to positive first.
    long long num = abs((long long)n);

    // Keep reducing the number until it becomes a single digit.
    while (num > 9) {
        // Store the sum of digits for the current round.
        int sum = 0;

        while (num > 0) {
            // Add the last digit to the running sum.
            int lastDigit = num % 10;
            sum += lastDigit;

            // Remove the last digit.
            num /= 10;
        }

        // Start the next round with the new digit sum.
        num = sum;
    }

    return (int)num;
}

int main() {
    int n;
    cin >> n;

    // Print the final single-digit result.
    cout << singleDigit(n);
    return 0;
}
```
