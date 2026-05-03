## Q32 Problem: Best Time to Buy and Sell Stock

Given an array `prices` where `prices[i]` is the price of a stock on the `i-th` day, find the **maximum profit** you can achieve.

You may:

- Buy **one** stock
- Sell it later

If no profit is possible, return `0`.

---

## Example 1

```text id="k3m9q2"
Input: prices = [7,1,5,3,6,4]
Output: 5
```

---

## Example 2

```text id="x8r4t1"
Input: prices = [7,6,4,3,1]
Output: 0
```

---

## Example 3

```text id="p5v7b9"
Input: prices = [2,4,1]
Output: 2
```

---

### 🔴 Brute Force Approach

```cpp
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
using namespace std;

// BRUTE FORCE: Try all pairs (O(n^2))
int stock(vector<int> &arr){

    int n = arr.size();

    int maxProfit = 0;

    for(int i = 0; i < n; i++){
        for(int j = i + 1; j < n; j++){

            int profit = arr[j] - arr[i]; // sell - buy
            maxProfit = max(maxProfit, profit);
        }
    }

    return maxProfit;
}

int main(){

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    string line;
    getline(cin, line);

    // Clean input like [7,1,5]
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

    cout << stock(arr);
}
```

---

### 🟢 Optimal Approach (Single Pass)

```cpp
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
#include<climits>
using namespace std;

// OPTIMAL: Track minimum price and max profit (O(n))
int stock(vector<int> &arr){

    int n = arr.size();

    int maxProfit = 0;
    int minPrice = INT_MAX;

    for(int i = 0; i < n; i++){

        // Update minimum price so far
        minPrice = min(minPrice, arr[i]);

        // Calculate profit if sold today
        int profit = arr[i] - minPrice;

        // Update maximum profit
        maxProfit = max(maxProfit, profit);
    }

    return maxProfit;
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

    cout << stock(arr);
}
```
