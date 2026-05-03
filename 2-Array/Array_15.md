## Q15 Problem: Count Total Number of Subarrays

Given an integer array `nums`, return the **total number of contiguous subarrays**.

---

## Example 1

```text
Input: nums = [1,2,3]
Output: 6
```

---

## Example 2

```text
Input: nums = [4,5]
Output: 3
```

---

## Example 3

```text
Input: nums = [1]
Output: 1
```

```cpp
#include<iostream>
#include<sstream>
#include<vector>
using namespace std;

// Function to count total number of subarrays
int countSubarrays(vector<int> &arr){
    
    int n = arr.size();
    int count = 0;
    
    // Fix starting index
    for(int i = 0; i < n; i++){
        
        // Fix ending index
        for(int j = i; j < n; j++){
            count++; // each (i, j) represents one subarray
        }
    }
    
    return count;
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
    
    // Parse input into vector
    while(ss >> x){
        arr.push_back(x);
    }
    
    cout << countSubarrays(arr);
    
    return 0;
}
```