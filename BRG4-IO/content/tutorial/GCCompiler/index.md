+++
title = 'Upgrade your compiler'
date = 2024-07-11T08:28:12+02:00
draft = false
+++

# Commandline
g++ hat die Moeglichkeit mit ein par command line Flags ein wenig geupgraded zu werden. https://bytes.usc.edu/cs104/wiki/gcc

Example command:
```
g++ -fsanitize=undefined,null -D_GLIBCXX_DEBUG -O1 -g -Wextra --std=c++17 your_program.cpp -o your_program
```
## Wall
```-Wextra``` show all warnings. It turns on all standard C++ warnings about code that might cause unexpected or undefined behavior. -02 Checks your program during the optimisations
### Version

```--std=c++17``` Allows you to use the c++ 17th edition features(build in binary search)
## Debug info
```-g ``` Allows you to debug the program with gdb
## Protections
```-fsanitize=address,undefined,null``` This slows down the code you run on your computer, but protects you from the worst errors https://lemire.me/blog/2020/09/23/how-expensive-is-integer-overflow-trapping-in-c/
