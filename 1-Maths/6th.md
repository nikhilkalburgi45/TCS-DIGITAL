# Q6 Palindrome Number

Given an integer `n`, check whether it is a palindrome or not.

---

## Example

### Example 1

**Input:**

```
121
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
-121
```

**Output:**

```
0
```

---

## Approach (How it Works)

### Core Idea:

- Reverse the number
- Compare it with the original number

---

### Step-by-step:

1. Take input `n`
2. Store original number
3. Reverse the number
4. Compare original and reversed
5. Return true (1) or false (0)

---

## Code

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPalli(int originalNumber) {

    // Negative numbers are not palindrome
    if (n < 0) return false;

    long long num = originalNumber;
    long long reverseNumber = 0;

    while (num > 0) {
        int lastDigit = num % 10;
        reverseNumber = (reverseNumber * 10) + lastDigit;
        num = num / 10;
    }

    return originalNumber == reverseNumber;
}

int main() {

    int n;
    cin >> n;

    cout << isPalli(n);

    return 0;
}
```
