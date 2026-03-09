# PlatformIO
Search and install the platform of: `teensy`.

# LSP
To get proper LSP support, run: `pio run -t compiledb`.

# Code requirements
Read the PDFs in this directory.  The summary is given as follows:

## Rule: 1
Restrict all code to very simple control flow constructs; do not use `goto` statements, `setjmp` or `longjmp` constructs, or direct or indirect recursion.

## Rule: 2
Give all loops a fixed upper bound.  It must be trivially possible for a checking tool to prove statically that the loop cannot exceed a preset upper bound on the number of iterations.  If a tool cannot prove the loop bound statically, the rule is considered violated.

## Rule: 3
Do not use dynamic memory allocation after initialization.

## Rule: 4
No function should be longer than what can be printed on a single sheet of paper in a standard format with one line per statement and one line per declaration.  Typically, this means no more than about 60 lines of code per function.

## Rule: 5
The code's assertion density should average to minimally two assertions per function. Assertions must be used to check for anomalous conditions that should never happen in real-life executions.  Assertions must be side effect free and should be defined as Boolean tests.  When an assertion fails, an explicit recovery action must be taken such as returning an error condition to the caller of the function that executes the failing assertion.  Any assertion for which a static checking tool can prove that it can never fail or never hold violates this rule.

## Rule: 6
Declare all data objects at the smallest possible level of scope.

## Rule: 7
Each calling function must check the return value of nonvoid functions, and each called function must check the validity of all parameters provided by the caller.

## Rule: 8
The use of the preprocessor must be limited to the inclusion of header files and simple macro definitions.  Token pasting, variable argument lists (ellipses), and recursive macro calls are not allowed.  All macros must expand into complete syntactic units.  The use of conditional compilation directives must be kept to a minimum.

## Rule: 9
The use of pointers must be restricted.  Specifically, no more than one level of dereferencing should be used.  Pointer dereference operations may not be hidden in macro definitions or inside `typedef` declarations.  Function pointers are not permitted.

## Rule: 10
All code must be compiled, from the first day of development, with all compiler warnings enabled at the most pedantic setting available.  All code must compile without warnings.  All code must also be checked daily with at least one, but preferably more than one, strong static source code analyzer and should pass all analyses with zero warnings.
