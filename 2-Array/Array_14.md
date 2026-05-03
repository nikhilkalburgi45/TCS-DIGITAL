## Q14 Problem: Print All Subarrays

Given an integer array `nums`, print all possible **contiguous subarrays**.

---

## Example 1

```text
Input: nums = [1,2,3]
Output:
1
1 2
1 2 3
2
2 3
3
```

---

## Example 2

```text id="2a1z6t"
Input: nums = [4,5]
Output:
4
4 5
5
```

---

## Example 3

```text id="91b3xw"
Input: nums = [1]
Output:
1
```

```cpp id="3v6q3m"
#include<iostream>
#include<sstream>
#include<vector>
using namespace std;

// Function to print all subarrays
void printSubarrays(vector<int>& arr) {
    int n = arr.size();

    // Fix starting point
    for(int i = 0; i < n; i++) {

        // Fix ending point
        for(int j = i; j < n; j++) {

            // Print elements from i to j
            for(int k = i; k <= j; k++) {
                cout << arr[k] << " ";
            }
            cout << "\n"; // new line after each subarray
        }
    }
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

    printSubarrays(arr);

    return 0;
}
```
