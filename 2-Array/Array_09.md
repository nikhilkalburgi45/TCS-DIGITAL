## Q9 Problem: Union of Two Arrays

Given two integer arrays `arr1` and `arr2`, return the **union** of both arrays.

The union should contain **distinct elements only**, and the result should be in **sorted order**.

---

## Example 1

```text
Input: arr1 = [1,2,3], arr2 = [2,3,4]
Output: 1 2 3 4
```

---

## Example 2

```text
Input: arr1 = [1,1,2], arr2 = [2,2,3]
Output: 1 2 3
```

---

## Example 3

```text
Input: arr1 = [5,6], arr2 = [1,2,3]
Output: 1 2 3 5 6
```

```cpp
#include <iostream>
#include <vector>
#include <set>
using namespace std;

// Function to find union of two arrays
vector<int> findUnion(vector<int> &arr1, vector<int> &arr2) {
    set<int> st;          // stores unique elements in sorted order
    vector<int> result;   // final answer

    // insert all elements of first array
    for (int x : arr1) {
        st.insert(x);
    }

    // insert all elements of second array
    for (int x : arr2) {
        st.insert(x);
    }

    // move elements from set to result vector
    for (auto it : st) {
        result.push_back(it);
    }

    return result;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n, m;

    cin >> n;
    vector<int> arr1(n);

    // input first array
    for (int i = 0; i < n; i++) {
        cin >> arr1[i];
    }

    cin >> m;
    vector<int> arr2(m);

    // input second array
    for (int i = 0; i < m; i++) {
        cin >> arr2[i];
    }

    // compute union
    vector<int> ans = findUnion(arr1, arr2);

    // output result
    for (int val : ans) {
        cout << val << " ";
    }

    return 0;
}
```
