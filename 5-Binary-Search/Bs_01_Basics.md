```cpp
#include<iostream>
#include<vector>
#include<sstream>
#include<algorithm>
using namespace std;

int main(){
ios::sync_with_stdio(false);
cin.tie(NULL);

    int n;
    cin >> n;
    cin.ignore();

    string line;
    getline(cin, line);

    vector<int> arr;
    stringstream ss(line);

    int x;
    while (ss >> x) {
        arr.push_back(x);
    }

    int target;
    cin >> target;

    // SORT REQUIRED
    sort(arr.begin(), arr.end());

    // ---------------- Q1: binary_search ----------------
    bool found = binary_search(arr.begin(), arr.end(), target);

    // ---------------- Q2: lower_bound ----------------
    auto lb = lower_bound(arr.begin(), arr.end(), target);
    int lb_index = lb - arr.begin();

    // ---------------- Q3: upper_bound ----------------
    auto ub = upper_bound(arr.begin(), arr.end(), target);
    int ub_index = ub - arr.begin();

    // ---------------- Q4: Search Insert Position ----------------
    // same as lower_bound
    int insert_pos = lb_index;

    // ---------------- Q5: First & Last Occurrence ----------------
    int first = -1, last = -1;

    if (lb != arr.end() && *lb == target) {
        first = lb_index;
        last = ub_index - 1;
    }

    // ---------------- Q6: Count Occurrences ----------------
    int count = 0;
    if (first != -1) {
        count = ub_index - lb_index;
    }

    // ---------------- OUTPUT ----------------
    cout << "Sorted Array: ";
    for (int v : arr) cout << v << " ";
    cout << "\n";

    cout << "Q1 Found: " << found << "\n";
    cout << "Q2 Lower Bound Index: " << lb_index << "\n";
    cout << "Q3 Upper Bound Index: " << ub_index << "\n";
    cout << "Q4 Insert Position: " << insert_pos << "\n";

    cout << "Q5 First Occurrence: " << first << "\n";
    cout << "Q5 Last Occurrence: " << last << "\n";

    cout << "Q6 Count: " << count << "\n";

    return 0;

}
```
