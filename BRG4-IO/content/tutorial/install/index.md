+++
title = 'Installation'
date = 2024-06-06T14:54:41+02:00
draft = true
+++

# Windows
# MacOS
# Linux
C++ hat zwei ebenen, auf der einen Seite der Compiler welcher Text datein interpretiert und zu zu Executables umschreibt und auf der anderen Seite der Text editor, welcher dir als Mensch hilft C++ text/Code zu schreiben.\
Es kommen kurze Beschreibungen wie du den Compiler installierst, danach solltest du einen File der so aussieht
``` test.cpp
#include <iostream>
int main() {
    std::cout << "Hello World" << std::endl;
}
```
mit dem command
```
g++ test.cpp
```
Compilieren
## Debian & Ubuntu & Linux Mint ...
### Compiler
Wir arbeiten mit g++ und werden auch den Windows Menschen diesen Compiler installieren
```
apt install build-essential
```

## Editor
### Doom Emacs
### Nano
The nano config file is under
```
/etc/nanorc
```
A cpp file is just a normal text file but there are still some settings I would change
```
set linenumbers
set matchbrackets "(<[{)>]}"
set saveonexit
```
Fuer code highliting laded euch diese Datei runter [[c.nanorc]] und schreibt in eure nano config
```
include "PATHTO/c.nanorc"
```
### VSCODE
