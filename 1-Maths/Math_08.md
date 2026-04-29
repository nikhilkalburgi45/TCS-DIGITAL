# Q8 Print All Divisors

Given an integer `n`, print all its divisors in increasing order.

### Example 1

Input: `n = 6`

Output: `1 2 3 6`

Explanation: These are all the numbers that divide `6` exactly.

### Example 2

Input: `n = 10`

Output: `1 2 5 10`

Explanation: These are all the numbers that divide `10` without leaving a remainder.

## Approach

### Core Idea

- Divisors come in pairs.
- If `i` divides `n`, then `n / i` is also a divisor.
- We only need to check up to `sqrt(n)`.

### Simple Steps

1. Read the value of `n`.
2. Loop from `1` to `sqrt(n)`.
3. If `i` divides `n`, store both `i` and `n / i`.
4. Sort the divisors and print them.

## Code 1: Using Vector and Sort

```cpp
#include <bits/stdc++.h>
using namespace std;

void printAllDivisors(int n) {
    // Store all divisors first so we can sort them later.
    vector<int> divisors;

    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            // i is a divisor of n.
            divisors.push_back(i);

            // n / i is the paired divisor. Avoid duplicate for perfect squares.
            if (i != n / i) {
                divisors.push_back(n / i);
            }
        }
    }

    // Sort divisors so output is in increasing order.
    sort(divisors.begin(), divisors.end());

    for (int x : divisors) {
        // Print each divisor.
        cout << x << " ";
    }
}

int main() {
    int n;
    cin >> n;

    // Print all divisors of n.
    printAllDivisors(n);
    return 0;
}
```
