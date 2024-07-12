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
> Modulu wird in c++ mit % beschrieben und bedeutet praktisch a % b = c, wenn wir a durch b dividieren kommt c rest raus.
> Wenn man durch 2 dividiert und das Ergbniss gleich 0 ist, dann ist die Zahl gerade.
### Aktion
Jetzt ist die Frage was passiert denn in dem Scenario A und in dem Scenario B
- A: wird die variable halbiert -> n / 2
- B: wird die variable mit 3 multipliziert und dann mit 1 addiert -> n * 3 + 1
Eingetrage sieht das so aus
```
if (n % 2 == 0)  {
    n / 2
} else {
    n * 3 + 1
}
```
Die Frage ist jetzt, wie speicher wir das. Normalerweise speichert man wenn man daten hat sie in Variablen. Da wir das n, danach nicht mehr brauchen werden, koennen wir n einfach wieder benutzen.
```
if (n % 2 == 0)  {
    n = n / 2;
} else {
    n = n * 3 + 1;
}
```
> Semicolon nicht vergessen
### Loop
Wenn wir uns die Aufgaben stellung nochmal durchlesen wird sofort klar, dass es sich in der Aufgabe um einen Loop handelt. Man soll eine gewisse aktion so lange machen bis ein bestimmtes output gegeben ist.\
C++ hat fuer solche Aufgaben den syntax des while loops.
```
while (CHECKER){

}
```
Der while loop wiederhollt etwas, solange sein Checker TRUE ist. In unserem Fall soll er sich wiederhollen, solange n nicht 1 ist, weil dann soll das Program Enden.
```
while (n != 1){

}
```
> a != b gibt True wenn die Wert nicht gleich sind
Jetzt muss die Logic nur noch in den Loop gesetzt werden
```
while (n != 1){
    if (n % 2 == 0)  {
        n = n / 2;
    } else {
        n = n * 3 + 1;
    }
}
```
Das Program started jetzt mit einem n und endet wenn n 1 ist.

### IO
Verbinden wir das Program mit dem einlesen der Varaible die wir am Anfang hatten:
```
#include <iostream>

int main()
    int n;
    std::cin >> n;
    while (n != 1){
        if (n % 2 == 0)  {
            n = n / 2;
        } else {
            n = n * 3 + 1;
        }
    }
}
```
Das Program kann jetzt die Variable n einlesen und durch die Logic laufen, verlangt von der Aufgabe ist jetz aber das jeder Schritt documentiert wird, indem wir die Zwischen ergebnisse in die Command line schreiben.\
In der Command line schreibt man mit std::cout <<;\
Das Ziel ist jeden Schritt zu dokumentieren indem man die Variable in die Command Line schreibt. Dazu muessen wir einen Ort aussuchen, welchen die Variabel in den meisten ihrer faelle durchgeht.
```
#include <iostream>

int main()
    int n;
    std::cin >> n;
    while (n != 1){
        std::cout << n << " ";
        if (n % 2 == 0)  {
            n = n / 2;
        } else {
            n = n * 3 + 1;
        }
    }
}
```
Ich habe mich hier fuer die Zeile unter dem while Loop entschieden. Jedesmal solange der Wert nicht 1 ist, schreibt cout << die Variable in die Command line und haengt einen abstand dazu.\
Es gibt nur noch ein Problem, wir sollten auch den letzten zustand schreiben, aber wenn n == 1 ist dann bricht die schleife ab und std::cout wird nicht mehr ausgefuehrt.\
Deshalb muss ganz am Ende nochmal n geprinted werden und auch die Zeile beendet, das macht man mit std::endl;
```
#include <iostream>

int main()
    int n;
    std::cin >> n;
    while (n != 1){
        std::cout << n << " ";
        if (n % 2 == 0)  {
            n = n / 2;
        } else {
            n = n * 3 + 1;
        }
    }
    std::cout << n << std::endl;
}
```
