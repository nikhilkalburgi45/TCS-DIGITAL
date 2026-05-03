## Q31 Problem: Rearrange Array Elements by Sign

Given an integer array `nums` containing equal number of positive and negative elements, rearrange the array such that:

- Positive and negative numbers alternate  
- The first element is **positive**  
- Relative order of elements should be maintained  

---

## Example 1

```text
Input: nums = [3,1,-2,-5,2,-4]
Output: 3 -2 1 -5 2 -4
```

---

## Example 2

```text
Input: nums = [1,-1]
Output: 1 -1
```

---

## Example 3

```text
Input: nums = [5,-3,4,-2]
Output: 5 -3 4 -2
```

```cpp
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
using namespace std;

// Function to rearrange positives and negatives alternately
void rearrangeBits(vector<int> &arr){
    
    int n = arr.size();
    
    vector<int> pos; // store positive numbers
    vector<int> neg; // store negative numbers
    
    // Separate positives and negatives
    for(int i = 0; i < n; i++){
        if(arr[i] > 0){
            pos.push_back(arr[i]);
        } else {
            neg.push_back(arr[i]);
        }
    }
    
    // Merge alternately: positive at even index, negative at odd index
    for(int i = 0; i < n/2; i++){
        arr[2*i] = pos[i];
        arr[2*i + 1] = neg[i];
    }
}

int main(){
    
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    string line;
    getline(cin,line);
    
    // Clean input like [1,-2,3]
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
    
    rearrangeBits(arr);
    
    // Output result
    for(int i : arr){
        cout << i << " ";
    }
}
```