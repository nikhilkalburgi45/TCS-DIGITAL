# Q13 Twin Prime Pairs

Given an integer `n`, print all twin prime pairs up to `n`. Twin primes are pairs of prime numbers that differ by exactly `2`.

### Example 1

Input: `n = 15`

Output: `(3,5) (5,7) (11,13)`

Explanation: These are pairs of primes that differ by 2.

### Example 2

Input: `n = 10`

Output: `(3,5) (5,7)`

Explanation: Primes ≤ 10 are `2, 3, 5, 7`. Twin pairs are `(3,5)` and `(5,7)`.

### Example 3

Input: `n = 5`

Output: `(3,5)`

Explanation: Only one twin prime pair up to 5.

## Approach 1: Using isPrime Helper

### Core Idea

- A twin prime pair is two primes that differ by 2.
- For each number `i`, check if both `i` and `i+2` are prime.
- If yes, print them as a pair.

### Simple Steps

1. Loop from `i = 2` to `n - 2`.
2. Check if `i` is prime AND `i + 2` is prime.
3. If both are prime, print the pair `(i, i+2)`.

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

void twinPrime(int n) {
    for (int i = 2; i <= n - 2; i++) {
        if (isPrime(i) && isPrime(i + 2)) {
            cout << "(" << i << "," << i + 2 << ") ";
        }
    }
}

int main() {
    int n;
    cin >> n;

    twinPrime(n);
    return 0;
}
```

## Approach 2: Using Sieve of Eratosthenes

### Core Idea

- Use Sieve to find all primes first.
- Then iterate and print twin prime pairs.

### Simple Steps

1. Create sieve to mark all primes
2. Loop through and check pairs
3. Print twin prime pairs

## Code 2

```cpp
#include<bits/stdc++.h>
using namespace std;

void twinPrime(int n) {
    vector<bool> isPrime(n + 1, true);
    isPrime[0] = isPrime[1] = false;

    for (int i = 2; i * i <= n; i++) {
        if (isPrime[i]) {
            for (int j = i * i; j <= n; j += i) {
                isPrime[j] = false;
            }
        }
    }

    for (int i = 2; i <= n - 2; i++) {
        if (isPrime[i] && isPrime[i + 2]) {
            cout << "(" << i << "," << i + 2 << ") ";
        }
    }
}

int main() {
    int n;
    cin >> n;

    twinPrime(n);
    return 0;
}
```
