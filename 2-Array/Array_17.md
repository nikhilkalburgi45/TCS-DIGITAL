## Q17 Problem: Subarray with Given Sum (Exists)

Given an integer array `nums` and an integer `k`, return **true** if there exists a **contiguous subarray** whose sum equals `k`, otherwise return **false**.

---

## Example 1

```text id="hsvt0j"
Input: nums = [1,2,3,7,5], k = 12
Output: true
```

---

## Example 2

```text id="0n74fm"
Input: nums = [1,2,3], k = 7
Output: false
```

---

## Example 3

```text id="1xq2w9"
Input: nums = [3,4,-7,1,3,3,1,-4], k = 7
Output: true
```

---

### 🔴 Brute Force Approach

```cpp id="0s6c0r"
#include<iostream>
#include<sstream>
#include<vector>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
bool issubarraySumExists(vector<int> &arr, int k){

    int n = arr.size();

    // Fix starting index
    for(int i = 0; i < n; i++){
        int sum = 0;

        // Extend subarray
        for(int j = i; j < n; j++){
            sum += arr[j];

            // Check if sum equals k
            if(sum == k){
                return true;
            }
        }
    }
    return false;
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

    cout << issubarraySumExists(arr, k);

    return 0;
}
```

---

### 🟢 Optimal Approach (Prefix Sum + Hashing)

```cpp id="h8r6p1"
#include<iostream>
#include<sstream>
#include<unordered_set>
#include<vector>
using namespace std;

// OPTIMAL: Prefix sum + HashSet (O(n))
bool issubarraySumExists(vector<int> &arr, int k){

    int n = arr.size();

    unordered_set<int> st; // stores prefix sums

    int sum = 0;

    for(int i = 0; i < n; i++){

        sum += arr[i]; // running prefix sum

        // Case 1: subarray from 0 to i
        if(sum == k){
            return true;
        }

        // Case 2: subarray exists with sum k
        if(st.count(sum - k)){
            return true;
        }

        st.insert(sum); // store prefix sum
    }

    return false;
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

    cout << issubarraySumExists(arr, k);

    return 0;
}
```
