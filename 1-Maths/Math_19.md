#include <bits/stdc++.h>
using namespace std;

vector<int> primeFactorization(int n) {
vector<int> factors;

    // Step 1: handle 2 separately
    while (n % 2 == 0) {
        factors.push_back(2);
        n /= 2;
    }

    // Step 2: check odd numbers from 3 to sqrt(n)
    for (int i = 3; i * i <= n; i += 2) {
        while (n % i == 0) {
            factors.push_back(i);
            n /= i;
        }
    }

    // Step 3: if remaining n > 1 → it's prime
    if (n > 1) {
        factors.push_back(n);
    }

    return factors;

}

int main() {
int n;
cin >> n;

    vector<int> res = primeFactorization(n);

    cout << "Prime factors: ";
    for (int x : res) {
        cout << x << " ";
    }

    return 0;

}
