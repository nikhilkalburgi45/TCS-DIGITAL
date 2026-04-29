# Q15 Fibonacci Number

Given an integer `n`, find the `n`-th Fibonacci number. The Fibonacci sequence is defined as:

- F(0) = 0
- F(1) = 1
- F(n) = F(n-1) + F(n-2) for n > 1

### Example 1

Input: `n = 6`

Output: `8`

Explanation: Sequence: 0, 1, 1, 2, 3, 5, 8. The 6th Fibonacci number is 8.

### Example 2

Input: `n = 0`

Output: `0`

Explanation: F(0) = 0 by definition.

### Example 3

Input: `n = 5`

Output: `5`

Explanation: Sequence: 0, 1, 1, 2, 3, 5. The 5th Fibonacci number is 5.

## Approach 1: Using Loop (Space-Optimized)

### Core Idea

- Each Fibonacci number is the sum of the previous two numbers.
- Use two variables to store the last two values.
- Iteratively compute the next Fibonacci number.

### Simple Steps

1. Handle base cases: F(0) = 0, F(1) = 1.
2. Initialize `prev2 = 0` and `prev1 = 1`.
3. Loop from `i = 2` to `n`.
4. Calculate `curr = prev1 + prev2`.
5. Shift variables: `prev2 = prev1`, `prev1 = curr`.
6. Return `prev1`.

## Code 1

```cpp
#include<bits/stdc++.h>
using namespace std;

long long fibo(int n) {
    if (n < 0) return -1;
    if (n <= 1) return n;

    long long prev1 = 1;
    long long prev2 = 0;

    for (int i = 2; i <= n; i++) {
        long long curr = prev1 + prev2;
        prev2 = prev1;
        prev1 = curr;
    }

    return prev1;
}

int main() {
    int n;
    cin >> n;

    cout << fibo(n);
    return 0;
}
```

## Approach 2: Using Recursion with Memoization

### Core Idea

- Use recursion with memoization to avoid recalculating values.
- Store computed results in a map for quick lookup.

### Simple Steps

1. Handle base cases: F(0) = 0, F(1) = 1.
2. Check if result already computed (in memo map).
3. If yes, return cached result.
4. Otherwise, compute and store result.

## Code 2

```cpp
#include<bits/stdc++.h>
using namespace std;

map<int, long long> memo;

long long fibo(int n) {
    if (n < 0) return -1;
    if (n <= 1) return n;

    // Check if already computed
    if (memo.find(n) != memo.end()) {
        return memo[n];
    }

    // Compute and store result
    memo[n] = fibo(n - 1) + fibo(n - 2);
    return memo[n];
}

int main() {
    int n;
    cin >> n;

    cout << fibo(n);
    return 0;
}
```
