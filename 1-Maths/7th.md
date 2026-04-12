# Q7 Armstrong Number

Given an integer `n`, check whether it is an Armstrong number.

---

## Example

### Example 1

**Input:**

```
153
```

**Output:**

```
1
```

---

### Example 2

**Input:**

```
123
```

**Output:**

```
0
```

---

### Example 3

**Input:**

```
9474
```

**Output:**

```
1
```

---

## Approach (How it Works)

### Core Idea:

An **Armstrong number** is a number where:

> Sum of (each digit ^ total number of digits) == original number

---

### Step-by-step:

1. Take input `n`
2. Store original number
3. Count number of digits
4. Extract each digit
5. Raise digit to power of digit count
6. Add all values
7. Compare with original number
8. Return true (1) or false (0)

---

## Code (Correct & Generalized)

```cpp
#include <bits/stdc++.h>

using namespace std;

bool armstrong(int originalNumber) {

    int sum = 0;
    int x = originalNumber;
    while (x > 0) {
        int lastDigit = x % 10;
        sum = sum + (lastDigit * lastDigit * lastDigit);
        x = x / 10;

    }

    return originalNumber == sum;

}

int main() {

    int n;
    cin >> n;
    cout << armstrong(n);

}
```
