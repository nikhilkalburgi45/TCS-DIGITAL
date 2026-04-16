# Q7 Armstrong Number

Given an integer `n`, check whether it is an Armstrong number.

### Example 1

Input: `n = 153`

Output: `1`

Explanation: `1^3 + 5^3 + 3^3 = 153`, so it is an Armstrong number.

### Example 2

Input: `n = 123`

Output: `0`

Explanation: `1^3 + 2^3 + 3^3 = 36`, which is not equal to `123`.

### Example 3

Input: `n = 9474`

Output: `1`

Explanation: `9^4 + 4^4 + 7^4 + 4^4 = 9474`, so it is an Armstrong number.

## Approach

### Core Idea

- Count the number of digits.
- Raise each digit to that power.
- Add all values and compare with the original number.

### Simple Steps

1. Read the value of `n`.
2. If `n` is negative, return `false`.
3. Count the digits in the number.
4. Extract each digit and add `digit^count` to the sum.
5. Compare the sum with the original number.

## Code

```cpp
#include <bits/stdc++.h>
using namespace std;

bool armstrong(int originalNumber) {
    // Negative numbers are not Armstrong numbers here.
    if (originalNumber < 0) return false;

    int count = 0;
    int temp = originalNumber;

    // Handle 0 as a one-digit number.
    if (temp == 0) count = 1;

    // Count how many digits are in the number.
    while (temp > 0) {
        count++;
        temp /= 10;
    }

    long long sum = 0;
    temp = originalNumber;

    while (temp > 0) {
        // Raise each digit to the power of total digits and add it.
        int lastDigit = temp % 10;
        sum += (long long)round(pow(lastDigit, count));

        // Move to the next digit.
        temp /= 10;
    }

    // If the sum matches the original number, it is Armstrong.
    return sum == originalNumber;
}

int main() {
    int n;
    cin >> n;

    // Print 1 for true and 0 for false.
    cout << armstrong(n);
    return 0;
}
```
