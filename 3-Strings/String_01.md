# 1) Problem Statement

Reverse a given string **in-place** without using extra space.

---

# 2) Input / Output

**Input:**

```
hello world
```

**Output:**

```
dlrow olleh
```

---

# 3) Simple Explanation

You are given a string.
You need to **flip it completely**, like:

```
h e l l o
↓ ↓ ↓ ↓ ↓
o l l e h
```

You are NOT allowed to create another string ideally — modify the same one.

---

# 4) Idea / Intuition

Think of it like:

- One pointer at **start**
- One pointer at **end**
- Swap them
- Move inward

Example:

```
hello

Step 1: h ↔ o  → oellh
Step 2: e ↔ l  → olleh
Stop when pointers meet
```

This is a classic **two-pointer technique**.

---

# 5) Algorithm (Simple Steps)

1. Take string input
2. Initialize:
   - `left = 0`
   - `right = n - 1`

3. While `left < right`:
   - Swap `str[left]` and `str[right]`
   - Increment `left`
   - Decrement `right`

4. Print the string

---

# 6) Complete Code (With Simple Comments)

```cpp
#include <iostream>
#include <string>
using namespace std;

// Function to reverse string in-place
void reverseString(string &str) {

    int left = 0;
    int right = str.size() - 1;

    // Keep swapping until pointers meet
    while (left < right) {
        swap(str[left], str[right]); // swap characters
        left++;   // move forward
        right--;  // move backward
    }
}

int main() {

    string str;

    // Take full line input (including spaces)
    getline(cin, str);

    // Reverse the string
    reverseString(str);

    // Print the result
    cout << str;

    return 0;
}
```

---

# Dry Run

Input:

```
abcde
```

Steps:

```
left=0, right=4 → swap a,e → ebcda
left=1, right=3 → swap b,d → edcba
left=2, right=2 → stop
```

Output:

```
edcba
```

---

# Complexity

- Time: **O(n)** (single pass)
- Space: **O(1)** (in-place, no extra memory)
