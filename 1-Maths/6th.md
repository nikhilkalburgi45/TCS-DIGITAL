# Q6 Palindrome Number

Given an integer `n`, check whether it is a palindrome or not.

### Example 1

Input: `n = 121`

Output: `1`

Explanation: The number reads the same from left to right and right to left.

### Example 2

Input: `n = 123`

Output: `0`

Explanation: The reverse of `123` is `321`, so it is not a palindrome.

### Example 3

Input: `n = -121`

Output: `0`

Explanation: Negative numbers are not treated as palindromes here.

## Approach

### Core Idea

- Reverse the number.
- Compare the reversed value with the original value.

### Simple Steps

1. Read the value of `n`.
2. If `n` is negative, return `false`.
3. Reverse the number.
4. Compare the reversed number with the original number.

## Code

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPalli(int originalNumber) {
    // Negative numbers are not palindrome in this version.
    if (originalNumber < 0) return false;

    long long num = originalNumber;
    long long reverseNumber = 0;

    while (num > 0) {
        // Build the reversed number one digit at a time.
        int lastDigit = num % 10;
        reverseNumber = reverseNumber * 10 + lastDigit;
        num /= 10;
    }

    // If both numbers are same, it is a palindrome.
    return originalNumber == reverseNumber;
}

int main() {
    int n;
    cin >> n;

    // Print 1 for true and 0 for false.
    cout << isPalli(n);
    return 0;
}
```
