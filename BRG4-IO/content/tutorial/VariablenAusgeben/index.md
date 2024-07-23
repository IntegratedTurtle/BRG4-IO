+++
title = 'Variablen Ausgeben'
date = 2024-07-23T13:15:16+02:00
draft = true
+++
So wie man zu beginn eines Programmes fast immer die Variablen einlesen muss, muss man sei output ausgeben. Das ist oft einfacher, wenn man nur einzelne Zahlen ausgieb, da man sich nicht um das speichern kuemmern muss, es gibt aber doch hier auch patterns die sich immer wieder wiederhollen.
# Wie funktioniert ausgeben
Dein Program startet mit einer neune Zeile, an welche du mit std::cout einfach etwas dranhaengen kannst. Stelle es dir vor wie ein Fluss welcher vor deiner Austuer fliest, den vorteil den du hast, ist, dass der fluss, bis du etwas reinschreibst auf dich Wartet.\
Die Console die du vor dir hast ist an einem weiter unten liegenden Punkt des FLusses und faengt alle packaget die dein Program in den Fluss geworfen hat auf und praesentiert sie dir.\
Mit diese Methapher kann man auch gut den Buffer erlaeren der im Hintergrund arbeitet.
Jedes mal von deinem Schreibtisch aufzustehen und vor die Tuer zu gehen, ist relativ langsam, deswegen sammelt das Program immer wieder seine Packete in einer Kiste unter deinem Schreibtisch, und wenn diese voll ist, gehst du mit der ganzen Kist nach unten und setzt sie in den FLuss.
Das hat den Vorteil, dass man nicht so of den weiten weg bis zum Fluss gehen muss, aber auch den Nachteil, dass nicht immer genau dann in den Fluss gesetzt wird wenn du es in den Code geschrieben hast.\
Deswegen gibt es "std::endl".
Das gibt dir eine neue Zeile und zwingt das Program sofort los zu gehen und die Kisten in den Fluss zu werfen.

# Ausgeben von einzelen Variablen
Sollange es variablen sind die nur einen Wert halten, wie String, int, float, kann man diese ohne probleme mit cout einfach ausgeben.
```cpp
std::cout << variable;
```
Dabei muss beachtet werden, dass hier einfach an der letzten stelle die variable gesetzt wird, ohne davor oder dahinter ein Leerzeichen zu setzen.\
Bsp:(Wenn dein Zeicher bei dem | symbol ist)
```
./test
a|

--> cout << "Hello";

./test
aHello|
```
## Verketten
Man kann dabei auch mehrere Variablen gleichzeitig ausgeben, man muss sie nur durch mehrere << trennen, es wird aber immer noch nichts dazwischen geschrieben.
```
./test
a|

--> cout << "Hello" << "World" << "little" << "Program";

./test
aHelloWorldlittleProgram|
```
Auch wenn gerade nicht gezeigt kann man hierbei verschiedenste typen von Variablen ausgeben, da die einzelen Teile nicht von andern abgeben und somit praktisch das selbe sind wie:
```
./test
a|

--> cout << "Hello" 
--> cout << "World";

./test
aHelloWorld|
```
## Abstaende
Somit muessen wir abstaende selber hinzufuegen, dabei gibt es drei verschiedene die man altaeglich benutzt
- Space = ' '
- Tab = '\\t'
- NewLine = '\\n'
Wenn die Console die Befehle des Program empfaengt, weis es nicht von selber was damit zu tun ist, denn genauso wie jeder andere Buchstabe ist zBsp die NewLine einfach nur eine Zahl. Erst wenn es beginnt die Zahlen an zu zeigen und zu interpretieren kann es mit dem Formating und somit auswerden der NewLine beginnen. So muessen wir, als Menschen die das Program schreiben, diese besondern Zeichen auch als Einzelcharacter verstaendlich abschicken. Fuer den Space kann man einfach einen Abstand lassen, aber Tab und NewLine muessen so representiert werden.
```
./test
a|

--> cout << "Hello" << " " << "World" << "\n" <<"little" << "\tProgram" << endl;

./test
aHello World
little      Program
|
```
# booleans printen
Booleans representieren die Werte Wahr oder Falsch. Strom an oder Aus, oder wie man es meist representiert, 1 oder 0. So werden sie dann auch ausgegeben, versucht man also einen boolean zu printen gibt es das:
```
cout << "value: " << true << "\n";
cout << "value: " << false << endl;
-->
value: 1
value: 0|
```
# Vector printen
Vectoren printen ist ein wenig complizierter, da in c++ mit cout nur einzelne Werte geprintet werden koennen.
## multi dimension vector
