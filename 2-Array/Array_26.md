## Q26 Problem: Count Subarrays with XOR = K

Given an integer array `nums` and an integer `k`, return the **number of subarrays** whose **XOR equals `k`**.

---

## Example 1

```text id="p7v4q1"
Input: nums = [4,2,2,6,4], k = 6
Output: 4
```

---

## Example 2

```text id="c9l2t8"
Input: nums = [5,6,7,8,9], k = 5
Output: 2
```

---

## Example 3

```text id="x2r6m3"
Input: nums = [1,1,1,1], k = 0
Output: 4
```

---

### Brute Force Approach

```cpp id="v5j3ds"
#include<iostream>
#include<sstream>
#include<vector>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
int countSubarraysXork(vector<int>& arr,int k) {

    int n = arr.size();
    int count = 0;

    // Fix starting index
    for(int i = 0; i < n; i++){
        int xoRR = 0;

        // Extend subarray
        for(int j = i; j < n; j++){

            xoRR ^= arr[j]; // update XOR

            // Check if XOR equals k
            if(xoRR == k){
                count++;
            }
        }
    }

    return count;
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

    cout << countSubarraysXork(arr, k);

    return 0;
}
```

---

### Optimal Approach (Prefix XOR + HashMap)

```cpp id="h8k1mz"
#include<iostream>
#include<sstream>
#include<unordered_map>
#include<vector>
using namespace std;

// OPTIMAL: Prefix XOR + HashMap (O(n))
int countSubarraysXork(vector<int>& arr,int k) {

    unordered_map<int,int> mp; // prefix XOR → frequency
    mp[0] = 1;

    int xoRR = 0;
    int count = 0;

    for(int i = 0; i < arr.size(); i++){

        xoRR ^= arr[i]; // prefix XOR

        // Required prefix XOR
        int target = xoRR ^ k;

        if(mp.find(target) != mp.end()){
            count += mp[target];
        }

        mp[xoRR]++;
    }

    return count;
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

    cout << countSubarraysXork(arr, k);

    return 0;
}
```
