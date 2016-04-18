# C++ Code Conventions

## Header files (C/C++)
Example for a file CuraEngine/src/folder/SomeClass.h (UpperCamelCase):
~~~~~~~~~~~~~~~{.cpp}
#ifndef (FOLDER_SOME_CLASS_H)
#define FOLDER_SOME_CLASS_H

...

#endif //FOLDER_SOME_CLASS_H
~~~~~~~~~~~~~~~
Each header file must include a header guard as shown above. The defined macro is adopted from the path and name of the class and must follow the rules for macros (UPPER_CASE).
Here the folder `src` is skipped, because all header and implementation files of CuraEngine are in `src`.

## Null pointer (C++)
----
For C++, never use `NULL`, but use `nullptr` instead. NULL is an integer, not a pointer.

## Enums
Always use enum classes; never plain enums. Use UpperCamelCase for enum names and UPPER_CASE for the values.

Example:
~~~~~~~~~~~~~~~{.cpp}
enum class EnumExample
{
    ELEM0 = 0,
    ELEM1 = 1
};

EnumExample var = EnumExample::ELEM0; // call enum value via the scope of the enum class
~~~~~~~~~~~~~~~

## Implementation
----
All implementations should be in .cpp files. An exception is template functions, which must be implemented in the header file.

Sometimes including the implementation in the header file can make it easier for the compiler to inline functions.

## Const vs Non-const
*** New ***
----
The best practice is to use const when and wherever possible. This is for both arguments declared in functions as well as the return values of the functions and the functions themselves (when they don't change the internal state of the object).
In the long run this will make the code, libraries and runtime more stable and robust.
In the short run this might cause some friction with (older) code that does not use this concept (yet).



## Pointers vs. References used as return values in argument list *** Changed/New ***
-----
[ TO BE DISCUSSED ]
In the end this was not as much a discussion as to use pointer or references, but what to use when using arguments to return values.

This has a bigger impact on documentation part of Doxygen: if arguments are allowed to be used to return values, then for all arguments everywhere, using doxygen commenting, [in] and [out] tags must be put in the comments describing the arguments.
