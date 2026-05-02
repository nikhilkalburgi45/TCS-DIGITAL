## Q4 Problem: Remove Duplicates from Sorted Array

Given a **sorted** integer array `nums`, remove the duplicates **in-place** such that each element appears only once and return the new length.

The relative order of the elements should be kept the same.

---

## Example 1

```text
Input: nums = [1,1,2]
Output: 2
```

---

## Example 2

```text
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5
```

---

## Example 3

```text
Input: nums = [1,2,3]
Output: 3
```

```cpp
#include<iostream>
#include<vector>
#include<sstream>
using namespace std;

// Function to remove duplicates from sorted array
int removeDuplicates(vector<int> &arr){

    int n = arr.size();
    if(n == 0) return 0;

    int left = 0; // points to last unique element

    for(int right = 1; right < n; right++){
        if(arr[left] != arr[right]){
            left++;
            arr[left] = arr[right]; // place next unique element
        }
    }
    return left + 1; // length of unique elements
}

int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

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

    cout << removeDuplicates(arr);

    return 0;
}
```
