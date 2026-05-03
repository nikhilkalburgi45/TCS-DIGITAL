## Q28 Problem: Two Sum

Given an integer array `nums` and an integer `target`, return **indices of the two numbers** such that they add up to `target`.

Assume:

- Exactly one solution exists
- You cannot use the same element twice

---

## Example 1

```text id="n8z4kp"
Input: nums = [2,7,11,15], target = 9
Output: 0 1
```

---

## Example 2

```text id="y2v6cm"
Input: nums = [3,2,4], target = 6
Output: 1 2
```

---

## Example 3

```text id="k7p3qd"
Input: nums = [3,3], target = 6
Output: 0 1
```

---

### Brute Force Approach

```cpp id="w3c9mf"
#include<iostream>
#include<vector>
#include<sstream>
using namespace std;

// BRUTE FORCE: Check all pairs (O(n^2))
vector<int> twoSum(vector<int> &arr,int target){

    int n = arr.size();

    for(int i = 0; i < n; i++){
        for(int j = i + 1; j < n; j++){

            // Check if pair sums to target
            if(arr[i] + arr[j] == target){
                return {i, j};
            }
        }
    }

    return {-1, -1};

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

    // Parse input
    while(ss >> x){
        arr.push_back(x);
    }

    int target;
    cin >> target;

    vector<int> result = twoSum(arr, target);

    for(int i : result){
        cout << i << " ";
    }
}
```

---

### Optimal Approach (HashMap)

```cpp id="u7q2lx"
#include<iostream>
#include<vector>
#include<sstream>
#include<unordered_map>
using namespace std;

// OPTIMAL: HashMap (O(n))
vector<int> twoSum(vector<int> &arr,int target){

    unordered_map<int,int> mpp; // value → index

    for(int i = 0; i < arr.size(); i++){

        int need = target - arr[i]; // required value

        // If complement exists
        if(mpp.count(need)){
            return {mpp[need], i};
        }

        // Store current element
        mpp[arr[i]] = i;
    }

    return {-1, -1};
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

    // Parse input
    while(ss >> x){
        arr.push_back(x);
    }

    int target;
    cin >> target;

    vector<int> result = twoSum(arr, target);

    for(int i : result){
        cout << i << " ";
    }
}
```
