## Q24 Problem: Minimum Size Subarray Sum

Given an integer array `nums` and an integer `target`, return the **minimal length of a contiguous subarray** of which the sum is **greater than or equal to `target`**. If there is no such subarray, return `0`.

---

## Example 1

```text id="s1m8rt"
Input: nums = [2,3,1,2,4,3], target = 7
Output: 2
```

---

## Example 2

```text id="t9v3hk"
Input: nums = [1,4,4], target = 4
Output: 1
```

---

## Example 3

```text id="k2c7pz"
Input: nums = [1,1,1,1,1], target = 11
Output: 0
```

---

### Brute Force Approach

```cpp id="h4y8x1"
#include<iostream>
#include<sstream>
#include<algorithm>
#include<vector>
#include<climits>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
int minSubarrayLen(vector<int>& arr,int target) {

    int n = arr.size();
    int minLen = INT_MAX;

    // Fix starting index
    for(int i = 0; i < n; i++){
        int sum = 0;

        // Extend subarray
        for(int j = i; j < n; j++){

            sum += arr[j];

            // Check if sum ≥ target
            if(sum >= target){
                minLen = min(minLen, j - i + 1);
                break; // no need to extend further
            }
        }
    }

    // If no valid subarray found
    return (minLen == INT_MAX) ? 0 : minLen;
}

int main() {

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [1,2,3]
    for (char &ch: line) {
        if (ch == '[' || ch == ']' || ch == ',') {
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);

    int x;
    while (ss >> x) {
        arr.push_back(x);
    }

    int target;
    cin >> target;

    cout << minSubarrayLen(arr, target);

    return 0;
}
```

---

### Optimal Approach (Sliding Window – For Positive Integers)

```cpp id="m8q2p4"
#include<iostream>
#include<sstream>
#include<vector>
#include<algorithm>
using namespace std;

// OPTIMAL: Sliding Window (O(n)) – works when all elements are positive
int minSubarrayLen(vector<int>& arr,int target) {

    int n = arr.size();

    int left = 0;
    int sum = 0;
    int minLen = INT_MAX;

    for(int right = 0; right < n; right++){

        sum += arr[right]; // expand window

        // shrink window while condition satisfied
        while(sum >= target){
            minLen = min(minLen, right - left + 1);
            sum -= arr[left];
            left++;
        }
    }

    return (minLen == INT_MAX) ? 0 : minLen;
}

int main() {

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [1,2,3]
    for (char &ch: line) {
        if (ch == '[' || ch == ']' || ch == ',') {
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);

    int x;
    while (ss >> x) {
        arr.push_back(x);
    }

    int target;
    cin >> target;

    cout << minSubarrayLen(arr, target);

    return 0;
}
```
