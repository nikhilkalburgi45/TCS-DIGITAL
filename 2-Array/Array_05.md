## Q5 Problem: Rotate Array to the Left by One Position

Given an integer array `nums`, rotate the array to the left by one position.

---

## Example 1

```text
Input: nums = [1,2,3,4,5]
Output: 2 3 4 5 1
```

---

## Example 2

```text
Input: nums = [10,20,30]
Output: 20 30 10
```

---

## Example 3

```text
Input: nums = [1]
Output: 1
```

```cpp
#include <iostream>
#include <vector>
#include <sstream>
using namespace std;

// Function to rotate array left by one position
void rotateLeft(vector<int> &arr) {
    int n = arr.size();

    if (n == 0) return; // safety

    int temp = arr[0]; // store first element

    // shift all elements one step left
    for (int i = 0; i < n - 1; i++) {
        arr[i] = arr[i + 1];
    }

    arr[n - 1] = temp; // place first element at end
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n;
    cin >> n;
    cin.ignore(); // to handle newline after integer input

    string line;
    getline(cin, line);

    // Clean input like [1,2,3]
    for (char &ch : line) {
        if (ch == '[' || ch == ']' || ch == ',') {
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);

    int x;
    while (ss >> x) {
        arr.push_back(x);
    }

    rotateLeft(arr);

    // Output rotated array
    for (int val : arr) {
        cout << val << " ";
    }

    return 0;
}
```
