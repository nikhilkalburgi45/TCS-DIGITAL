# Q11 Count Prime Numbers Up to `n`

Given an integer `n`, count how many prime numbers exist from `1` to `n` (inclusive).

### Example 1

Input: `n = 10`

Output: `4`

Explanation: Prime numbers ≤ 10 → `2, 3, 5, 7`

### Example 2

Input: `n = 20`

Output: `8`

Explanation: Prime numbers ≤ 20 → `2, 3, 5, 7, 11, 13, 17, 19`

### Example 3

Input: `n = 1`

Output: `0`

Explanation: No primes exist up to 1.

## Approach 1: Using Loop with isPrime

### Core Idea

- For every number from `2` to `n`, check if it is prime.
- Use the isPrime helper function to check each number.
- Increment count if prime.

### Simple Steps

1. Initialize `count = 0`
2. Loop `i = 2 → n`
3. For each `i`, call isPrime(i)
4. If prime → increment count
5. Return count

## Code 1

```cpp
#include<bits/stdc++.h>
using namespace std;

bool isPrime(int n) {
    if (n <= 1) return false;

    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            return false;
        }
    }
    return true;
}

int countUptoN(int n) {
    int count = 0;

    for (int i = 2; i <= n; i++) {
        if (isPrime(i)) {
            count++;
        }
    }

    return count;
}

int main() {
    int n;
    cin >> n;

    cout << countUptoN(n);
    return 0;
}
```

## Approach 2: Optimal (Sieve of Eratosthenes)

### Core Idea

- Instead of checking each number repeatedly, precompute all primes using a sieve.
- Mark all non-primes, then count remaining primes.

### Simple Steps

1. Create boolean array `isPrime[n+1] = true`
2. Mark `0` and `1` as false
3. Start from `2`
4. Mark multiples of each prime as false
5. Count remaining `true` values

## Code 2

```cpp
#include<bits/stdc++.h>
using namespace std;

int countUptoN(int n) {
    vector<bool> isPrime(n + 1, true);
    isPrime[0] = isPrime[1] = false;

    for (int i = 2; i * i <= n; i++) {
        if (isPrime[i]) {
            for (int j = i * i; j <= n; j += i) {
                isPrime[j] = false;
            }
        }
    }

    int count = 0;
    for (int i = 2; i <= n; i++) {
        if (isPrime[i]) {
            count++;
        }
    }

    return count;
}

int main() {
    int n;
    cin >> n;

    cout << countUptoN(n);
    return 0;
}
```
