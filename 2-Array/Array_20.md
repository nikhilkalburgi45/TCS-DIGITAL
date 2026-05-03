## Q20 Problem: Largest Subarray with Sum = 0

Given an integer array `nums`, return the **length of the longest contiguous subarray** whose sum is equal to `0`.

---

## Example 1

```text
Input: nums = [1,-1,3,2,-2,-3,3]
Output: 6
```

---

## Example 2

```text
Input: nums = [1,2,3]
Output: 0
```

---

## Example 3

```text
Input: nums = [1,-1]
Output: 2
```

---

### Brute Force Approach

```cpp
#include<iostream>
#include<sstream>
#include<algorithm>
#include<vector>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
int largestZeroSumSubarray(vector<int>& arr) {

    int n = arr.size();
    int maxLen = 0;

    // Fix starting index
    for(int i = 0; i < n; i++) {
        int sum = 0;

        // Extend subarray
        for(int j = i; j < n; j++) {
            sum += arr[j];

            // Check if sum becomes zero
            if(sum == 0) {
                maxLen = max(maxLen, j - i + 1);
            }
        }
    }

    return maxLen;
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

    cout << largestZeroSumSubarray(arr);

    return 0;
}
```

---

### Optimal Approach (Prefix Sum + HashMap)

```cpp
#include<iostream>
#include<sstream>
#include<unordered_map>
#include<vector>
using namespace std;

// OPTIMAL: Prefix Sum + HashMap (O(n))
int largestZeroSumSubarray(vector<int>& arr) {

    unordered_map<int,int> mp; // prefix sum → first index

    int sum = 0;
    int maxLen = 0;

    for(int i = 0; i < arr.size(); i++) {
        sum += arr[i];

        // Case 1: subarray from 0 to i
        if(sum == 0) {
            maxLen = i + 1;
        }

        // Case 2: seen this sum before
        if(mp.find(sum) != mp.end()) {
            int len = i - mp[sum];
            maxLen = max(maxLen, len);
        } else {
            mp[sum] = i; // store first occurrence
        }
    }

    return maxLen;
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

    cout << largestZeroSumSubarray(arr);

    return 0;
}
```
