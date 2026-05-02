## Q1 Problem: Find Largest and Smallest Element in an Array

Given an integer array `nums`, return the **maximum** and **minimum** element present in the array.

### Example 1

```
Input: nums = [3, 5, 1, 8, 2]

Output: 8 1
```

### Example 2

```
Input: nums = [10]

Output: 10 10
```

```cpp
#include <iostream>
#include <vector>
#include <sstream>
using namespace std;

// Function to find largest element
int largest(vector<int> &arr) {
    int n = arr.size();

    int maxi = arr[0]; // assume first element is max initially

    // Traverse rest of array
    for (int i = 1; i < n; i++) {
        if (arr[i] > maxi) {
            maxi = arr[i]; // update if bigger found
        }
    }
    return maxi;
}

// Function to find smallest element
int smallest(vector<int> &arr) {
    int n = arr.size();

    int mini = arr[0]; // assume first element is min initially

    // Traverse rest of array
    for (int i = 1; i < n; i++) {
        if (arr[i] < mini) {
            mini = arr[i]; // update if smaller found
        }
    }

    return mini;
}

int main() {
    string line;

    // Take input like: [1,2,3,4]
    getline(cin, line);

    // Replace unwanted characters with space
    for (char &ch : line) {
        if (ch == '[' || ch == ']' || ch == ',') {
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);
    int x;

    // Convert string to integers
    while (ss >> x) {
        arr.push_back(x);
    }

    // Output: max and min
    cout << largest(arr) << " ";
    cout << smallest(arr);

    return 0;
}
```
