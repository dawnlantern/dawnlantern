# Dynamic library

### Introduction

 Dynamic library also known as shared library. Shared libraries will not linked into the object code when the program is compiled, they are loaded when the program is running. \
 If different applications call the same library, there is only one instance of the shared library in memory, which avoids wasting space.\
 Shared libraries use ".so" as the file suffix.

### Statement

 Unlike static libraries, dynamic libraries do not require ar tool when generating.\
 When generating the object file, we need to add the compile option "-fPIC", to indicates that pic(position independent code) is to be created:

 `gcc -fPIC -c <file>.c -o <file>.o`

 Generate dynamic library statement, add the compile option "-share", to 
 indicates generating a shared library:

 `gcc -share <file1>.o <file2>.o -o lib<library name>.so`

 When generating the executable file, we need to add several options in particular. 

 `gcc <file>.c -L <path> -I <path> -l <library name>`

 `-L`: Specify the path to the library\
 `-I`: Specify the path to the header file\
 `-l`: Specify the name of the library

### Steps

 + Generating the object file.
  
    `gcc -fPIC -c <file>.c -o <file>.o`

 + Generating dynamic library.

    `gcc -shared <file1>.o <file2>.o -o lib<library name>.so`

 + generating the executable file.

    `gcc <file>.c -L <path> -I <path> -l <library name>`

 + Because the dynamic linker works in the program running phase, we need to provide the path where the dynamic library is located. Here are a few solutions:

    + Modify environment variables "LD_LIBRARY_PATH"(Modify only temporary variables, invalid when terminal restarts)

        `export LD_LIBRARY_PATH=<path>`

    + Permanent effect needs to modify ~/.bashrc

        `vi ~/.bashrc`

        end of file added

        `export LD_LIBRARY_PATH=<path>`

        then run to available

        `. ~/.bashrc`

    
### Tips

  By using command "nm" to check out the corresponding function:

  `nm lib<library name>.so | grep <function name>`

  By using command "ldd" to check the shared library that the executable file depends on:

  `ldd <file name>`