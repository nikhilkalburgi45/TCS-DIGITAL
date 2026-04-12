# Q5 Reverse a Number

Given an integer `n`, reverse its digits and return the reversed number.

---

## Example

### Example 1

**Input:**

```
1234
```

**Output:**

```
4321
```

---

### Example 2

**Input:**

```
1200
```

**Output:**

```
21
```

---

### Example 3

**Input:**

```
-567
```

**Output:**

```
-765
```

---

## Approach (How it Works)

### Core Idea:

- Extract last digit using `% 10`
- Append it to result using `* 10`
- Remove last digit using `/ 10`

---

### Step-by-step:

1. Take input `n`
2. Store sign (positive/negative)
3. Work with absolute value
4. Loop:
   - `digit = n % 10`
   - `reverse = reverse * 10 + digit`
   - `n = n / 10`

5. Restore sign

---

## Code (Fixed + Safe Version)

```cpp
#include <bits/stdc++.h>
using namespace std;

int reverseNumber(int n) {

    // Use long long to avoid overflow while processing
    long long num = abs((long long)n);
    long long reverseNo = 0;

    while (num > 0) {
        int lastDigit = num % 10;
        reverseNo = (reverseNo * 10) + lastDigit;
        num = num / 10;
    }

    return reverseNo;
}

int main() {
    int n;
    cin >> n;

    cout << reverseNumber(n);

    return 0;
}
```
