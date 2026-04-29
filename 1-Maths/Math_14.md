# Q14 Find Factorial

Given an integer `n`, find the factorial of `n`. The factorial of `n` (denoted as `n!`) is the product of all positive integers from `1` to `n`.

### Example 1

Input: `n = 5`

Output: `120`

Explanation: `5! = 5 × 4 × 3 × 2 × 1 = 120`

### Example 2

Input: `n = 0`

Output: `1`

Explanation: By definition, `0! = 1`

### Example 3

Input: `n = 6`

Output: `720`

Explanation: `6! = 6 × 5 × 4 × 3 × 2 × 1 = 720`

## Approach 1: Using Loop

### Core Idea

- Multiply all integers from `1` to `n`.
- Start with result = `1`.
- For each number from `1` to `n`, multiply it with the result.

### Simple Steps

1. Initialize `result = 1`.
2. Loop from `i = 1` to `n`.
3. Multiply `result` by `i` in each iteration.
4. Return the final result.

## Code 1

```cpp
#include<bits/stdc++.h>
using namespace std;

long long fact(int n) {
    long long result = 1;

    for (int i = 1; i <= n; i++) {
        result = result * i;
    }

    return result;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n;
    cin >> n;

    cout << fact(n);
    return 0;
}
```

## Approach 2: Using Recursion

### Core Idea

- Use recursion where `n! = n * (n-1)!`.
- Base case: `0! = 1`.

### Simple Steps

1. If `n <= 1`, return `1`.
2. Otherwise, return `n * fact(n-1)`.

## Code 2

```cpp
#include<bits/stdc++.h>
using namespace std;

long long fact(int n) {
    // Base case: 0! = 1
    if (n <= 1) return 1;

    // Recursive case: n! = n * (n-1)!
    return n * fact(n - 1);
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n;
    cin >> n;

    cout << fact(n);
    return 0;
}
```
