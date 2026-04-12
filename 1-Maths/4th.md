# Q4 Convert Number to Single Digit (Digital Root)

Given an integer `n`, repeatedly add its digits until the result becomes a single digit.

---

## Example

### Example 1

**Input:**

```
1234
```

**Output:**

```
1
```

Explanation:

```
1+2+3+4 = 10
1+0 = 1
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
9
```

---

## Approach (How it Works)

### Core Idea:

- Keep summing digits until number becomes single digit (`< 10`)

---

### Step-by-step:

1. Take input `n`
2. Convert negative to positive
3. While number has more than one digit:
   - Extract digits and calculate sum
   - Replace `n` with sum

4. Print final single digit

---

## 💻 Code (Fixed Version)

```cpp
#include <bits/stdc++.h>
using namespace std;

int singleDigit(int n) {

    // Handle negative safely
    long long num = abs((long long)n);

    // Keep reducing until single digit
    while (num > 9) {

        int sum = 0;  // reset every iteration

        while (num > 0) {
            int lastDigit = num % 10;
            sum += lastDigit;
            num /= 10;
        }

        num = sum; // update number
    }

    return num;
}

int main() {
    int n;
    cin >> n;

    cout << singleDigit(n);

    return 0;
}
```


