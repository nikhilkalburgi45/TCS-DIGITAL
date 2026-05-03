## Q33 Problem: Leaders in an Array

Given an integer array `nums`, return all **leaders** in the array.

An element is called a **leader** if it is **greater than or equal to all elements to its right**.

---

## Example 1

```text id="9f2k1p"
Input: nums = [16,17,4,3,5,2]
Output: 17 5 2
```

---

## Example 2

```text id="m7t3z8"
Input: nums = [1,2,3,4,5]
Output: 5
```

---

## Example 3

```text id="x4p8q1"
Input: nums = [5,4,3,2,1]
Output: 5 4 3 2 1
```

---

### 🟢 Optimal Approach (Traverse from Right)

```cpp id="s6k3bv"
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
#include<climits>
using namespace std;

// OPTIMAL: Traverse from right (O(n))
vector<int> leader(vector<int> &arr){
    
    int n = arr.size();
    
    vector<int> leaders;
    
    int maxRight = arr[n - 1]; // last element is always a leader
    leaders.push_back(maxRight);
    
    // Traverse from second last to start
    for(int i = n - 2; i >= 0; i--){
        
        // If current element >= max on right → leader
        if(arr[i] >= maxRight){
            leaders.push_back(arr[i]);
            maxRight = arr[i]; // update maxRight
        }
    }
    
    // Reverse to maintain original order
    reverse(leaders.begin(), leaders.end());
    
    return leaders;
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
    
    vector<int> ans = leader(arr);
    
    // Output leaders
    for(int i : ans){
        cout << i << " ";
    }
}
```
