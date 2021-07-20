
- `make` autmatically figures out how to use a compiler for you
- assembly?
- linking external files (math.h)
    - header file calls functions
        - those functions 0s and 1s stored somewhere else
- https://cs50.harvard.edu/x/2021/weeks/2/ <- how to use clang
    - `clang main.c` -> `a.out` (assembly output)
    - `clang -o main main.c` -> `main`
        - `-o` = output, output "main"
- using clang in Replit
- pre-processing
    - pasting header file code intot program file
- compiling
    - turning text based code into machine code (aka assembly)
- assembling
    - taking machine code (aka assembly) and turning it into binary
- linking
    - connecting together binary machine code into one file (some times `#include` doesn't copy paste header code into program code, so we just have to inlude the *compiled* header binary file with our binary file)
- setting up an IDE on your computer
    - getting clang on your computer
    - setting up vs code

Implementing Binary search using the VS-Code IDE. Show how Binary search requires sorting. Next week show:
- sorting algorithms
- file loading

- figure out name for week 2
