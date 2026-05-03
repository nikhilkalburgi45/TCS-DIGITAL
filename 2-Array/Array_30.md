## Q30 Problem: Majority Element

Given an integer array `nums` of size `n`, return the **majority element**.

The majority element is the element that appears **more than ⌊n/2⌋ times**.
If no such element exists, return `-1`.

---

## Example 1

```text id="v3c8q1"
Input: nums = [3,2,3]
Output: 3
```

---

## Example 2

```text id="m2p9kd"
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```

---

## Example 3

```text id="b7x4ra"
Input: nums = [1,2,3]
Output: -1
```

---

### 🔴 Brute Force Approach

```cpp id="d8y4lp"
#include<iostream>
#include<vector>
#include<sstream>
using namespace std;

// BRUTE FORCE: Check frequency of each element (O(n^2))
int majorityElement(vector<int> &arr){
    
    int n = arr.size();
    
    for(int i = 0; i < n; i++){
        int count = 0; // reset for each i
        
        for(int j = 0; j < n; j++){
            if(arr[i] == arr[j]){
                count++;
            }
        }
        
        // Check if majority
        if(count > n/2){
            return arr[i];
        }
    }
    
    return -1;
}

int main(){
    
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    string line;
    getline(cin,line);
    
    // Clean input like [1,2,3]
    for(char &ch : line){
        if(ch == '[' || ch == ']' || ch == ','){
            ch = ' ';
        }
    }
    
    vector<int> arr;
    stringstream ss(line);
    int x;
    
    while(ss >> x){
        arr.push_back(x);
    }

    cout << majorityElement(arr);
}
```

---

### 🟡 Better Approach (HashMap)

```cpp id="w5r2js"
#include<iostream>
#include<vector>
#include<sstream>
#include<unordered_map>
using namespace std;

// BETTER: Use HashMap to count frequency (O(n))
int majorityElement(vector<int> &arr){
    
    int n = arr.size();
    unordered_map<int,int> mpp;
    
    // Count frequency
    for(int i = 0; i < n; i++){
        mpp[arr[i]]++;
    }
    
    // Check majority
    for(auto it : mpp){
        if(it.second > n/2){
            return it.first;
        }
    }
    
    return -1;
}

int main(){
    
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    string line;
    getline(cin,line);
    
    // Clean input
    for(char &ch : line){
        if(ch == '[' || ch == ']' || ch == ','){
            ch = ' ';
        }
    }
    
    vector<int> arr;
    stringstream ss(line);
    int x;
    
    while(ss >> x){
        arr.push_back(x);
    }

    cout << majorityElement(arr);
}
```

---

### 🟢 Optimal Approach (Moore’s Voting Algorithm)

```cpp id="q9k3zt"
#include<iostream>
#include<vector>
#include<sstream>
using namespace std;

// OPTIMAL: Moore's Voting Algorithm (O(n), O(1))
int majorityElement(vector<int> &arr){
    
    int count = 0;
    int candidate = 0;
    
    // Step 1: Find candidate
    for(int x : arr){
        if(count == 0){
            candidate = x;
        }
        
        if(x == candidate){
            count++;
        } else {
            count--;
        }
    }
    
    // Step 2: Verify candidate
    count = 0;
    for(int x : arr){
        if(x == candidate){
            count++;
        }
    }
    
    return (count > arr.size()/2) ? candidate : -1;
}

int main(){
    
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    string line;
    getline(cin,line);
    
    // Clean input
    for(char &ch : line){
        if(ch == '[' || ch == ']' || ch == ','){
            ch = ' ';
        }
    }
    
    vector<int> arr;
    stringstream ss(line);
    int x;
    
    while(ss >> x){
        arr.push_back(x);
    }

    cout << majorityElement(arr);
}
```
