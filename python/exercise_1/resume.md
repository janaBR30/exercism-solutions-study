Introduction
Python is a dynamic and strongly typed programming language. It employs both duck typing and gradual typing via type hints.

While Python supports many different programming styles, internally everything in Python is an object. This includes numbers, strings, lists, and even functions.

We'll dig more into what all of that means as we continue through the track.

This first exercise introduces 4 major Python language features:

Name Assignment (variables and constants),
Functions (the def keyword and the return keyword),
Comments, and
Docstrings.

In general, content, tests, and analyzer tooling for the Python track follow the style conventions outlined in [PEP 8](https://www.python.org/dev/peps/pep-0008/) and [PEP 257](https://www.python.org/dev/peps/pep-0257/) for Python code style, with the additional (strong) suggestion that there be no single letter variable names.

On the Python track, [variables][variables] are always written in [`snake_case`][snake case], and constants in `SCREAMING_SNAKE_CASE`.

[variables]: https://realpython.com/python-variables/
[snake case]: https://en.wikipedia.org/wiki/Snake_case
Name Assignment (Variables & Constants)
Programmers can bind names (also called variables) to any type of object using the assignment = operator: <name> = <value>. A name can be reassigned (or re-bound) to different values (different object types) over its lifetime.

>>> my_first_variable = 1  # my_first_variable bound to an integer object of value one.
>>> my_first_variable = 2  # my_first_variable re-assigned to integer value 2.

>>> print(type(my_first_variable))
<class 'int'>

>>> print(my_first_variable)
2

>>> my_first_variable = "Now, I'm a string." # You may re-bind a name to a different object type and value.
>>> print(type(my_first_variable))
<class 'str'>

>>> print(my_first_variable)
"Now, I'm a string."  # Strings can be declared using single or double quote marks.
Constants
Constants are names meant to be assigned only once in a program. They should be defined at a module (file) level, and are typically visible to all functions and classes in the program. Using SCREAMING_SNAKE_CASE signals that the name should not be re-assigned, or its value mutated.

Functions
The def keyword begins a function definition. Each function can have zero or more formal parameters in () parenthesis, followed by a : colon. Statements for the body of the function begin on the line following def and must be indented in a block.

# The body of a function is indented by 2 spaces, & prints the sum of the numbers.
def add_two_numbers(number_one, number_two):
  total = number_one + number_two
  print(total)  

>>> add_two_numbers(3, 4)
7


# Inconsistent indentation in your code blocks will raise an error.
>>> def add_three_numbers_misformatted(number_one, number_two, number_three):
...     result = number_one + number_two + number_three   # This was indented by 4 spaces.
...    print(result)     #this was only indented by 3 spaces
...
...
  File "<stdin>", line 3
    print(result)
    ^
IndentationError: unindent does not match any outer indentation level
Functions explicitly return a value or object via the return keyword:

# Function definition on first line, explicit return used on final line.
def add_two_numbers(number_one, number_two):
  return number_one + number_two   


# Calling the function in the Python terminal returns the sum of the numbers.
>>> add_two_numbers(3, 4)
7

# Assigning the function call to a variable and printing 
# the variable will also return the value.
>>> sum_with_return = add_two_numbers(5, 6)
>>> print(sum_with_return)
11
Functions that do not have an explicit return expression will implicitly return the None object. The details of None will be covered in a later exercise. For the purposes of this exercise and explanation, None is a placeholder that represents nothing, or null:

# This function does not have an explicit return.
def add_two_numbers(number_one, number_two):
  result = number_one + number_two


# Calling the function in the Python terminal appears 
# to not return anything at all.
>>> add_two_numbers(5, 7)
>>>


# Using print() with the function call shows that 
# the function is actually returning the **None** object.
>>> print(add_two_numbers(5, 7))
None


# Assigning the function call to a variable and printing 
# the variable will also show None.
>>> sum_without_return = add_two_numbers(5, 6)
>>> print(sum_without_return)
None
Calling Functions
Functions are called or invoked using their name followed by (). Dot (.) notation is used for calling functions defined inside a class or module.

>>> def number_to_the_power_of(number_one, number_two):
        return number_one ** number_two
...

>>> number_to_the_power_of(3,3) # Invoking the function with the arguments 3 and 3.
27


# A mis-match between the number of parameters and the number of arguments will raise an error.
>>> number_to_the_power_of(4,)
...
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: number_to_the_power_of() missing 1 required positional argument: 'number_two'


# Calling methods or functions in classes and modules.
>>> start_text = "my silly sentence for examples."
>>> str.upper(start_text)  # Calling the upper() method for the built-in str class.
"MY SILLY SENTENCE FOR EXAMPLES."

# Importing the math module
import math

>>> math.pow(2,4)  # Calling the pow() function from the math module
>>> 16.0
Comments
Comments in Python start with a # that is not part of a string, and end at line termination. Unlike many other programming languages, Python does not support multi-line comment marks. Each line of a comment block must start with the # character.

Docstrings
The first statement of a function body can optionally be a docstring, which concisely summarizes the function or object's purpose. Docstrings are declared using triple double quotes (""") indented at the same level as the code block:

# An example from PEP257 of a multi-line docstring.
def complex(real=0.0, imag=0.0):
    """Form a complex number.

    Keyword arguments:
    real -- the real part (default 0.0)
    imag -- the imaginary part (default 0.0)
    """

    if imag == 0.0 and real == 0.0:
        return complex_zero
Docstrings are read by automated documentation tools and are returned by calling the special attribute .__doc__ on the function, method, or class name. Docstring conventions are laid out in PEP257.

Docstrings can also function as lightweight unit tests, which will be covered in a later exercise.

# An example on a user-defined function.
>>> def number_to_the_power_of(number_one, number_two):
        """Raise a number to an arbitrary power.

        :param number_one: int the base number.
        :param number_two: int the power to raise the base number to.
        :return: int - number raised to power of second number

        Takes number_one and raises it to the power of number_two, returning the result.
        """

        return number_one ** number_two
...

# Calling the .__doc__ attribute of the function and printing the result.
>>> print(number_to_the_power_of.__doc__)
Raise a number to an arbitrary power.

    :param number_one: int the base number.
    :param number_two: int the power to raise the base number to.
    :return: int - number raised to power of second number

    Takes number_one and raises it to the power of number_two, returning the result.