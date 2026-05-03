## Q13 Problem: Single Number

Given a non-empty integer array `nums`, every element appears **twice** except for one. Find that **single unique element**.

---

## Example 1

```text id="u4z9k7"
Input: nums = [2,2,1]
Output: 1
```

---

## Example 2

```text id="fj3xqp"
Input: nums = [4,1,2,1,2]
Output: 4
```

---

## Example 3

```text id="6saxlb"
Input: nums = [1]
Output: 1
```

```cpp id="3q0t6n"
#include<iostream>
#include<sstream>
#include<vector>
using namespace std;

// Function to find the single number using XOR
int uniQue(vector<int> &arr){

    int xoRR = 0; // XOR accumulator

    // XOR all elements
    // Property: a ^ a = 0 and a ^ 0 = a
    for(int x : arr){
        xoRR ^= x;
    }

    return xoRR; // remaining value is the unique element
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

    cout << uniQue(arr);

    return 0;
}
```
