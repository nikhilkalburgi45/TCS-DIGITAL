# Q9 Check if a Number is Prime

Given an integer `n`, check whether it is a prime number.

### Example 1

Input: `n = 7`

Output: `1`

Explanation: `7` has exactly two divisors: `1` and `7`.

### Example 2

Input: `n = 10`

Output: `0`

Explanation: `10` is divisible by `2` and `5`, so it is not prime.

## Approach 1: Brute Force

### Core Idea

- Count how many numbers divide `n`.
- A prime number has exactly 2 divisors.

### Simple Steps

1. If `n <= 1`, return `false`.
2. Check every number from `1` to `n`.
3. Count how many numbers divide `n`.
4. If the count is `2`, the number is prime.

## Code 1

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPrimeBrute(int n) {
    // Numbers less than or equal to 1 are not prime.
    if (n <= 1) return false;

    int count = 0;

    for (int i = 1; i <= n; i++) {
        // Count how many numbers divide n exactly.
        if (n % i == 0) {
            count++;
        }
    }

    // A prime number has exactly two divisors.
    return count == 2;
}

int main() {
    int n;
    cin >> n;

    // Print 1 for prime and 0 for not prime.
    cout << isPrimeBrute(n);
    return 0;
}
```

## Approach 2: Optimal

### Core Idea

- If a number has a divisor larger than `sqrt(n)`, it must also have a smaller paired divisor.
- So checking up to `sqrt(n)` is enough.

### Simple Steps

1. If `n <= 1`, return `false`.
2. Loop from `2` to `sqrt(n)`.
3. If any number divides `n`, return `false`.
4. If no divisor is found, return `true`.

## Code 2

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPrime(int n) {
    // Numbers less than or equal to 1 are not prime.
    if (n <= 1) return false;

    for (int i = 2; i * i <= n; i++) {
        // If any number divides n, it is not prime.
        if (n % i == 0) {
            return false;
        }
    }

    // No divisor found, so the number is prime.
    return true;
}

int main() {
    int n;
    cin >> n;

    // Print 1 for prime and 0 for not prime.
    cout << isPrime(n);
    return 0;
}
```

```cpp
#include<bits/stdc++.h>
using namespace std;

bool isPrime(int n) {
    if (n <= 1) return false;
    if (n == 2) return true;
    if (n % 2 == 0) return false;

    for (int i = 3; i <= n / i; i += 2) {
        if (n % i == 0) {
            return false;
        }
    }
    return true;
}

int main() {
    int n;
    cin >> n;

    cout << (isPrime(n) ? "Prime" : "Not Prime");
}
```
