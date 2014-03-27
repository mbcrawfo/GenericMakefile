GenericMakefile
===============

A generic makefile for use with small/medium C and C++ projects. Allows for
easy project setup without the need to create tedious build rules or
dependency lists.

#Features:
* Automatically finds and compiles all source files within the source directory.
* Automatically generates dependecies as files are compiled, ensuring that files are correctly recompiled when dependecies have updated.
* Includes configurations for normal (release) build and debug build suitable for GDB debugging.
* Times the compilation of each file and the entire build.
* Generates version numbers based on git tags (see below), which are passed the compiler as preprocessor macros.

##Git Tags:
Tags should be made in the format "vMAJOR.MINOR[-description]", where MAJOR
and MINOR are numeric. Four macros will be generated and passed to the
preprocessor:
* *VERSION_MAJOR* - The major version number from the most recent tag.
* *VERSION_MINOR* - The minor version number from the most recent tag.
* *VERSION_REVISION* - The number of commits since the most recent tag.
* *VERSION_HASH* - The SHA of the current commit. Includes the "-dirty" suffix  if there are uncommited changes.

#Limitations:
* Doesn't really support multiple types of source files in the same project.
* Deleting a header file requires a "make clean" and full recompile, unless
  you want to manually find and delete all the dependency files that use it.
* No easy way to exclude files from the build. You can either change the
  extension of files to be excluded, or use preprocessor flags for
  conditional compilation.

Thanks to my friend Jay and people on Stack Overflow for help with regex
to parse the version info.
