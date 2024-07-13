+++
title = 'Weird Algorithm'
date = 2024-07-11T22:55:44+02:00
draft = false
Description = 'Aufgaben um mit dem syntax vertraut zu werden'
+++
[Website](https://cses.fi/problemset/task/1068)
Hier ist der verbesserte Artikel:

## Hilfe
Vor allem am Anfang kann man wirklich gut ChatGPT oder ähnliche Tools nach Hilfe fragen. Sprachmodelle sind gut darin, gelöste Probleme zu erklären.

## Lösung
Man startet einmal mit einem Boilerplate. Das bedeutet, es gibt einige Dinge, die wir schreiben müssen und die für "jedes" Programm gleich sind.

```cpp
#include <iostream>

int main() {

}
```

- `#include <iostream>`: Damit unterstützen wir, dass wir mit der Kommandozeile interagieren können, weil wir eine Zahl einlesen und dann auch Zahlen ausgeben möchten.
- `int main() {}`: Wenn ihr euch C++ schon angeschaut habt, werdet ihr sehen, dass `main` eine Funktion ist, die einen ganzzahligen Wert zurückgibt. Damit wird in C++ einfach nur gekennzeichnet, wo das Programm starten soll.

### Einlesen von Variablen
Dazu wird es unter Tutorials noch einen eigenen Eintrag geben, da diese Sektion im Endeffekt auswendig gelernt werden muss. Es ist nicht viel, aber da es so wenig ist, muss man es sich nicht jedes Mal logisch erschließen, sondern kann sich einfach Muster merken.

In dieser Aufgabe müssen wir die Variable `n` speichern, welche unser Startpunkt ist. `n` wird hierbei immer eine ganze Zahl sein, also können wir einmal die Variable `n` anlegen.

```cpp
#include <iostream>

int main() {
    int n;
}
```

Als Kommandozeileneingabe bekommen wir eine Zahl, so können wir diese eine Zahl auch in der Variable abspeichern.

```cpp
#include <iostream>

int main() {
    int n;
    std::cin >> n;
}
```

`std::cin` ist hierbei der Befehl, welcher Kommandozeileneingaben annimmt. Mit den `>>` können wir das, was davon eingefangen wurde, in eine Variable schieben, hierbei in die Variable `n`.

### Logik
Wenn man sich das Beispiel anschaut, wird man sehen, dass es zwei Modi geben muss. Wenn die Variable `n` gerade ist, wird A getan, wenn sie ungerade ist, B. Um das zu erreichen, können wir `if` und `else` verwenden.

```cpp
if (gerade) {
    // A
} else {
    // B
}
```

Da eine Zahl, wenn sie nicht gerade ist, ungerade ist, müssen wir nur einen Check durchführen. In C++ prüft man, ob eine Variable gerade ist, mit dem Modulo von 2 und schaut dann, ob es 0 ist.

```cpp
if (n % 2 == 0) {
    // A
} else {
    // B
}
```

> Modulo wird in C++ mit `%` beschrieben und bedeutet praktisch `a % b = c`. Wenn wir `a` durch `b` dividieren, kommt `c` als Rest heraus. Wenn man durch 2 dividiert und das Ergebnis gleich 0 ist, dann ist die Zahl gerade.

### Aktion
Jetzt ist die Frage, was passiert denn in Szenario A und in Szenario B?
- A: Die Variable wird halbiert -> `n / 2`
- B: Die Variable wird mit 3 multipliziert und dann 1 addiert -> `n * 3 + 1`

Eingetragen sieht das so aus:

```cpp
if (n % 2 == 0) {
    n / 2;
} else {
    n * 3 + 1;
}
```

Die Frage ist jetzt, wie speichern wir das. Normalerweise speichert man, wenn man Daten hat, diese in Variablen. Da wir `n` danach nicht mehr brauchen werden, können wir `n` einfach wieder benutzen.

```cpp
if (n % 2 == 0) {
    n = n / 2;
} else {
    n = n * 3 + 1;
}
```

> Semikolon nicht vergessen

### Schleife
Wenn wir uns die Aufgabenstellung nochmal durchlesen, wird sofort klar, dass es sich in der Aufgabe um eine Schleife handelt. Man soll eine gewisse Aktion so lange durchführen, bis ein bestimmtes Ergebnis gegeben ist. C++ hat für solche Aufgaben die Syntax der while-Schleife.

```cpp
while (CHECKER) {

}
```

Die while-Schleife wiederholt etwas, solange ihr Bedingungsausdruck TRUE ist. In unserem Fall soll sie sich wiederholen, solange `n` nicht 1 ist, weil dann soll das Programm enden.

```cpp
while (n != 1) {

}
```

> `a != b` gibt TRUE zurück, wenn die Werte nicht gleich sind.

Jetzt muss die Logik nur noch in die Schleife gesetzt werden.

```cpp
while (n != 1) {
    if (n % 2 == 0) {
        n = n / 2;
    } else {
        n = n * 3 + 1;
    }
}
```

Das Programm startet jetzt mit einem `n` und endet, wenn `n` 1 ist.

### Ein- und Ausgabe
Verbinden wir das Programm mit dem Einlesen der Variable, die wir am Anfang hatten:

```cpp
#include <iostream>

int main() {
    int n;
    std::cin >> n;
    while (n != 1) {
        if (n % 2 == 0) {
            n = n / 2;
        } else {
            n = n * 3 + 1;
        }
    }
}
```

Das Programm kann jetzt die Variable `n` einlesen und durch die Logik laufen. Verlangt von der Aufgabe ist jetzt aber, dass jeder Schritt dokumentiert wird, indem wir die Zwischenergebnisse in die Kommandozeile schreiben. In die Kommandozeile schreibt man mit `std::cout <<`. Das Ziel ist, jeden Schritt zu dokumentieren, indem man die Variable in die Kommandozeile schreibt. Dazu müssen wir einen Ort auswählen, den die Variable in den meisten ihrer Fälle durchläuft.

```cpp
#include <iostream>

int main() {
    int n;
    std::cin >> n;
    while (n != 1) {
        std::cout << n << " ";
        if (n % 2 == 0) {
            n = n / 2;
        } else {
            n = n * 3 + 1;
        }
    }
}
```

Ich habe mich hier für die Zeile unter dem while-Loop entschieden. Jedes Mal, solange der Wert nicht 1 ist, schreibt `std::cout <<` die Variable in die Kommandozeile und hängt einen Abstand dazu. Es gibt nur noch ein Problem: Wir sollten auch den letzten Zustand schreiben, aber wenn `n == 1` ist, dann bricht die Schleife ab und `std::cout` wird nicht mehr ausgeführt. Deshalb muss ganz am Ende nochmal `n` ausgegeben werden und auch die Zeile beendet werden. Das macht man mit `std::endl`.

```cpp
#include <iostream>

int main() {
    int n;
    std::cin >> n;
    while (n != 1) {
        std::cout << n << " ";
        if (n % 2 == 0) {
            n = n / 2;
        } else {
            n = n * 3 + 1;
        }
    }
    std::cout << n << std::endl;
}
```

Jetzt ist das Programm komplett und erfüllt die Aufgabe.
