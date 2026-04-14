# Q8 Check if a Number is Prime

Given an integer `n`, check whether it is a prime number.

---

## Example

### Example 1

**Input:**

```
7
```

**Output:**

```
1
```

---

### Example 2

**Input:**

```
10
```

**Output:**

```
0
```

---

## Approach (How it Works)

### Core Idea:

- A prime number has exactly **2 divisors → 1 and itself**

---

# Approach 1: Brute Force

### Step-by-step:

1. Take input `n`
2. If `n <= 1`, return false
3. Count how many numbers divide `n`
4. If count == 2 → prime, else not

---

## Code (Brute)

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPrime(int n) {

    if(n <= 1) return false;

    int count = 0;

    for(int i = 1; i <= n; i++) {
        if(n % i == 0) {
            count++;
        }
    }

    return count == 2;
}

int main() {

    int n;
    cin >> n;

    cout << isPrime(n);

    return 0;
}
```

---

# Approach 2: Optimal (√n)

### Step-by-step:

1. Take input `n`
2. If `n <= 1`, return false
3. Loop from `2` to `sqrt(n)`
4. If any divisor found → return false
5. Else → prime

---

## Code (Optimized)

```cpp id="4z6hkb"
#include <bits/stdc++.h>
using namespace std;

bool isPrime(int n) {

    if(n <= 1) return false;

    for(int i = 2; i * i <= n; i++) {
        if(n % i == 0) {
            return false;
        }
    }

    return true;
}

int main() {

    int n;
    cin >> n;

    cout << isPrime(n);

    return 0;
}
```
