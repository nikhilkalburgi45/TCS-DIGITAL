# Q13. Count Prime Numbers up to `N`

Given an integer `n`, count how many prime numbers exist from `1` to `n`.

---

## Example 1

Input:

```text
n = 10
```

Output:

```text
4
```

Explanation:

```text
Primes: 2, 3, 5, 7
```

---

## Approach 1: Reuse `isPrime` (Your Current Code)

## Core Idea

- Iterate from `2 → n`
- Check each number using `isPrime()`
- Count valid primes

---

## Code (Your Approach — Cleaned)

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPrime(int n){
    if(n <= 1) return false;

    for(int i = 2; i * i <= n; i++){
        if(n % i == 0){
            return false;
        }
    }
    return true;
}

int main() {
    int n;
    cin >> n;

    int count = 0;

    for(int i = 2; i <= n; i++){
        if(isPrime(i)){
            count++;
        }
    }

    cout << count;
    return 0;
}
```

---

# Approach 2: Optimal (Sieve of Eratosthenes)

## Core Idea

- Instead of checking numbers one by one
- Precompute all primes in one pass

---

## Key Insight

If a number is prime:

- Its multiples are NOT prime

So eliminate instead of checking.

---

## Code (Optimal)

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;

    vector<bool> prime(n + 1, true);

    prime[0] = prime[1] = false;

    for(int i = 2; i * i <= n; i++){
        if(prime[i]){
            for(int j = i * i; j <= n; j += i){
                prime[j] = false;
            }
        }
    }

    int count = 0;

    for(int i = 2; i <= n; i++){
        if(prime[i]){
            count++;
        }
    }

    cout << count;

    return 0;
}
```
