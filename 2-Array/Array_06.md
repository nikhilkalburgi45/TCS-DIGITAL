## Q6 Problem: Rotate Array to the Right by One Position

Given an integer array `nums`, rotate the array to the right by one position.

---

## Example 1

```text
Input: nums = [1,2,3,4,5]
Output: 5 1 2 3 4
```

---

## Example 2

```text
Input: nums = [10,20,30]
Output: 30 10 20
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

// Function to rotate array right by one position
void rotateRight(vector<int> &arr) {
    int n = arr.size();

    if (n == 0) return; // safety

    int temp = arr[n - 1]; // store last element

    // shift all elements one step right
    for (int i = n - 1; i > 0; i--) {
        arr[i] = arr[i - 1];
    }

    arr[0] = temp; // place last element at front
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n;
    cin >> n;
    cin.ignore();

    string line;
    getline(cin, line);

    // sanitize input
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

    // optional strict validation
    if (arr.size() != n) {
        cout << "Input size mismatch\n";
        return 0;
    }

    rotateRight(arr);

    // OUTPUT
    for (int val : arr) {
        cout << val << " ";
    }

    return 0;
}
```
