## Q23 Problem: Count Number of Nice Subarrays

Given an integer array `nums` and an integer `k`, return the **number of subarrays** with exactly `k` odd numbers.

---

## Example 1

```text
Input: nums = [1,1,2,1,1], k = 3
Output: 2
```

---

## Example 2

```text
Input: nums = [2,4,6], k = 1
Output: 0
```

---

## Example 3

```text
Input: nums = [2,2,2,1,2,2,1,2,2,2], k = 2
Output: 16
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
int countNice(vector<int>& arr,int k) {

    int n = arr.size();
    int count = 0;

    // Fix starting index
    for(int i = 0; i < n; i++){
        int oddCount = 0;

        // Extend subarray
        for(int j = i; j < n; j++){

            // Count odd numbers
            if(arr[j] % 2 == 1){
                oddCount++;
            }

            // If exactly k odds → valid subarray
            if(oddCount == k) {
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

    cout << countNice(arr, k);

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

// OPTIMAL: Prefix Sum (count of odds) + HashMap (O(n))
int countNice(vector<int>& arr,int k) {

    unordered_map<int,int> mp; // prefix odd count → frequency
    mp[0] = 1;

    int oddCount = 0;
    int count = 0;

    for(int i = 0; i < arr.size(); i++){

        // Increment if current element is odd
        if(arr[i] % 2 == 1){
            oddCount++;
        }

        // If (oddCount - k) exists → valid subarrays
        if(mp.find(oddCount - k) != mp.end()){
            count += mp[oddCount - k];
        }

        mp[oddCount]++;
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

    cout << countNice(arr, k);

    return 0;
}
```
