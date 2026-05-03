## Q18 Problem: Longest Subarray with Sum K

Given an integer array `nums` and an integer `k`, return the **length of the longest contiguous subarray** whose sum equals `k`.

---

## Example 1

```text
Input: nums = [1,2,3,1,1,1,1], k = 3
Output: 3
```

---

## Example 2

```text
Input: nums = [1,2,3,4,5], k = 9
Output: 3
```

---

## Example 3

```text
Input: nums = [2,-1,2,3], k = 3
Output: 3
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
int lengthOflongestSubarray(vector<int> &arr,int k){

    int n = arr.size();
    int maxlength = 0;

    // Fix starting index
    for(int i = 0; i < n; i++){
        int sum = 0;

        // Extend subarray
        for(int j = i; j < n; j++){
            sum += arr[j];

            // Check if sum equals k
            if(sum == k){
                maxlength = max(maxlength, j - i + 1);
            }
        }
    }

    return maxlength;
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

    cout << lengthOflongestSubarray(arr, k);

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
int lengthOflongestSubarray(vector<int> &arr,int k){

    int n = arr.size();
    unordered_map<int,int> mp; // prefix sum → first index

    int sum = 0;
    int maxlength = 0;

    for(int i = 0; i < n; i++){
        sum += arr[i];

        // Case 1: subarray from 0 to i
        if(sum == k){
            maxlength = i + 1;
        }

        // Case 2: subarray exists
        if(mp.find(sum - k) != mp.end()){
            int len = i - mp[sum - k];
            maxlength = max(maxlength, len);
        }

        // Store first occurrence only
        if(mp.find(sum) == mp.end()){
            mp[sum] = i;
        }
    }

    return maxlength;
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

    cout << lengthOflongestSubarray(arr, k);

    return 0;
}
```
