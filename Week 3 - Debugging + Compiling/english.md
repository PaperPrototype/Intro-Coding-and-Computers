This week may not be necessary since it was mostly covered in week 2.

Convert to "Compilers" week?

This link video onwards (debugging is spearate week)
https://video.cs50.io/tI_tIZFyKBw?screen=SOJ4zTf_nkg&start=3008&end=3369

- Compiling
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
        - for example: pasting header file code into our code file
    - compiling
        - turning text based code into CPU specific "assembly"
    - assembling
        - taking assembly and turning it into binary "machine code" (0s and 1s instructions)
    - linking
        - taking all the 0s and 1s of different files and "linking" them together into one file. (Some times `#include` doesn't copy paste header code into program code because it only has acces to the "compiled" header, so it just has to include the *compiled* binary with our binary)
    - Where are the files stored?
        - When you install a compiler it usually comes with a collection of .h files
    - How does the compiler know where to find the .h files
        - That is something you do when you download the compiler
    - Is all the code from the .h files included or only the code from them that we used.

- Debugging
    - use printf for debugging
- Debugger in Replit
    - breakpoints
    - step over
- Rubber duck debugging
    - Talking to a rubber duck
    - This is for real
- Linear search
    - 
