## Q29 Problem: Sort Colors (Dutch National Flag Problem)

Given an array `nums` with `n` objects colored `0`, `1`, and `2`, sort them **in-place** so that objects of the same color are adjacent, with the order: `0 → 1 → 2`.

---

## Example 1

```text
Input: nums = [2,0,2,1,1,0]
Output: 0 0 1 1 2 2
```

---

## Example 2

```text
Input: nums = [2,0,1]
Output: 0 1 2
```

---

## Example 3

```text
Input: nums = [0]
Output: 0
```

---

### Better Approach (Counting Method)

```cpp
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
#include<unordered_map>
using namespace std;

// BETTER: Count 0s, 1s, 2s then overwrite (O(n))
void sortColors(vector<int> &arr){

    int n = arr.size();

    int zero = 0;
    int one = 0;
    int two = 0;

    // Count occurrences
    for(int i = 0; i < n; i++){
        if(arr[i] == 0){
            zero++;
        } else if(arr[i] == 1){
            one++;
        } else {
            two++;
        }
    }

    int i = 0;

    // Fill 0s
    while(zero--){
        arr[i++] = 0;
    }

    // Fill 1s
    while(one--){
        arr[i++] = 1;
    }

    // Fill 2s
    while(two--){
        arr[i++] = 2;
    }
}

int main(){

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [2,0,1]
    for(char &ch : line){
        if(ch == '[' || ch == ']' || ch == ','){
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);
    int x;

    while(ss >> x){
        arr.push_back(x);
    }

    sortColors(arr);

    for(int i : arr){
        cout << i << " ";
    }
}
```

---

### Optimal Approach (Dutch National Flag - 3 Pointers)

```cpp
#include<iostream>
#include<vector>
#include<sstream>
using namespace std;

// OPTIMAL: 3 pointers (O(n), single pass)
void sortColors(vector<int> &arr){

    int low = 0, mid = 0, high = arr.size() - 1;

    while(mid <= high){

        if(arr[mid] == 0){
            swap(arr[low], arr[mid]);
            low++;
            mid++;
        }
        else if(arr[mid] == 1){
            mid++;
        }
        else{
            swap(arr[mid], arr[high]);
            high--;
        }
    }
}

int main(){

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input
    for(char &ch : line){
        if(ch == '[' || ch == ']' || ch == ','){
            ch = ' ';
        }
    }

    vector<int> arr;
    stringstream ss(line);
    int x;

    while(ss >> x){
        arr.push_back(x);
    }

    sortColors(arr);

    for(int i : arr){
        cout << i << " ";
    }
}
```
