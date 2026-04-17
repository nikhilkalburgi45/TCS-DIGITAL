# Q11. Print All Prime Factors of a Number

Given an integer `n`, print all its **prime factors**.

---

## Example 1

Input:

```
n = 12
```

Output:

```
2 2 3
```

Explanation:

```
12 = 2 × 2 × 3
```

---

## Example 2

Input:

```
n = 17
```

Output:

```
17
```

Explanation:

- 17 is already prime

---

# Approach 1: Naive (Don’t Use in Interview)

## Core Idea

- Loop from `2` to `n`
- Check:
  1. Does `i` divide `n`?
  2. Is `i` prime?

```cpp
#include <bits/stdc++.h>
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

int main() {
    int n;
    cin >> n;

    for (int i = 2; i <= n; i++) {
        // Check if i is prime and divides n
        if (isPrime(i)) {
            while (n % i == 0) {
                cout << i << " ";
                n = n / i;
            }
        }
    }

    return 0;
}
```

# Approach 2: Optimal (Prime Factorization using √n)

## Core Idea

Instead of checking every number:

- Extract factors **as you divide the number**

---

## Key Insight

Meaning:

- Once you find a factor, divide it out completely
- Reduce problem size continuously

---

## Simple Steps

1. Start from `i = 2`
2. While `i * i <= n`:
   - If `i` divides `n`:
     - Print `i`
     - Divide `n = n / i`

   - Else move to next `i`

3. After loop:
   - If `n > 1`, print `n` (remaining prime)

---

## Code (Optimal)

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;

    for (int i = 2; i * i <= n; i++) {
        // Extract all occurrences of i
        while (n % i == 0) {
            cout << i << " ";
            n = n / i;
        }
    }

    // If n is still greater than 1, it's a prime factor
    if (n > 1) {
        cout << n;
    }

    return 0;
}
```

---

# 🔍 Dry Run (n = 36)

```
i = 2
36 % 2 == 0 → print 2 → n = 18
18 % 2 == 0 → print 2 → n = 9

i = 3
9 % 3 == 0 → print 3 → n = 3
3 % 3 == 0 → print 3 → n = 1

Stop
```

Output:

```
2 2 3 3
```
