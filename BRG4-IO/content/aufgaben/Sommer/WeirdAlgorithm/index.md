+++
title = 'Weird Algorithm'
date = 2024-07-11T22:55:44+02:00
draft = true
Description = 'Aufgaben um mit dem syntax vertraut zu werden'
+++
[Website](https://cses.fi/problemset/task/1068)
## Hilfe
Vorallem am anfang kann man wirklich good ChatGPT oder aehnliches nach hilfe Fragen, llms sind gut darin geloeste Probleme zu erklaeren.
## Loesung
Man startet einmal mit einem boilerplate, das bedeutet es gibt einig ding die wir schreiben muessen und fuer "jedes" Program gleich sind.
```
#include <iostream>

int main()

}
```
- #include <iostream> Damit supporten wir, dass wir das wir mit der Command line interagieren koennen, weil wir moechten ja eine Zahl einlesen und dann auch Zahlen schreiben koennen.
- int main () {} Wenn ihr euch c++ schon angeschaut habt werdet ihr sehen das, main ein funktion ist die einen ganzen Zahlenwert exportiert. Damit wird in C++ einfach nur gekennzeichnet wo das Program starten soll.
### Einlesen von Variablen
Dazu wird sich unter Tutorials noch ein eigenen Eintrag finden, da diese Sektion im Endefekt auswendig lernen ist. Es ist nicht viel, aber, da es so wenig ist muss man es sich nicht jedesmal logisch erschlieSSen sondern kann sich einfach Patterns merken.\
In dieser Aufgabe muessen wir die Variable n speichern, welche unser Startpunkt ist.\
n wird hierbei immer eine ganze Zahl sein, also koennen wir einmal die Variable n anlegen
```
#include <iostream>

int main()
    int n;
}
```
Als command line input bekommen wir ein Zahl, so koennen wir diese eine Zahl auch in der Variable abspeichern.
```
#include <iostream>

int main()
    int n;
    std::cin >> n;
}
```
std::cin ist hierbei der command, welcher CommandlineINput nimmt. Mit den >> koennen wir das was davon eingefangen wurde in eine Variable schieben, hierbei in die Variable n.
### Logic
Wenn man sich das Beispiel anschaut wird man sehen es zwei Moduse geben muss. Wenn die Variable n gerade ist wird a getan wenn sie ungerade ist b.
Um das zu erreichen koennen wir if und else verwenden.
```
if (Gerade)  {
    //A
} else {
    //B
}
```
Da eine Zahl wenn sie nicht gerade ist ungerade ist koennen muessen wir nur einen Check durchfuehren.\
In c++ checkt man ob eine Variable gerade ist, mit dem Modulu von 2 und schaut dann ob es 0 ist.
```
if (n % 2 == 0)  {
    //A
} else {
    //B
}
```
