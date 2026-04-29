#include<bits/stdc++.h>
using namespace std;

bool isLeapYear(int n) {

    if (n % 400 == 0) {
        return true;
    } 
    else if (n % 100 == 0) {
        return false;
    } 
    else if (n % 4 == 0) {
        return true;
    } 
    else {
        return false;
    }
}

int main() {
    int n;
    cin >> n;

    cout << isLeapYear(n);
}