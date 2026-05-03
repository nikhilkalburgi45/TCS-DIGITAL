## Q25 Problem: Count Subarrays with Sum Divisible by K

Given an integer array `nums` and an integer `k`, return the **number of subarrays whose sum is divisible by `k`**.

---

## Example 1

```text id="2y9m1u"
Input: nums = [4,5,0,-2,-3,1], k = 5
Output: 7
```

---

## Example 2

```text id="v3x8q0"
Input: nums = [5], k = 9
Output: 0
```

---

## Example 3

```text id="l0b7t2"
Input: nums = [2,-2,2,-4], k = 3
Output: 2
```

---

### Brute Force Approach

```cpp id="k1c4vn"
#include<iostream>
#include<sstream>
#include<algorithm>
#include<vector>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
int countSubarraysDivisibleByK(vector<int>& arr,int k) {

    int n = arr.size();
    int count = 0;

    // Fix starting index
    for(int i = 0; i < n; i++){
        int sum = 0;

        // Extend subarray
        for(int j = i; j < n; j++){
            sum += arr[j];

            // Check if sum divisible by k
            if(sum % k == 0){
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

    cout << countSubarraysDivisibleByK(arr, k);

    return 0;
}
```

---

### Optimal Approach (Prefix Sum + HashMap)

```cpp id="r8v5hz"
#include<iostream>
#include<sstream>
#include<unordered_map>
#include<vector>
using namespace std;

// OPTIMAL: Prefix Sum + HashMap (O(n))
int countSubarraysDivisibleByK(vector<int>& arr,int k) {

    unordered_map<int,int> mp; // remainder → frequency
    mp[0] = 1;

    int sum = 0;
    int count = 0;

    for(int i = 0; i < arr.size(); i++){
        sum += arr[i];

        int rem = sum % k;

        // handle negative remainder
        if(rem < 0) rem += k;

        if(mp.find(rem) != mp.end()){
            count += mp[rem];
        }

        mp[rem]++;
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

    cout << countSubarraysDivisibleByK(arr, k);

    return 0;
}
```
