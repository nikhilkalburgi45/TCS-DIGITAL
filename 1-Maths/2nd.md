# Q2 Count Digits in a Number

Given an integer `n`, count the total number of digits in it.

---

## Example

### Example 1

**Input:**

```
1234
```

**Output:**

```
4
```

---

### Example 2

**Input:**

```
0
```

**Output:**

```
1
```

---

### Example 3

**Input:**

```
-567
```

**Output:**

```
3
```

---

## Approach (How it Works)

### Core Idea:

- Remove digits one by one using `/ 10`
- Count how many times you can do that before number becomes `0`

---

### Step-by-step:

1. Take input `n`
2. Handle edge case when `n == 0`
3. Convert negative to positive
4. Loop:
   - Remove last digit
   - Increment count

---

```cpp
#include <bits/stdc++.h>
using namespace std;

void countDigits(int n) {

    // Edge case: if number is 0
    if (n == 0) {
        cout << 1;
        return;
    }

    // Use long long to safely handle INT_MIN
    long long num = abs((long long)n);

    int count = 0;

    // Count digits
    while (num > 0) {
        count++;
        num = num / 10;
    }

    cout << count;
}

int main() {
    int n;
    cin >> n;

    countDigits(n);

    return 0;
}
```
