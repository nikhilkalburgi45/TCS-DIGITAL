## Q12 Problem: Maximum Consecutive Ones

Given a binary array `nums`, return the **maximum number of consecutive `1`s** in the array.

---

## Example 1

```text
Input: nums = [1,1,0,1,1,1]
Output: 3
```

---

## Example 2

```text
Input: nums = [1,0,1,1,0,1]
Output: 2
```

---

## Example 3

```text
Input: nums = [0,0,0]
Output: 0
```

```cpp
#include<iostream>
#include<sstream>
#include<vector>
#include<algorithm>  // for max()
using namespace std;

// Function to find maximum consecutive 1s
int maxOnes(vector<int> &arr){

    int count = 0;     // current streak of 1s
    int maxCount = 0;  // maximum streak found

    for(int x : arr){
        if(x == 1){
            count++; // extend current streak
            maxCount = max(maxCount, count); // update max
        } else {
            count = 0; // reset streak if 0 found
        }
    }

    return maxCount;
}

int main(){

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [1,0,1]
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

    cout << maxOnes(arr);

    return 0;
}
```
