## Q23 Problem: Longest Subarray with Sum ≤ K

Given an integer array `nums` and an integer `k`, return the **length of the longest contiguous subarray** whose sum is **less than or equal to `k`**.

---

## Example 1

```text id="3qk6ht"
Input: nums = [1,2,1,0,1], k = 4
Output: 4
```

---

## Example 2

```text id="6k0e9q"
Input: nums = [2,1,3,2], k = 5
Output: 2
```

---

## Example 3

```text id="9p1h3u"
Input: nums = [5,6,7], k = 4
Output: 0
```

---

### Brute Force Approach

```cpp id="6x4p5b"
#include<iostream>
#include<sstream>
#include<algorithm>
#include<vector>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
int longestSubarrayLessThanK(vector<int>& arr,int k) {

    int n = arr.size();
    int maxLen = 0;

    // Fix starting index
    for(int i = 0; i < n; i++){
        int sum = 0;

        // Extend subarray
        for(int j = i; j < n; j++){
            sum += arr[j];

            // If sum ≤ k, update answer
            if(sum <= k){
                maxLen = max(maxLen, j - i + 1);
            } else {
                break; // no need to continue
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

    int k;
    cin >> k;

    cout << longestSubarrayLessThanK(arr, k);

    return 0;
}
```

---

### Optimal Approach (Sliding Window – Only for Non-Negative Arrays)

```cpp id="t4b6n9"
#include<iostream>
#include<sstream>
#include<vector>
#include<algorithm>
using namespace std;

// OPTIMAL: Sliding Window (O(n)) – works when all elements ≥ 0
int longestSubarrayLessThanK(vector<int>& arr,int k) {

    int n = arr.size();

    int left = 0;
    int sum = 0;
    int maxLen = 0;

    for(int right = 0; right < n; right++){

        sum += arr[right]; // expand window

        // shrink window if sum > k
        while(sum > k && left <= right){
            sum -= arr[left];
            left++;
        }

        // valid window
        if(sum <= k){
            maxLen = max(maxLen, right - left + 1);
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

    int k;
    cin >> k;

    cout << longestSubarrayLessThanK(arr, k);

    return 0;
}
```
