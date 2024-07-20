+++
title = 'Missing Number'
date = 2024-07-18T19:53:07+02:00
draft = false
+++
[website](https://cses.fi/problemset/task/1083)
# Missing Number
# Fehlende Zahl finden

Du hast die Aufgabe, eine fehlende Zahl in einer Liste von Zahlen zu finden. Die Liste enthält alle Zahlen von 1 bis n, außer einer. Deine Aufgabe ist es, die fehlende Zahl zu finden.

## Eingabe

Die erste Eingabezeile enthält eine ganze Zahl n. Die zweite Zeile enthält n-1 Zahlen. Jede Zahl ist eindeutig und liegt zwischen 1 und n (einschließlich).

## Ausgabe

Gib die fehlende Zahl aus.

## Beispiel

Eingabe:
```
5
2 3 1 5
```

Ausgabe:
```
4
```

## Lösung

Wir beginnen wieder mit dem Standard-Codegerüst:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

}
```

- `#include <vector>`: Da wir dieses Mal mit einer unbestimmten Anzahl von Zahlen arbeiten, importieren wir die `vector`-Klasse. Ein `vector` ist eine Möglichkeit, dynamisch viele Variablen in einer Liste zu speichern.
- `using namespace std;`: Du hast vielleicht bemerkt, dass wir im vorherigen Algorithmus oft `std::cout` geschrieben haben. Wir können uns das Leben leichter machen und sagen, dass wir `std` vor `cout` nicht mehr brauchen. Warum man dies außerhalb von Wettbewerbsprogrammierung nicht tun sollte, kann ich bei Bedarf persönlich erklären.

### Einlesen von Variablen

