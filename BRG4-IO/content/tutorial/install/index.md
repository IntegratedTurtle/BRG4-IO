+++
title = 'Installation'
date = 2024-06-06T14:54:41+02:00
draft = true
+++

# Windows
# MacOS
# Linux
C++ hat zwei Ebenen, auf der einen Seite der Compiler welcher Textdatein interpretiert und zu Executables umschreibt und auf der anderen Seite der Texteditor, welcher dir als Mensch hilft C++ text/Code zu schreiben.\
Es kommen kurze Beschreibungen wie du den Compiler installierst, danach solltest du einen File der so aussieht
``` cpp
#include <iostream>
int main() {
    std::cout << "Hello World" << std::endl;
}
```
mit dem command
```
g++ test.cpp
```
Compilieren.
## Debian & Ubuntu & Linux Mint ...
### Compiler
Wir arbeiten mit g++ und werden auch den Windows Menschen diesen Compiler installieren
```
apt install build-essential
```
## Fedora
### Compiler
g++ compiler
```
sudo dnf install gcc-c++
```
## OpenSuse
### Compiler
g++ compiler
```
zypper in gcc-c++
```

## Editor
### Doom Emacs
In der init.el entcommentiere
``` elisp
:tools
    lsp
:lang
    (cc +lsp)
```
Check ob ~clangd~ installiert ist und installiere es wenn noch nicht.
Fuege das zu deiner config.el hinzu:
```
(setq lsp-clients-clangd-args '("-j=3"
				"--background-index"
				"--clang-tidy"
				"--completion-style=detailed"
				"--header-insertion=never"
				"--header-insertion-decorators=0"))
(after! lsp-clangd (set-lsp-priority! 'clangd 2))
```
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
Fuer code highlighting laded euch diese Datei runter [c.nanorc](c.nanorc) und schreibt in eure nano config
```
include "PATHTO/c.nanorc"
```
### VSCODE
