Code Conventions
===============
This document describes the code conventions and guidelines to be followed in all Ultimaker code, regardless the programming environment.

Do note that not all the code convention described here have been fully implemented yet. However, any newly committed code should follow the conventions below.

Also familiarise yourself with the following guidelines for examples and ideas and so on and so forth:
| Language | Guidelines | Link |
| :---: | :--- | :---
| Python | PEP8 | https://www.python.org/dev/peps/pep-0008/ |
| PHP | PSR-2 | http://www.php-fig.org/psr/psr-2/ |
| C++ | Best Practices | https://www.gitbook.com/book/lefticus/cpp-best-practices/details |
| QML | tbd | tbd |
| JavaScript | tbd | tbd |
| CSS | tbd | tbd |
| html | tbd | tbd |

These should be followed unless overruled in this document or the specific guidelines set for each language.
In certain cases specific rules might apply depening on the programming languaged used, but in general all the conventions would apply all programming and/or scripting languages.
These can be found inside the __code_conventions__ folder.

When contributing to other OpenSource projects, those coding guidelines must be followed.

----------

Basic Language
----------------------
*** New *** - to be discussed
What language is leading for the sake of consistency? color / colour; favourite / favorite ?
> Proposal:
> With EN-US being more compact and likely more widely used over EN-GB, the preference is to use EN-US as the base.

Commenting
----------------------
There are 4 kinds of comments that can be used:
>- Commenting for documentation purposes (see Doxygen Commenting in different document)
>- Comments to make clear something needs to be examined and possibly be refactored (referring to a Jira issue/story)
>- Comments that are needed to explain a workaround to some unexpected behaviours
>- In case of clariftying a choice made to implement something in a certain way, comments can be used to explain why

Comments in general never should state the obvious. If that's the case, rethink the strategy and solution.

Logging
----------------------
Logging should be done on a few levels:
>- **DEBUG**: Verbose logging -> logging data that is useful to debug parts of the code being run
>- **INFO**: Logging -> logging information that can be seen as feedback to a user on his/her actions and the actions that the system performs
>- **WARN**: Warning message are an indication to the user that something is not entirely right, but might not yet be a big issue
>- **ERROR**: When a function cannot continue at all, but it doesn't mean that the application has to stop working.
>- **CRITICAL**: An error is a situation that cannot be overcome without external influence. This implies that the application is very likely to stop working at all

With the above guidelines, try to use common sense in what log level to use. Especially with DEBUG and INFO the border is not very clear.

*** New *** - to be discussed
uranium logging
python logging
[easylogging++ (boost)]
compile time log level?

Indenting / trailing whitespaces
-------------
The following rules apply:
>- Never use TABs
>- Indenting is allways 4 spaces
>- No trailing whitespaces

Make sure that all editors used enforce these settings for the lines edited  changed. For example the setting that a TAB will be replaced with 4 spaces and so on. 
Untouched code stays the same, unless a complete refactoring is going to happen.

