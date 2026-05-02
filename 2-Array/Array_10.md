## Q10 Problem: Intersection of Two Sorted Arrays

Given two **sorted** integer arrays `arr1` and `arr2`, return their **intersection**.

The intersection should contain elements present in both arrays. If duplicates exist, include them as many times as they appear in both arrays.

---

## Example 1

```text
Input: arr1 = [1,2,2,3], arr2 = [2,2,4]
Output: 2 2
```

---

## Example 2

```text
Input: arr1 = [1,2,3], arr2 = [4,5,6]
Output:
```

---

## Example 3

```text
Input: arr1 = [1,1,2,3], arr2 = [1,2,2,3]
Output: 1 2 3
```

```cpp
#include<iostream>
#include<sstream>
#include<vector>
#include<algorithm>
using namespace std;

// Function to parse input string into vector
vector<int> parse(string line){

    // Clean input like [1,2,3] → "1 2 3"
    for(char &ch : line){
        if(ch == '[' || ch == ']' || ch == ','){
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);
    int x;

    // Convert string to integers
    while(ss >> x){
        arr.push_back(x);
    }

    return arr;
}

// Function to find intersection of two sorted arrays
vector<int> interSection(vector<int> &arr1, vector<int> &arr2){

    int n = arr1.size();
    int m = arr2.size();

    int left = 0, right = 0;
    vector<int> ans;

    // Two pointer traversal
    while(left < n && right < m){
        if(arr1[left] < arr2[right]){
            left++; // move left pointer
        }
        else if(arr1[left] > arr2[right]){
            right++; // move right pointer
        }
        else{
            // common element found
            ans.push_back(arr1[left]);
            left++;
            right++;
        }
    }
    return ans;
}

int main(){

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n, m;
    cin >> n >> m;
    cin.ignore();

    string line1, line2;
    getline(cin, line1);
    getline(cin, line2);

    vector<int> arr1 = parse(line1);
    vector<int> arr2 = parse(line2);

    // Find intersection
    vector<int> r = interSection(arr1, arr2);

    // Output result
    for(int x : r){
        cout << x << " ";
    }

    return 0;
}
```
