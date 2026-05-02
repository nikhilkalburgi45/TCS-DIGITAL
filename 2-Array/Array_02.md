## Q2 Problem: Second Largest and Second Smallest Element

Given an integer array `nums`, return:

- The **second largest** element
- The **second smallest** element

If either does not exist (due to duplicates or size < 2), return `-1` for that value.

---

## Example 1

```text
Input: nums = [3, 1, 5, 2, 4]
Output: 4 2
```

---

## Example 2

```text
Input: nums = [5, 5, 5]
Output: -1 -1
```

---

## Example 3

```text
Input: nums = [10, 9, 11, 13, 13]
Output: 11 10
```

```cpp
#include <iostream>
#include <vector>
#include <sstream>
#include <climits>
using namespace std;

// Function to find second smallest element
int secondSmallest(vector<int> &arr) {
    int n = arr.size();

    // If less than 2 elements → no second smallest
    if (n < 2) return -1;

    int small = INT_MAX;          // smallest element
    int second_small = INT_MAX;   // second smallest element

    for (int i = 0; i < n; i++) {
        if (arr[i] < small) {
            // Found new smallest → shift old smallest to second
            second_small = small;
            small = arr[i];
        }
        else if (arr[i] < second_small && arr[i] != small) {
            // Found a value between smallest and second smallest
            second_small = arr[i];
        }
    }

    // If second smallest was never updated → return -1
    return (second_small == INT_MAX) ? -1 : second_small;
}

// Function to find second largest element
int secondLargest(vector<int> &arr) {
    int n = arr.size();

    // If less than 2 elements → no second largest
    if (n < 2) return -1;

    int large = INT_MIN;           // largest element
    int second_large = INT_MIN;    // second largest element

    for (int i = 0; i < n; i++) {
        if (arr[i] > large) {
            // Found new largest → shift old largest to second
            second_large = large;
            large = arr[i];
        }
        else if (arr[i] > second_large && arr[i] != large) {
            // Found a value between largest and second largest
            second_large = arr[i];
        }
    }

    // If second largest was never updated → return -1
    return (second_large == INT_MIN) ? -1 : second_large;
}

int main() {
    string line;
    getline(cin, line);

    // Convert input like [1,2,3] → "1 2 3"
    for (char &ch : line) {
        if (ch == '[' || ch == ']' || ch == ',') {
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);
    int x;

    // Parse integers into vector
    while (ss >> x) {
        arr.push_back(x);
    }

    // Output: second largest first, then second smallest
    cout << secondLargest(arr) << " " << secondSmallest(arr);

    return 0;
}
```
