#include<bits/stdc++.h>
using namespace std;

string convertToBinary(int n){

    if(n == 0) return "0";

    string result = "";

    while(n > 0){
        if(n % 2 == 1){
            result += '1';
        } else {
            result += '0';
        }
        n = n / 2;  // FIX: update n
    }

    reverse(result.begin(), result.end());  // FIX

    return result;  // FIX

}

int main(){
ios_base::sync_with_stdio(false);
cin.tie(NULL);

    int n;
    cin >> n;

    cout << convertToBinary(n);

}
