## Q3 Problem: K-th Largest Element in an Array

Given an integer array `nums` and an integer `k`, return the **k-th largest** element in the array.

If `k` is invalid (greater than array size or non-positive), return `-1`.

---

## Example 1

```text
Input: nums = [3,2,1,5,6,4], k = 2
Output: 5
```

---

## Example 2

```text
Input: nums = [3,2,3,1,2,4,5,5,6], k = 4
Output: 4
```

---

## Example 3

```text
Input: nums = [1], k = 1
Output: 1
```

```cpp
#include <iostream>
#include <vector>
#include <sstream>
#include <algorithm>
using namespace std;

// Function to find k-th largest using sorting
int findKthLargest(vector<int>& nums, int k) {
    int n = nums.size();

    // Edge case
    if (k > n || k <= 0) return -1;

    sort(nums.begin(), nums.end()); // ascending order

    return nums[n - k]; // k-th largest
}

int main() {
    string line;
    getline(cin, line);

    // Clean input: [1,2,3]
    for (char &ch : line) {
        if (ch == '[' || ch == ']' || ch == ',') {
            ch = ' ';
        }
    }

    vector<int> nums;
    stringstream ss(line);
    int x;

    while (ss >> x) {
        nums.push_back(x);
    }

    int k;
    cin >> k; // take k separately

    cout << findKthLargest(nums, k);

    return 0;
}
```
