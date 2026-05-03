## Q19 Problem: Count Subarrays with Sum K

Given an integer array `nums` and an integer `k`, return the **total number of contiguous subarrays** whose sum equals `k`.

---

## Example 1

```text id="n2c6hc"
Input: nums = [1,1,1], k = 2
Output: 2
```

---

## Example 2

```text id="3e4h0q"
Input: nums = [1,2,3], k = 3
Output: 2
```

---

## Example 3

```text id="qk6y7n"
Input: nums = [3,4,7,2,-3,1,4,2], k = 7
Output: 4
```

---

### Brute Force Approach

```cpp id="a4b8mp"
#include<iostream>
#include<sstream>
#include<algorithm>
#include<vector>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
int countSubarraysSum(vector<int> &arr,int k){

    int n = arr.size();
    int count = 0;

    // Fix starting index
    for(int i = 0; i < n; i++){
        int sum = 0;

        // Extend subarray
        for(int j = i; j < n; j++){
            sum += arr[j];

            // Check if sum equals k
            if(sum == k){
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

    cout << countSubarraysSum(arr, k);

    return 0;
}
```

---

### Optimal Approach (Prefix Sum + HashMap)

```cpp id="r9m5r3"
#include<iostream>
#include<sstream>
#include<unordered_map>
#include<vector>
using namespace std;

// OPTIMAL: Prefix Sum + HashMap (O(n))
int countSubarraysSum(vector<int> &arr,int k){

    unordered_map<int,int> mp; // prefix sum → frequency
    mp[0] = 1; // base case

    int sum = 0;
    int count = 0;

    for(int i = 0; i < arr.size(); i++){
        sum += arr[i];

        // If (sum - k) exists → valid subarrays found
        if(mp.find(sum - k) != mp.end()){
            count += mp[sum - k];
        }

        // Store prefix sum
        mp[sum]++;
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

    cout << countSubarraysSum(arr, k);

    return 0;
}
```
