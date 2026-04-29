# Q12 Sum of Prime Numbers up to `n`

Given an integer `n`, find the sum of all prime numbers from `1` to `n` (inclusive).

### Example 1

Input: `n = 10`

Output: `17`

Explanation: Prime numbers ≤ 10 → `2, 3, 5, 7`. Sum = `2 + 3 + 5 + 7 = 17`

### Example 2

Input: `n = 20`

Output: `77`

Explanation: Prime numbers ≤ 20 → `2, 3, 5, 7, 11, 13, 17, 19`. Sum = `77`

### Example 3

Input: `n = 2`

Output: `2`

Explanation: Only `2` is prime, so sum = `2`

## Approach 1: Using isPrime Helper

### Core Idea

- Iterate through all numbers from `2` to `n`.
- Check if each number is prime.
- If prime, add it to the running sum.

### Simple Steps

1. Initialize `sum = 0`.
2. Loop from `i = 2` to `n`.
3. Check if `i` is prime using isPrime().
4. If prime, add `i` to sum.
5. Return the total sum.

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

int sumUptN(int n) {
    int sum = 0;

    for (int i = 2; i <= n; i++) {
        if (isPrime(i)) {
            sum = sum + i;
        }
    }
    return sum;
}

int main() {
    int n;
    cin >> n;

    cout << sumUptN(n);
    return 0;
}
```

## Approach 2: Using Sieve of Eratosthenes

### Core Idea

- Use Sieve of Eratosthenes to find all primes efficiently.
- Sum up all the primes found.

### Simple Steps

1. Create boolean array `isPrime[n+1] = true`
2. Mark `0` and `1` as false
3. Mark multiples of each prime as false
4. Sum all indices marked as true

## Code 2

```cpp
#include<bits/stdc++.h>
using namespace std;

int sumUptN(int n) {
    vector<bool> isPrime(n + 1, true);
    isPrime[0] = isPrime[1] = false;

    for (int i = 2; i * i <= n; i++) {
        if (isPrime[i]) {
            for (int j = i * i; j <= n; j += i) {
                isPrime[j] = false;
            }
        }
    }

    int sum = 0;
    for (int i = 2; i <= n; i++) {
        if (isPrime[i]) {
            sum += i;
        }
    }
    return sum;
}

int main() {
    int n;
    cin >> n;

    cout << sumUptN(n);
    return 0;
}
```
