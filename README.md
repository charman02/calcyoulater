# Program Purpose
The purpose of this program is to design and implement an RPN calculator
using a stack data structure, which had to be implemented first as well.

# Files
DatumStack.h: Interface of DatumStack class
DatumStack.cpp: Implementation of DatumStack class
unit_tests.h: Unit tests used to test DatumStack member functions
RPNCalc.h: Interface of RPNCalc class
RPNCalc.cpp: Implementation of RPNCalc class
main.cpp: Runs CalcYouLater program by calling run on object of RPNCalc class
README: Explains program design and discusses specifics
Makefile: Defines rules to create executable
add.cyl: Carries out simple additions
fact.cyl: Implements factorial function using RPNCalc commands
fib.cyl: Implements Fibonacci function
fib_debug.cyl: Uses Fibonacci to demonstrate a way to debug RPNCalc programs

# Program
  make CalcYouLater
  ./CalcYouLater

# Data Structures
In order to implement RPNCalc, I utilized the DatumStack class, which is a
stack data structure that I implemented using std::list. I used std::list
to implement DatumStack because it seemed to have more member functions,
specifically modifiers, than std::vector, but either would have worked. A
stack data structure was used to implement RPNCalc because it allows the
operands to be pushed onto the stack as they are encountered, and the
operators can be applied to the operands that are at the top of the stack.
Each operand and operator can be pushed and popped from the stack in constant
time, and the order of operations is determined by the order in which the
operators are encountered in the expression.

One other way that stacks are utilized is function calls. When a function is
called, the current state of the program is pushed onto the stack as a new
stack frame. When the function completes, the stack frame is popped off the
stack, and the program resumes executing from the point where the function
was called. This allows the program to keep track of where it is in the
execution of nested functions, and to manage local variables and parameters
of each function call.

Another way that stacks are utilized is undo/redo functionality in GUIs. When
a user performs an action, the current state of the program is saved to a
stack, along with a description of the action that was taken. If the user
later decides to undo the action, the program pops the top element off the
stack, restores the saved state, and reverses the action that was taken. If
the user decides to redo the action, the program pushes the saved state back
onto the stack and repeats the action. This approach allows the program to
keep track of multiple levels of undo/redo.

# Testing
I used unit testing (unit_tests.h) to test the member functions of the
DatumStack class. I manipulated the stack size, and tested different types
of Datum objects for each function. For the RPNCalc class and the program as
a whole, I tested using the given .cyl files and converting them to .cylc so
that I could open them in my program. I used both diff testing and manually
running the program and inputting files to see what the output would look
like. For example, for add.cylc, I used diff testing, but for fib.cylc, I
pushed some numbers onto the stack, pushed fib.cylc as an rstring, entered
the file command, and finally used print to determine if the top element was
what I expected it to be.
