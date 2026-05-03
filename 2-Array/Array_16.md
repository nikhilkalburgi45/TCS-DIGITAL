## Q16 Problem: Maximum Subarray Sum

Given an integer array `nums`, find the **contiguous subarray** (containing at least one number) which has the **largest sum**, and return its sum.

---

## Example 1

```text
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
```

---

## Example 2

```text
Input: nums = [1]
Output: 1
```

---

## Example 3

```text
Input: nums = [5,4,-1,7,8]
Output: 23
```

---

### Brute Force Approach

```cpp
#include<iostream>
#include<sstream>
#include<algorithm>
#include<climits>
#include<vector>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
int maxSubarraySum(vector<int>& arr) {
    int n = arr.size();
    int maxi = INT_MIN;

    // Fix starting index
    for(int i = 0; i < n; i++){
        int sum = 0;

        // Extend subarray till end
        for(int j = i; j < n; j++){
            sum += arr[j];              // add current element
            maxi = max(maxi, sum);      // update maximum
        }
    }
    return maxi;
}

int main(){

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [1,2,3]
    for(char &ch : line){
        if(ch == '[' || ch == ']' || ch == ','){
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);

    int x;

    // Parse input
    while(ss >> x){
        arr.push_back(x);
    }

    cout << maxSubarraySum(arr);

    return 0;
}
```

---

### Optimal Approach (Kadane’s Algorithm)

```cpp
#include<iostream>
#include<sstream>
#include<algorithm>
#include<climits>
#include<vector>
using namespace std;

// OPTIMAL: Kadane’s Algorithm (O(n))
int maxSubarraySum(vector<int> &arr) {
    int n = arr.size();

    int sum = 0;        // current running sum
    int maxi = arr[0];  // stores maximum subarray sum

    for(int i = 0; i < n; i++)
    {
        sum += arr[i];              // add current element

        if(sum > maxi){
            maxi = sum;            // update max if needed
        }

        if(sum < 0){
            sum = 0;               // reset if sum becomes negative
        }
    }

    return maxi;
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

    // Parse input
    while (ss >> x) {
        arr.push_back(x);
    }

    cout << maxSubarraySum(arr);

    return 0;
}
```
