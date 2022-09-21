# Static library

### Introduction

 It is added to the executable code before the executable program runs. Become part of the executable program.\
 The static library can be thought of as a collection of object codes, usually with ".a" as the file suffix.\
 The static library does not need to be compiled again when the program is generated, its saves compilation time.

### Statement

 `ar -rcs lib<library name>.a <file1>.o <file2>.o`

 This statement means adding the files to the static library. The file must be a compiled file, which suffix is ".o".\
 If the static library does not exist, it will be automatically created a new one.\
 "-rcs" are fixed optional.

### Steps
  
  + Convert ".c" files to ".o" files.
  
    `gcc -c <file>.c -o <file>.o`
  
  + Use ar tool to make static library.
  
    `ar -rcs lib<library name>.a <file1>.o <file2>.o`
  
  + Compile static library into executable file.
  
    `gcc <file>.c lib<library name>.a -o <executable file>`

### Tips

 Before compiling, it is best to redeclare the static library functions which have been used, to avoid the implicit declaration of the compiler. we can declare the functions in the ".h" file, then include the header in ".c" file.
 Implicit declaration: If the compiler does not find the declaration of the static library function which we used, it will make an implicit declaration. The implicit declaration function only returns int, if the return value of the original function is not of type int, it will generate an error. So it needs to be re-declared to indicate its return type.