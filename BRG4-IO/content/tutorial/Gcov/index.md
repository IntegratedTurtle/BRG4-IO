+++
title = 'Gcov'
date = 2024-07-11T10:35:02+02:00
draft = true
Description = 'Wann laeuft der Code was'
+++

# Gcov
Wenn man Code geschrieben hat, un man sich nicht ganz sicher ist was jetzt genau passiert, oder der Code zu langsam ist, kann es nuetzlich sein sich anzusehen, wie oft welche Zeile laeuft.
## Vorbereitung
Compiliere deine *.cpp* Datei mit
```
--coverage
```
Dann fuehr dein Program mit einem Testcase aus
## Commands
```
gcov test.cpp -m -k -t | less -R
```
- gcov: ruft das program auf
- m: Schreibt ganze funktionnamen
- k: Farben :->
- t: terminal output, wenn du das Ergebniss in einen File speichern willst lass das weg, wenn du gcov aber mit less benutzen willst ist das wichtig
- | : Pipe: schickt output zum naechstem Command, da t aktiv ist schickt es den Text zu less
- R: Farben :->
## Analyse
!Das Program zeigt dir alle verlinked files auch an, die sind meistens fuer uns irrelevant!
```
        -:    1:#include "iostream"
        -:    2:#include "vector"
        -:    3:
        3:    4:int main() {
        3:    5:    std::string word;
        3:    6:    std::cin >> word;
        -:    7:
        6:    8:    std::cout << "got " << word << std::endl;
        -:    9:
      612:   10:    for(short i = 0; i < word.length(); i++){
      303:   11:        if(word[i] == 'a' || word[i] == 'A' || word[i] == 'o'|| word[i] == 'O'){
       90:   12:            std::cout << "";
        -:   13:        } else {
      213:   14:            std::cout << "." << (char) std::tolower(word[i]);
        -:   15:        }
        -:   16:    }
        3:   17:    std::cout << "\n";
        3:   18:}
```
In der ersten Column ist zu sehen wie oft die Zeile gelaufen ist\
In der zweiten Column ist die Zeilenzahl in deinem Code editor
