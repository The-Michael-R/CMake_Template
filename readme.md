# CMake template with distributed modules
The intent of this template is to be a simple way to create a distributed project
using [cmake](https://cmake.org) build flow. To keep it simple it only supports the build part.

**Note:** I'm not a `cmake` expert. More like an absolute beginner. So probably there  are
things wrong or just ugly. But for me that template seems to be usable and fit my current needs.

This template can be used for projects that uses some kind of library structure.
The modules are located in the libs folder tree. With teh header files in the include
sub-tree and the .c files are in the lib sub-tree. Each libray is separated in its own 
sub-folder to keep them sreparated and re-usable.
```
├── libs
│   ├── include
│   │   ├── lib1
│   │   │   └── lib1.h
│   │   └── lib2
│   │       └── lib2.h
│   ├── lib
│   │   ├── lib1
│   │   │   ├── CMakeLists.txt
│   │   │   └── lib1.c
│   │   └── lib2
│   │       ├── CMakeLists.txt
│   │       └── lib2.c
│   └── CMakeLists.txt
├── src
│   ├── main.c
│   └── project_conf.h.in
├── CMakeLists.txt
└── readme.md
```

The template consists of three _levels_ of `CMakeLists.txt`.
1. In the root directory the project level pointing to the libs and the main .c-file
in the src directory.
2. One in the libs sub-folder. Addressing the individual libraries. This is a very
simple file that includes all (selected) libraries.
3. The `CMakeLists.txt` in the individial library folder. This one can hold library
specific configuration settings.

The `CMakeLists.txt` in the libs-folder and library specific folders create a `${LIBRARY}` list
that allows the `CMmakeLists.txt` file in the root directory to configure the linker with
all libraries needed to be linked into the binary.

## Conficuring the template
The minimum configuration you should do.

### CMakeList.txt in root
Here the project name and version needs to be touched. The latter is even optional to create the
`project_conf.h` file used in the main.c.

You might also change the compiler version and switches.

### CMakeList.txt in libs
Add the individual library modules you want to be part of your project.

### CMakeList.txt in the specific
Set the name of the library and the c-files.

You might also change library specific compiler settings. the template doesn't change them but the
place is shown with the empthy `add_compile_options{}`.
