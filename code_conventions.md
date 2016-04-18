TODO
======
- QML
- JavaScript
- CSS

# Code Conventions
This document describes the code conventions and guidelines to be followed in all Ultimaker code, regardless the programming environment.

Do note that not all the code convention described here have been fully implemented yet. However, any newly committed code should follow the conventions below.

Also familiarise yourself with the following guidelines for examples and ideas and so on and so forth:
| Language | Guidelines | Link |
| :---: | :--- | :---
| Python | PEP8 | https://www.python.org/dev/peps/pep-0008/ |
| PHP | PSR-2 | http://www.php-fig.org/psr/psr-2/ |
| C++ | Best Practices | https://www.gitbook.com/book/lefticus/cpp-best-practices/details |

These should be followed unless overruled in this document or the specific guidelines set for each language.
In certain cases specific rules might apply depening on the programming languaged used, but in general all the conventions would apply all programming and/or scripting languages.
These can be found inside the __code_conventions__ folder.

When contributing to other OpenSource projects, those coding guidelines must be followed.

## Basic Language
*** NEW *** - color / colour; favourite / favorite ?
With EN-US being more compact and likely more widely used over EN-GB, the preference is to use EN-US as the base.

## Commenting
There are 4 kinds of comments that can be used.
* Commenting for documentation purposes (see Doxygen Commenting in different document)
* Comments to make clear something needs to be examined and possibly be refactored (referring to a Jira issue/story)
* Comments that are needed to explain a workaround to some unexpected behaviours
* In case of clariftying a choice made to implement something in a certain way, comments can be used to explain why

Comments in general never should state the obvious. If that's the case, rethink the strategy and solution.

## Logging
Logging should be done on a few levels:
* DEBUG: Verbose logging -> logging data that is useful to debug parts of the code being run
* INFO: Logging -> logging information that can be seen as feedback to a user on his/her actions (acties gebruiker en acties systeem)
* WARN: Warning message are an indication to the user that something is not entirely right, but might not yet be a big issue
* ERROR: When a function cannot continue at all, but it doesnt mean that the application has to stop working.
* CRITICAL An error is a situation that cannot be overcome without external influence. This implies that the application is very likely to stop working at all

With the above guidelines, try to use common sense in what log level to use. Especially with DEBUG and INFO the border is not very clear.

*** New ***
uranium logging
python logging
[easylogging++ (boost)]
compile time log level?

## Indenting / trailing whitespaces
* Never use TABs
* Indenting is allways 4 spaces
* No trailing whitespaces

Make sure that all editors used enforce these settings for the lines edited  changed (untouched code stays the same, unless a complete refactoring is going to happen)

## Codeblocks (not Code::Blocks :))

* Allways use a codeblock if possible and allowed in the language construction
* Codeblocks allways start on a new line
* The opening and closing codeblock delimiters should always be on a separate line on the same indentation level as the keywords (e.g. `if`, `while`, `else`).
* Any code within the a codeblock must be indented to one indentation level further. Indentation levels differ by 4 spaces.

Some examples of the previous rules:

Bad code
~~~~~~~~~~~~~~~{.cpp}
if (condition)       
{ cout << "Do nothing" << EOL; 
} else cout << "Hahaha" << EOL;
~~~~~~~~~~~~~~~

Good code
~~~~~~~~~~~~~~~{.cpp}
if (condition)
{ // New block, allways start block delimiter on new line
    // indent always with 4 spaces, never with tabs
    cout << "Do nothing" << EOL;
} // Block end delimiter also on new line
else // else on new line
{ // A code block is allways possible in this case, so use it
    cout << "Hahaha" << EOL;
}
~~~~~~~~~~~~~~~

## Naming conventions
| Type | Description | Example |
| Variables | starts with lowercase, words seperated with underscore | this_is_a_variable_name |
| Function | starts with lowercase and uppercase for each word | thisIsAFunctionName |
| Classes | starts with uppercase and uppercase for each word | | ThisIsAClassName |
| Macros / constants | all uppercase characters, words seperated with underscore | THIS_IS_A_CONSTANT |

