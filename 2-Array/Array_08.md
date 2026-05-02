## Q8 Problem: Move All Zeros to End

Given an integer array `nums`, move all `0`s to the end while maintaining the relative order of non-zero elements.

---

## Example 1

```text
Input: nums = [0,1,0,3,12]
Output: 1 3 12 0 0
```

---

## Example 2

```text
Input: nums = [0,0,1]
Output: 1 0 0
```

---

## Example 3

```text
Input: nums = [1,2,3]
Output: 1 2 3
```

<!-- Brute force -->

```cpp
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
using namespace std;

// Function to move all zeros to end using extra space
void moveAllZeros(vector<int> &arr){

    int n = arr.size(); // total number of elements

    vector<int> nonZero; // temporary vector to store non-zero elements

    // Step 1: collect all non-zero elements
    for(int i = 0; i < n; i++){
        if(arr[i] != 0){
            nonZero.push_back(arr[i]); // keep order intact
        }
    }

    // Step 2: calculate number of zeros
    int zeroCount = n - nonZero.size();

    // Step 3: append zeros at the end
    for(int i = 0; i < zeroCount; i++){
        nonZero.push_back(0);
    }

    // Step 4: copy back to original array
    for(int i = 0; i < n; i++){
        arr[i] = nonZero[i];
    }
}

int main() {

    int n;
    cin >> n;
    cin.ignore(); // ignore newline after integer input

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [1,2,3] → "1 2 3"
    for (char &ch: line) {
        if (ch == '[' || ch == ']' || ch == ',') {
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);

    int x;

    // Parse input into vector
    while (ss >> x) {
        arr.push_back(x);
    }

    // Validate input size
    if (arr.size() != n) {
        cout << "MisMatch";
        return 0;
    }

    // Move zeros to end
    moveAllZeros(arr);

    // Output final array
    for (int i : arr) {
        cout << i << " ";
    }

    return 0;
}
```

```cpp
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
using namespace std;

// Function to move all zeros to end using two pointers (in-place)
void moveAllZeros(vector<int> &arr){

    int n = arr.size();

    int left = 0; // position to place next non-zero

    for(int right = 0; right < n; right++){
        if(arr[right] != 0){
            swap(arr[left], arr[right]); // bring non-zero forward
            left++;
        }
    }

}

int main() {

    int n;
    cin >> n;
    cin.ignore();

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [1,2,3]
    for (char &ch: line) {
        if (ch == '[' || ch == ']' || ch == ',') {
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);

    int x;

    // Parse input into vector
    while (ss >> x) {
        arr.push_back(x);
    }

    // Validate input size
    if (arr.size() != n) {
        cout << "MisMatch";
        return 0;
    }

    moveAllZeros(arr);

    // Output final array
    for (int i : arr) {
        cout << i << " ";
    }

    return 0;

}
```
