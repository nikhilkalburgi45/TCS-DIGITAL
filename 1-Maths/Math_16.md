# Q16 Tribonacci Number

Given an integer `n`, find the `n`-th Tribonacci number. The Tribonacci sequence is defined as:

- T(0) = 0
- T(1) = 1
- T(2) = 1
- T(n) = T(n-1) + T(n-2) + T(n-3) for n > 2

### Example 1

Input: `n = 7`

Output: `13`

Explanation: Sequence: 0, 1, 1, 2, 4, 7, 13. The 7th Tribonacci number is 13.

### Example 2

Input: `n = 0`

Output: `0`

Explanation: T(0) = 0 by definition.

### Example 3

Input: `n = 5`

Output: `7`

Explanation: Sequence: 0, 1, 1, 2, 4, 7. The 5th Tribonacci number is 7.

## Approach 1: Using Loop (Space-Optimized)

### Core Idea

- Each Tribonacci number is the sum of the previous three numbers.
- Use three variables to store the last three values.
- Iteratively compute the next Tribonacci number.

### Simple Steps

1. Handle base cases: T(0) = 0, T(1) = 1, T(2) = 1.
2. Initialize `prev3 = 0`, `prev2 = 1`, `prev1 = 1`.
3. Loop from `i = 3` to `n`.
4. Calculate `curr = prev1 + prev2 + prev3`.
5. Shift variables: `prev3 = prev2`, `prev2 = prev1`, `prev1 = curr`.
6. Return `prev1`.

## Code 1

```cpp
#include<bits/stdc++.h>
using namespace std;

long long tribo(int n) {
    if (n < 0) return -1;
    if (n <= 1) return n;
    if (n == 2) return 1;

    long long prev1 = 1;
    long long prev2 = 1;
    long long prev3 = 0;

    for (int i = 3; i <= n; i++) {
        long long curr = prev1 + prev2 + prev3;
        prev3 = prev2;
        prev2 = prev1;
        prev1 = curr;
    }

    return prev1;
}

int main() {
    int n;
    cin >> n;

    cout << tribo(n);
    return 0;
}
```

## Approach 2: Using Recursion with Memoization

### Core Idea

- Use recursion with memoization to avoid recalculating values.
- Store computed results in a map for quick lookup.

### Simple Steps

1. Handle base cases: T(0) = 0, T(1) = 1, T(2) = 1.
2. Check if result already computed (in memo map).
3. If yes, return cached result.
4. Otherwise, compute and store result.

## Code 2

```cpp
#include<bits/stdc++.h>
using namespace std;

map<int, long long> memo;

long long tribo(int n) {
    if (n < 0) return -1;
    if (n <= 1) return n;
    if (n == 2) return 1;

    // Check if already computed
    if (memo.find(n) != memo.end()) {
        return memo[n];
    }

    // Compute and store result
    memo[n] = tribo(n - 1) + tribo(n - 2) + tribo(n - 3);
    return memo[n];
}

int main() {
    int n;
    cin >> n;

    cout << tribo(n);
    return 0;
}
```
