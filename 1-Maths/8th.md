# Q8 Print All Divisors

Given an integer `n`, print all its divisors.

---

## Example

### Example 1

**Input:**

```
6
```

**Output:**

```
1 2 3 6
```

---

### Example 2

**Input:**

```
10
```

**Output:**

```
1 2 5 10
```

---

## Approach (How it Works)

### Core Idea:

- A divisor is a number that divides `n` completely
- Instead of checking till `n`, optimize using √n

---

### Step-by-step:

1. Take input `n`
2. Loop from `1` to `sqrt(n)`
3. If `i` divides `n`
   - print `i`
   - print `n/i` (if different)

4. Avoid duplicates when `i == n/i`

---

## Code (Optimized)

```cpp
#include <bits/stdc++.h>
using namespace std;

void printAllDivisors(int n) {

    for(int i = 1; i * i <= n; i++) {

        if(n % i == 0) {
            cout << i << " ";
        }
    }
}

int main() {

    int n;
    cin >> n;

    printAllDivisors(n);

    return 0;
}
```
