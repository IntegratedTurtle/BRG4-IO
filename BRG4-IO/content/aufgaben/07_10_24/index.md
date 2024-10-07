+++
title = 'Einrichtung und Rekursion'
date = 2024-10-07T13:30:21+02:00
draft = true
+++

# Rekursion
```
// Aufgabe: Berechne die nte Fibonacci Nummer mit Rekursion
// Input: Ein int n wobei 1 <= n <= 1000
// Output: Den Wert der nten Fibonacci Nummer modulo 10e9 + 7

// 1. Regel: Was machen die Variablen?
// 2. Regel: Was ist der Basisfall?
// 3. Regel: Die Rekursion funktioniert schon

#include <bits/stdc++.h>
using namespace std;
#define l long long



// Nte Fibonacci nummer ausrechnen
// Return: integer
// a: Der Index der fibonacci Nummer, die man ausrechnen will
int fib(int a) {
    // Basisfaelle
    if (a == 1) return 1;
    if (a == 2) return 1;

    int solution = fib(a-1) + fib(a-2);
    return solution;
} 


int main() {

    l n;
    cin >> n;

    cout << fib(n) << endl;


    return 0;
}
```



## Problems
- Factorials
- [Fibonacci](https://www.spoj.com/problems/FIBOSUM/)
- [Tower of Harnoi](https://cses.fi/problemset/task/2165)
