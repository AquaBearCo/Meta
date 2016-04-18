# Doxygen as documenting tool

[ TODO ]
We use [Doxygen](www.doxygen.org/) to generate documentation. Try to keep your documentation in doxygen style.

Doxygen documentation should always be next to the declaration of the thing documented - in the header file.

Here's a small example:
~~~~~~~~~~~~~~~{.cpp}
/*!
 * Doxygen style comments!
 *
 * \param param1 explanation may refer to another \p param2
 * \param param2 each parameter should be explained
 * \return explanation of what is returned
 */
int function(int param1, int param2)
{
    // non-doxygen style comments on implementation details
}

int member; //!< inline doxygen comment on the entry to the left
~~~~~~~~~~~~~~~