[Variablen einlesen](https://integratedturtle.github.io/BRG4-IO/tutorial/variableneinlesen/)

Dieses Mal müssen wir eine Zahl, die wir `n` nennen, einlesen und dann `n-1` weitere Zahlen.

```cpp
int main() {
    int n, a;
    cin >> n;
    vector<int> values;
    for(int i = 0; i < n - 1; i++){
        cin >> a;
        values.push_back(a);
    }
}
```

Wie im separaten Artikel bereits erwähnt, erstellen wir zuerst zwei Variablen, `n` und `a`. Da wir die Zahl `n` als erstes erhalten, speichern wir diese mit `cin >> n;` in der Variable `n`. Dann erstellen wir einen `vector`, wobei wir angeben müssen, welchen Datentyp wir in diesem `vector` speichern werden. Da es weitere Zahlen sein werden, schreiben wir `<int>` hinter `vector`. Jetzt weichen wir ein wenig von der Standard-Implementierung ab, denn in der Aufgabenstellung steht, dass uns `n-1` verschiedene Variablen gegeben werden. Deshalb können wir nicht die gesamte Zahl `n` einlesen, sondern müssen 1 abziehen. Für jede Zahl lesen wir also die Variable ein, speichern sie in `a` und fügen `a` dann in den `vector` ein.

### Logik

Unsere Daten sind eine ungeordnete Liste von Zahlen, die alle Zahlen bis auf eine enthält. Die Frage ist, wie wir herausfinden können, welche der Zahlen diejenige ist, die noch nicht vorgekommen ist. Wir müssen dabei beachten, dass der Algorithmus sehr viele Zahlen verarbeiten kann und nicht so schnell wie wir Menschen viele Zahlen auf einmal betrachten kann. Deshalb sollten wir eine Liste führen, welche Zahlen wir schon gefunden haben und welche nicht. Die Zahl, die am Ende ungefunden bleibt, ist die, welche nicht aufgelistet wurde. Zum Glück wissen wir genau, welche Zahlen vorkommen sollten, und so können wir uns eine Liste erstellen, in der wir vermerken, welche Zahlen schon vorgekommen sind.

```cpp
vector<bool> theo_values(n, false);
```

Hier wird ein `vector` erstellt, der `bool`-Werte (also `true` oder `false`) speichert. Wenn wir den Namen schreiben, können wir diesem auch ein paar Parameter mitgeben, die den `vector` von Anfang an formatieren. Wenn wir uns den `vector` von vorher ansehen, den wir zum Einlesen von Variablen verwendet haben, ist dieser zuerst einmal leer. Mit `push_back()` erweitern wir diesen dann. Das ist sehr einfach, bringt aber, wie wir später besprechen werden, wenn man besonders schnell sein will, einige Einschränkungen mit sich. In dieser Schreibweise können wir von Anfang an sagen, wie groß der `vector` sein soll. In diesem Fall soll er `n` groß sein. Im zweiten Parameter können wir einen Wert definieren, den alle Werte im `vector` von Anfang an annehmen sollen. Da wir eine Liste wollen, sind diese am Anfang einmal alle `false`, das bedeutet, dass wir diese Werte noch nicht gefunden haben. Da die Werte, die kommen könnten, in einer Reihenfolge sind, können wir sagen, dass wir an der Position des Wertes vermerken, ob wir diesen Wert schon gefunden haben.

### Abhaken

```
n = 5, values = {2, 3, 1, 5}, theo_values = { false, false, false, false, false }
```

Das Ziel ist jetzt, durch den `values`-Vector zu gehen und jede Zahl, die wir finden, abzuhaken. Also ungefähr so:

```
2 -> { false, true, false, false, false } // Da es von 1-n geht, beginnen wir bei 1 zu zählen
3 -> { false, true, true , false, false }
1 -> { true , true, true , false, false }
5 -> { true , true, true , false, true  }
```

Damit wir das tun können, müssen wir zuerst einmal über alle Zahlen iterieren.

```cpp
for(int value : values){
    value
}
```

In dieser `for`-Schleife sagen wir, dass wir eine neue Variable definieren, in diesem Fall `value`, und die Schleife soll sich so oft wiederholen, dass `value` jeden Wert im `values`-Vector einmal annimmt (natürlich in der Reihenfolge). Somit gehen wir automatisch über jeden Wert im `vector`.

```cpp
for(int value : values){
    theo_values[value - 1] = true;
}
```

Damit wir in der Liste abhaken können, welchen Wert wir schon besucht haben, müssen wir nur an dem Index des Wertes den Wert von `theo_values` auf `true` setzen. Da unsere Zahlen aber von 1 bis n gehen und das Indizieren in C++ mit 0 beginnt, müssen wir dem Wert noch einmal 1 subtrahieren, damit der Wert `value = 1` auch an der ersten, also der nullten Stelle geschrieben wird.

### Auswerten

Jetzt müssen wir nur noch herausfinden, welcher der Werte nicht `true` ist, also wir nicht gefunden haben, und diesen mit einem `cout` ausgeben. Dafür sollten wir wieder über alle Werte im `theo_values`-Vector gehen, uns den Index merken und dann, wenn der Wert nicht `true` ist, den Index ausgeben.

```cpp
for(int i = 0; i < theo_values.size(); i++){
    if (!theo_values[i]) {
        cout << i + 1;
    }
}
```

Hier haben wir wieder eine klassische `for`-Schleife, in der wir `i` alle Indizes im `theo_values`-Vector annehmen lassen. Wir können jetzt jedes Mal in der Schleife uns ansehen, ob der gerade angesehene Wert wahr ist, und wenn er es nicht ist, was wir mit dem `!` besagen, den Codeblock in den darauf folgenden Klammern ausführen. Also, wenn wir uns mit dem Index jeden Wert ansehen und feststellen, dass er nicht `true` ist, geben wir den Index aus. Dieses Mal wieder mit `+1`, da wir ja bei 0 begonnen haben zu zählen, aber die Werte bei 1.
# Fertig
```cpp
#include "iostream";
#include "vector"
using namespace std;

int main() {
    int n, a;
    cin >> n;
    vector<int> values;
    for(int i = 0; i < n - 1; i++){
        cin >> a;
        values.push_back(a);
    }

    vector<bool> theo_values(n, false);

    for(int value : values){
        theo_values[value - 1] = true;
    }

    for(int i = 0; i < theo_values.size(); i++){
        if (!theo_values[i]) {
            cout << i + 1;
        }
    }

}
```
