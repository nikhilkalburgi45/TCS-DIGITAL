# Q5 Reverse a Number

Given an integer `n`, reverse its digits and return the reversed number.

### Example 1

Input: `n = 1234`

Output: `4321`

Explanation: Reversing the digits of `1234` gives `4321`.

### Example 2

Input: `n = 1200`

Output: `21`

Explanation: Leading zeros are removed in the reversed number, so `0021` becomes `21`.

### Example 3

Input: `n = -567`

Output: `-765`

Explanation: We reverse the digits of `567` and then put the negative sign back.

## Approach

### Core Idea

- Use `% 10` to take the last digit.
- Add it to the reversed number using `reverseNo = reverseNo * 10 + digit`.
- Remove the last digit using `/ 10`.

### Simple Steps

1. Read the value of `n`.
2. Save whether the number is negative.
3. Work on the absolute value.
4. Build the reversed number digit by digit.
5. Add the sign back at the end.

## Code 1: Using Loop

```cpp
#include <bits/stdc++.h>
using namespace std;

long long reverseNumber(int n) {
    // Work with the absolute value so the loop stays simple.
    long long num = abs((long long)n);
    long long reverseNo = 0;

    while (num > 0) {
        // Take the last digit of the current number.
        int lastDigit = num % 10;

        // Append that digit to the reversed number.
        reverseNo = reverseNo * 10 + lastDigit;

        // Remove the last digit from the current number.
        num /= 10;
    }

    // Restore the sign for negative inputs.
    return n < 0 ? -reverseNo : reverseNo;
}

int main() {
    int n;
    cin >> n;

    // Print the reversed number.
    cout << reverseNumber(n);
    return 0;
}
```

## Code 2: Using String

```cpp
#include <bits/stdc++.h>
using namespace std;

long long reverseNumber(int n) {
    // Convert to string.
    string s = to_string(abs((long long)n));

    // Reverse the string.
    reverse(s.begin(), s.end());

    // Convert back to long long.
    long long reverseNo = stoll(s);

    // Restore the sign.
    return n < 0 ? -reverseNo : reverseNo;
}

int main() {
    int n;
    cin >> n;

    // Print the reversed number.
    cout << reverseNumber(n);
    return 0;
}
```
