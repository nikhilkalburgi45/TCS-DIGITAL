## Q21 Problem: Count Subarrays with Equal Number of 0s and 1s

Given a binary array `nums`, return the **count of subarrays** with an equal number of `0`s and `1`s.

---

## Example 1

```text id="e9f6e3"
Input: nums = [0,1]
Output: 1
```

---

## Example 2

```text id="g2n4q1"
Input: nums = [0,1,0]
Output: 2
```

---

## Example 3

```text id="t7v9l2"
Input: nums = [1,1,0,0]
Output: 4
```

---

### Brute Force Approach

```cpp id="k3h8p0"
#include<iostream>
#include<sstream>
#include<algorithm>
#include<vector>
using namespace std;

// BRUTE FORCE: Convert 0 → -1, then count subarrays with sum = 0 (O(n^2))
int countSubarraysZerosAndOnes(vector<int>& arr) {

    int n = arr.size();
    int count = 0;

    // Convert 0 to -1
    for(int i = 0; i < n; i++){
        if(arr[i] == 0){
            arr[i] = -1;
        }
    }

    // Check all subarrays
    for(int i = 0; i < n; i++){
        int sum = 0;
        for(int j = i; j < n; j++){
            sum += arr[j];

            if(sum == 0){
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

    // Clean input like [0,1,0]
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

    cout << countSubarraysZerosAndOnes(arr);

    return 0;
}
```

---

### Optimal Approach (Prefix Sum + HashMap)

```cpp id="n5q2z8"
#include<iostream>
#include<sstream>
#include<unordered_map>
#include<vector>
using namespace std;

// OPTIMAL: Prefix Sum + HashMap (O(n))
int countSubarraysZerosAndOnes(vector<int>& arr) {

    int n = arr.size();

    // Convert 0 to -1
    for(int i = 0; i < n; i++){
        if(arr[i] == 0){
            arr[i] = -1;
        }
    }

    unordered_map<int,int> mp; // prefix sum → frequency
    mp[0] = 1;

    int sum = 0;
    int count = 0;

    for(int i = 0; i < n; i++){
        sum += arr[i];

        // If prefix sum seen before, subarrays exist
        if(mp.find(sum) != mp.end()){
            count += mp[sum];
        }

        mp[sum]++;
    }

    return count;
}

int main() {

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [0,1,0]
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

    cout << countSubarraysZerosAndOnes(arr);

    return 0;
}
```
