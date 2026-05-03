## Q27 Problem: Maximum Product Subarray

Given an integer array `nums`, find the **contiguous subarray** within the array that has the **largest product**, and return the product.

---

## Example 1

```text id="j1x9ps"
Input: nums = [2,3,-2,4]
Output: 6
```

---

## Example 2

```text id="l7c4zn"
Input: nums = [-2,0,-1]
Output: 0
```

---

## Example 3

```text id="p8t5qy"
Input: nums = [-2,3,-4]
Output: 24
```

---

### Brute Force Approach

```cpp id="z6f2rb"
#include<iostream>
#include<sstream>
#include<algorithm>
#include<vector>
#include<climits>
using namespace std;

// BRUTE FORCE: Check all subarrays (O(n^2))
int maxProduct(vector<int>& arr) {
    
    int n = arr.size();
    int maxi = INT_MIN;
    
    // Fix starting index
    for(int i = 0; i < n; i++){
        int prod = 1;

        // Extend subarray
        for(int j = i; j < n; j++){
            
            prod *= arr[j];           // update product
            maxi = max(maxi, prod);   // update maximum
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
    while (ss >> x) {
        arr.push_back(x);
    }

    cout << maxProduct(arr);

    return 0;
}
```

---

### Optimal Approach (Kadane Variant with Min/Max Tracking)

```cpp id="w9q3ks"
#include<iostream>
#include<sstream>
#include<vector>
#include<algorithm>
using namespace std;

// OPTIMAL: Track max and min product (O(n))
int maxProduct(vector<int>& arr) {
    
    int n = arr.size();
    
    int currMax = arr[0];
    int currMin = arr[0];
    int result = arr[0];
    
    for(int i = 1; i < n; i++){
        
        // If negative, swap because sign flips
        if(arr[i] < 0){
            swap(currMax, currMin);
        }
        
        currMax = max(arr[i], currMax * arr[i]);
        currMin = min(arr[i], currMin * arr[i]);
        
        result = max(result, currMax);
    }
    
    return result;
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

    cout << maxProduct(arr);

    return 0;
}
```
