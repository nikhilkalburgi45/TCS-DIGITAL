## Q11 Problem: Missing Number

Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the **only number missing** from the array.

---

## Example 1

```text
Input: nums = [3,0,1]
Output: 2
```

---

## Example 2

```text
Input: nums = [0,1]
Output: 2
```

---

## Example 3

```text
Input: nums = [9,6,4,2,3,5,7,0,1]
Output: 8
```

```cpp
#include<iostream>
#include<vector>
#include<sstream>
using namespace std;

// Function to find missing number using sum formula
int missingNumber(vector<int> &arr){

    int n = arr.size();

    // Expected sum of numbers from 0 to n
    int expected = n * (n + 1) / 2;

    int sum = 0;

    // Compute actual sum of array elements
    for(int i = 0; i < n; i++){
        sum += arr[i];
    }

    // Missing number = expected sum - actual sum
    return expected - sum;
}

int main()
{
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

    cout << missingNumber(arr);

    return 0;
}
```
