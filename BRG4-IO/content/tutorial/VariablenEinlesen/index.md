+++
title = 'VariablenEinlesen'
date = 2024-07-13T14:30:28+02:00
draft = false
+++
In den Aufgaben, die wir machen, müssen wir meist die Variablen selber einlesen. Das ist in C++ eigentlich nur auswendig lernen, deswegen kann es am Anfang noch etwas schwieriger sein zu wissen, was zu tun ist. Deshalb dieser Post.

## Allgemeines

`std::cin` ist eine Möglichkeit, Zeichen von der Kommandozeile einzulesen. Es mag im Vergleich zu vielen anderen Befehlen in C++ anders aussehen, unter anderem, weil es das einzige ist, das `>>` benutzt. Das liegt daran, dass es eigentlich noch aus der C-Programmiersprache stammt. Es gibt neuere Alternativen, aber dazu werden wir nicht kommen, da unsere Programme sehr voraussehbar laufen werden.

Ihr könnt euch, wie der Name von `iostream` (Input Output Stream) andeutet, einen Fluss vorstellen. Dieser Fluss kann in Linux auch mit Pipes (`|`) von einem Programm zum nächsten geleitet werden. Das bedeutet, ein Programm kann seinen Output wie einen Fluss ausgeben, und wir können ihn weiter in ein anderes Programm leiten.

Diese Flüsse sind vor allem Zeichen, welche durch Abstände, Tabs und Zeilenumbrüche getrennt werden. `std::cin` kann jetzt diesen Fluss einfangen und ihn in unserem Programm verarbeiten. Jedes Mal, wenn wir `cin` in eine Variable schreiben, nimmt sich `cin` aus diesem Fluss Zeichen, bis es den nächsten Abstand trifft.

## Einzelne Variablen

In fast allen Programmen werden wir mindestens eine Variable einlesen müssen. Beispiel: Wir müssen die Zahl `n` einlesen.

```cpp
int n;
std::cin >> n;
```

Dazu deklarieren wir die Variable `n`, ohne ihr einen Wert zu geben, und sammeln dann Zeichen aus dem Input bis zum nächsten Abstand. C++ versucht, diese dann in eine Zahl zu konvertieren. Mit dem obigen Code stehen bei diesem Input diese Zahlen in `n`:

```
8 -> 8
127 -> 127
53 12 -> 53
76 2 -> 76
```

### Mehrere Einzelvariablen

Wir können auch mehrere Einzelvariablen abspeichern. Dazu können wir uns zunutze machen, dass wir mehrere Variablen gleichzeitig definieren können und solange sich ein Abstand dazwischen befindet, auch gleichzeitig auslesen.

```cpp
int a, b, c;
std::cin >> a >> b >> c;
```

Das gibt bei diesem Input:

```
8 -> a = 8, b = ?, c = ?
1 2 7 -> a = 1, b = 2, c = 7
53 12 3 -> a = 53, b = 12, c = 3
```

### Menge an Variablen

Es passiert auch oft, dass man eine große Menge an Variablen einlesen muss. Diese Variablen speichern wir, vor allem dann, wenn es nicht immer gleich viele Variablen sind, in Vektoren ab. Wenn man Variablen in Vektoren abspeichert, bekommt man meist auch davor eine Einzelvariable, welche angibt, wie viele Variablen du abspeichern wirst.

```cpp
int n;
std::cin >> n;
std::vector<int> save;
int a;
for (int i = 0; i < n; i++) {
    std::cin >> a;
    save.push_back(a);
}
```

Hier lesen wir zuerst die Variable `n` ein, welche uns sagt, wie viele Elemente wir in den Vektor speichern sollen. Dann legen wir den Vektor mit dem Namen `save` an und noch eine Variable `a`, welche wir zum Zwischenspeichern nutzen werden. Der For-Loop geht jetzt so oft wie `n`, also wie viele Variablen wir in den Vektor `save` speichern wollen. Im Loop speichern wir den Wert dann in `a` und schieben `a` in den Vektor.

```
2
3 4 -> {3, 4}
4
1 2 3 5 -> {1, 2, 3, 5}
```

## Mehrdimensionale Vektoren

TODO

## Strings einlesen

Es ist sehr ähnlich wie bei Zahlen.

```cpp
std::string n;
std::cin >> n;
```

Hierbei ist nur wichtig, dass es nur solange die Wörter nimmt, wie sie keine Abstände beinhalten.

```cpp
int n;
std::cin >> n;
std::vector<std::string> save;
std::string a;
for (int i = 0; i < n; i++) {
    std::cin >> a;
    save.push_back(a);
}
```

## Faster IO

Manchmal muss man wirklich schnell werden, und da reichen die Standard-IO-Tools nicht mehr aus. Dann muss man diese Zeilen an den Anfang seines Programmes schreiben:

```cpp
std::ios_base::sync_with_stdio(false); 
std::cin.tie(NULL);
```
