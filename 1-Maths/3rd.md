# Q3 Sum of Digits of a Number

Given an integer `n`, calculate the sum of all its digits.

---

## Example

### Example 1

**Input:**

```
1234
```

**Output:**

```
10
```

---

### Example 2

**Input:**

```
0
```

**Output:**

```
0
```

---

### Example 3

**Input:**

```
-567
```

**Output:**

```
18
```

---

## Approach (How it Works)

### Core Idea:

- Extract last digit using `% 10`
- Add it to sum
- Remove last digit using `/ 10`
- Repeat until number becomes `0`

---

### Step-by-step:

1. Take input `n`
2. Handle edge case when `n == 0`
3. Convert negative number to positive
4. Loop:
   - `digit = n % 10`
   - Add to sum
   - `n = n / 10`

---

```cpp
#include <bits/stdc++.h>
using namespace std;

void addDigit(int n) {

    // Edge case
    if (n == 0) {
        cout << 0;
        return;
    }

    // Prevent overflow issue (INT_MIN)
    long long num = abs((long long)n);

    int sum = 0;

    // Calculate sum of digits
    while (num > 0) {
        int lastDigit = num % 10; // Extract last digit
        sum += lastDigit;         // Add to sum
        num = num / 10;           // Remove last digit
    }

    cout << sum;
}

int main() {
    int n;
    cin >> n;

    addDigit(n);

    return 0;
}
```