Function names should start with a verb (e.g. get, set, run, execute, validate etc.) or a question (e.g. is, has, can) as this helps a lot with understanding what the implementation is about.

Example:
~~~~~~~~~~~~~~~{.cpp}
#define UPPER_CASE_MACRO 1

class UpperCamelCaseClass
{
private:
    MemberVariableObject with_underscores;

public:
    void lowerCamelCaseFunction(ParamObject& also_with_underscores)
    {
        LocalObject under_scores;
    }
};
~~~~~~~~~~~~~~~


enum moeten const regels volgen


## Spacing
Example:
~~~~~~~~~~~~~~~{.cpp}
for (int i = 0; i < len; i++)
{
    int j, k;
    j = k = 1 + mathematicalOperation(i);
    std::vector<int> l;
    vector.resize(len);
    vector[i] = j;
}
~~~~~~~~~~~~~~~
 * Binary operators (e.g. `+` `-` `*` `/` `=` `+=` `-=` `/=` `*=`) should be enclosed by a space at both sides, except for the operators `->`, `.`, `->*`, `.*`, `,` and `::`.
 * After a comma (`,`) there should be a space - not before.
 * For keywords with parentheses `(` and `)` (e.g. `if`, `for`, `while`, `switch`) there should be a space in between the keyword and the opening parenthesis.
 * In the `for` statement: place a space after the `;`, but not before.
 * When calling a function, place the opening parenthesis `(` of the parameters right after the function name, without inserting a space.
 * When calling the index `[]` operator, don't insert a space before the `[`.


## Ordering
----
* Members: Implement functions Top-Down, starting with constructors/deconstructors in case of classes. That way, a class implementation can be read as a page from a book: from top to bottom providing clarity. This can be an issue for declarative language constructs like C/C++ , but then it's good practice to use forward declarations.
* Go from public, protected to private. Reasoning behind this is similar. When using a class, one is more interested in the public items. For inheriting the protected ones can be interesting, while the private parts should only be meaningfull to the maintainer of the class. This helps with the OOP paradigm of implementation hiding.

## Strings
----
Strings are double quotes. While python and php allow single and double quoted strings, and PEP8 only says "pick a rule and stick to it". We decided to do double quotes to match C++.

## Lines and Linelength
*** Changed / New ***
* "Maximum line length" - There is no hard limit on the line length, but as a thumb of rule, try to keep it to at most 120 characters. This helps doing the code reviews!
* A single line contains only one statement

## Alignment
*** New ***
Align code for better readability.
This can be done on assignment level, parameter passing on function, array definitions and so on. 

# Code Guidelines
Below are a couple of guidelines which should be followed, unless there's good reason not to. Most of these are her from an architectural point of view.

## Class Files
*** Changed ***
Each class would have its own file with a filename corrseponding to the class name.
Hence a class named Printer would have a printer.h(pp) + printer.cpp for C/C++, a printer.py for Python and a printer.php for PHP

## Namespaces
*** New ***
[ TO BE DISCUSSED ]

## Functions
*** New ***
* Functions should return only 1 value (the return value)
* If a function needs to return more, the returnvalue could be a dictionary/hashtable construction
* The number of arguments to a function (especially when it's a member of a class) should not exceed 5, or use a varargs construction.
* Functions should not contain more then 7-10 (?) lines of code. The pro is that functions have a more contained implementation leading to robust, testable, readable, less error-prone implementation. The con is that it will cause a bit more overhead (runtime calls) and documentation (for more functions)

## Basic principles
*** New ***
Adhere to the following coding principles
* DRY instead of WET: Don't Repeat Yourself / (Write Everyting Twice, We Enjoy Typing)
* KISS: Keep It Simple, Stupid
* GRASP: General Responsibility Assignment Software Patterns
* SOLID: Single responsibility, Open-closed, Liskov substitution, Interface segregation and Dependency inversion (segregration of concern ^ 2)

# Localization
For localization see the __Localization.md__ document on how to provide ways to translate the interface.

# Documenting
See the __Doygen__ documentation on how to use this to document the code.
