## Q7 Problem: Rotate Array to the Left by D Positions

Given an integer array `nums` and an integer `d`, rotate the array to the left by `d` positions.

---

## Example 1

```text
Input: nums = [1,2,3,4,5], d = 2
Output: 3 4 5 1 2
```

---

## Example 2

```text
Input: nums = [10,20,30,40], d = 1
Output: 20 30 40 10
```

---

## Example 3

```text
Input: nums = [1,2], d = 3
Output: 2 1
```

```cpp
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
using namespace std;

// Function to rotate array left by d positions using reversal algorithm
void rotateByD(vector<int> &arr, int d) {

    int n = arr.size();
    if (n == 0) return;

    d = d % n; // handle d > n

    // Reverse first d elements
    reverse(arr.begin(), arr.begin() + d);

    // Reverse remaining elements
    reverse(arr.begin() + d, arr.end());

    // Reverse entire array
    reverse(arr.begin(), arr.end());
}

int main() {

    int n;
    cin >> n;
    cin.ignore();

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

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

    int d;
    cin >> d;

    if (arr.size() != n) {
        cout << "MisMatch";
        return 0;
    }

    rotateByD(arr, d);

    for (int i : arr) {
        cout << i << " ";
    }

    return 0;
}
```
