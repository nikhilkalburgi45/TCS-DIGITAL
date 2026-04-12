# Q1 Extract and Print Digits of a Number

Given an integer `n`, extract and print all its digits one by one.

## Example

### Example 1

**Input:**

```
1234
```

**Output:**

```
4 3 2 1
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
7 6 5
```

---

## Approach (How it Works)

### Core Idea:

- Extract last digit using `% 10`
- Remove last digit using `/ 10`
- Repeat until number becomes `0`

### Step-by-step:

1. Take input number `n`
2. Handle edge case when `n == 0`
3. Convert negative number to positive
4. Loop:
   - `digit = n % 10`
   - Print digit
   - `n = n / 10`

```cpp
#include <bits/stdc++.h>
using namespace std;

void extractAndPrintDigits(int n) {

    // Edge case: if number is 0
    if (n == 0) {
        cout << 0;
        return;
    }

    // Handle negative numbers
    if (n < 0) {
        n = -n;
    }

    // Extract digits
    while (n > 0) {
        int lastDigit = n % 10;   // Get last digit
        cout << lastDigit << " "; // Print digit
        n = n / 10;               // Remove last digit
    }
}

int main() {
    int n;
    cin >> n;

    extractAndPrintDigits(n);

    return 0;
}
```

```cpp
void printDigitsInOrder(int n) {

    string s = to_string(n);

    for (char c : s) {
        if (c == '-') continue; // skip negative sign
        cout << c << " ";
    }
}

int main() {
    int n;
    cin >> n;

    printDigitsInOrder(n);
}
```