Codeblocks (not Code::Blocks :))
-------------
A **codeblock** [ https://en.wikipedia.org/wiki/Block_(programming) ] is a piece of code grouped together logically.

>- Allways use a codeblock if possible and allowed in the language construction
>- Codeblocks allways start on a new line
>- The opening and closing codeblock delimiters should always be on a separate line on the same indentation level as the keywords (e.g. `if`, `while`, `else`).
>- Any code within the a codeblock must be indented to one indentation level further. 
>- Indentation levels differ by 4 spaces.

Some examples of the previous rules:

Bad code:
```[.cpp]
    if (condition)       
    { cout << "Do nothing" << EOL; 
    } else cout << "Hahaha" << EOL;
```

Good code:
```[.cpp]
if (condition)
{ // New block, allways start block delimiter on new line
    // indent always with 4 spaces, never with tabs
    cout << "Do nothing" << EOL;
} // Block end delimiter also on new line
else // else on new line
{ // A code block is allways possible in this case, so use it
    cout << "Hahaha" << EOL;
}
```

Naming conventions
-------------
The following naming conventions should be followed:
| Type | Description | Example | Definition |
| :--- | :--- | :--- | :--- |
| Variable | all lowercase, words separated with underscore | ```this_is_a_variable_name``` |
| Function | starts with lowercase and then uppercase for each word | ```checkIfThisIsValidFunctionName()``` | CamelCase https://en.wikipedia.org/wiki/CamelCase |
| Class | starts with uppercase and then uppercase for each word | ```ThisIsMyClass``` | PascalCase https://en.wikipedia.org/wiki/PascalCase |
| Macros / constants / enum | all uppercase, words separated with underscores | ```THIS_IS_A_CONSTANT``` |


Function names should start with a verb (e.g. get, set, run, execute, validate etc.) or a question (e.g. is, has, can) as this helps a lot with understanding what the implementation is about.

Example:
```[.cpp]
#define UPPER_CASE_MACRO 1

class UpperCamelCaseClass
{
    private:
    MemberVariableType with_underscores;

    public:
    void lowerCamelCaseFunction(ParamVariableType also_with_underscores)
    {
        LocalVariableType using_underscores;
    }
};
```

Spacing
-------------
Spacing in text should adhere to the following rules:
>- Binary operators (e.g. `+` `-` `*` `/` `=` `+=` `-=` `/=` `*=`) should be enclosed by a space at both sides, except for the operators `->`, `.`, `->*`, `.*`, `,` and `::`.
>- After a comma (`,`) there should be a space - not before.
>- For keywords with parentheses `(` and `)` (e.g. `if`, `for`, `while`, `switch`) there should be a space in between the keyword and the opening parenthesis.
>- In the `for` statement: place a space after the `;`, but not before.
>- When calling a function, place the opening parenthesis `(` of the parameters right after the function name, without inserting a space.
>- When calling the index `[]` operator, don't insert a space before the `[`.

 
Example:
```[.cpp]
for (int i = 0; i < len; i++)
{
    int j, k;
    j = k = 1 + calculateSomeMathematicalOperation(i);
    std::vector<int> l;
    vector.resize(len);
    vector[i] = j;
}
```

Ordering
-------------
A simple ordering system helps to make code more human readable:
>- **Encapsulation**:  Go from *public* via *protected* to *private*. Reasoning behind this is to help with the OOP paradigm of implementation hiding. When using a class, one is more interested in the *public* items. For inheriting the *protected* ones can be interesting, while the *private* parts would only have a meaning to the maintainer of the class. [ https://en.wikipedia.org/wiki/Object-oriented_programming#Encapsulation ]
>- **Members Functions**: Implement functions following a Top-Down strategy starting with constructors and/or destructors in case of classes. That way, a class implementation can be read as a page from a book: from top to bottom providing clarity. This also helps with with declarative language constructs like C/C++ where this order can be maintained in the header file.
>- **Members Variables**: A good way to define variables is to use simple alphanumerical sorting.

Optional, it might be good to have these section marked with comments, simulating a region, like:
```[cpp]
// Begin of Public section
...
// End of Public section
```

Strings
-------------
Strings are double quotes. While python and php allow single and double quoted strings, and PEP8 only says "pick a rule and stick to it". We decided to do double quotes to match C++.

Lines and Linelength
-------------
>- **Maximum line length**: There is no hard limit on the line length, but as a thumb of rule, try to keep it to at most 120 characters. This helps doing the code reviews!
>- **Single statement**: A single line contains only one statement

Alignment
-------------
*** New *** - to be discussed
Align code for better readability.
This can be done on assignment level, parameter passing on function, array definitions and so on. 

Code Guidelines
===============
Below are a couple of guidelines which should be followed, unless there's good reason not to. Most of these are her from an architectural point of view.

----------

Class Files
-------------
*** Changed ***
Each class would have its own file with a filename corrseponding to the class name.
Hence a class named Printer would have a printer.h(pp) + printer.cpp for C/C++, a printer.py for Python and a printer.php for PHP

Namespaces
-------------
*** New ***
[ TO BE DISCUSSED ]

Functions
-------------
*** New *** - to be discussed
>- Functions should return only 1 value (the return value)
>- If a function needs to return more, the return value could be a dictionary / hashtable construction
>- The number of arguments to a function (especially when it's a member of a class) should not exceed 5, or use a varargs construction.
>- Functions should not contain more then 7-10 (?) lines of code. The pro is that functions have a more contained implementation leading to robust, testable, readable, less error-prone implementation. The con is that it will cause a bit more overhead (runtime calls) and documentation (for more functions)

Basic principles
-------------
*** New *** - to be discussed
Adhere to the following coding principles:
>- **DRY** instead of **WET**: Don't Repeat Yourself / (Write Everyting Twice, We Enjoy Typing) [ https://en.wikipedia.org/wiki/Don%27t_repeat_yourself ]
>- **KISS**: Keep It Simple, Stupid [ https://en.wikipedia.org/wiki/KISS_principle ] 
>- **GRASP**: General Responsibility Assignment Software Patterns [ https://en.wikipedia.org/wiki/GRASP_(object-oriented_design) ]
>- **SOLID**: Single responsibility, Open-closed, Liskov substitution, Interface segregation and Dependency inversion (segregation of concern) [ https://scotch.io/bar-talk/s-o-l-i-d-the-first-five-principles-of-object-oriented-design ]

Following these guidelines leads to better coding, faster coding, less bugs. easier testing and reusable code.

Localization
-------------
For localization see the __Localization.md__ document on how to provide ways to translate the interface.

Documenting
-------------
See the __Doygen__ documentation on how to use this to document the code.
