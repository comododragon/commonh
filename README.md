# Common Macro for Nice Codes

## Author

* André Bannwart Perina

## Introduction

This is a simple/straightforward header with some macros that may be used for assertion and logging in C codes.

## Licence

See LICENSE file.

## Prerequisites

None.

## How to Use

Simply include this header on your project and you're good to go.

## Summary of macros

* ```COMMON_COLOURED_PRINTS```: If this macro is defined at compile-time, some function macros will attempt to use terminal colouring for displaying information. Furthermore, some macros are supplied for colouring the output of your program (if this macro is not defined, these colour macros will be empty strings).
	* Available colours:
		* ```ANSI_COLOUR_BLACK```
		* ```ANSI_COLOUR_RED```
		* ```ANSI_COLOUR_GREEN```
		* ```ANSI_COLOUR_YELLOW```
		* ```ANSI_COLOUR_BLUE```
		* ```ANSI_COLOUR_MAGENTA```
		* ```ANSI_COLOUR_CYAN```
		* ```ANSI_COLOUR_WHITE```
		* ```ANSI_COLOUR_RESET```
	* Example of usage:
		* ```printf(ANSI_COLOUR_RED "Hello world!" ANSI_COLOUR_RESET);```
* ```ASSERT(cond)```: Assert a condition. This macro will jump to a label called ```_err``` if ```cond``` fails. Make sure to declare this label and use it wisely to handle post-error procedures.
	* Parameters:
		* ```cond```: Condition to be asserted.
	* Example of usage:
		* ```ASSERT(retVal != 0); // Will jump to _err if retVal is equal to zero```
* ```ASSERT_CALL(cond, callbacks)```: Assert a condition. If it fails, run callback statements. This macro will jump to a label called ```_err``` if ```cond``` fails. Make sure to declare this label and use it wisely to handle post-error procedures.
	* Parameters:
		* ```cond```: Condition to be asserted.
 		* ```callbacks```: Statements to be executed if ```cond``` is false. Statements might be separated by semicolon.
	* Example of usage:
		* ```ASSERT_CALL(retVal != 0, retVal = 0x100; printf("Error!\n"));```
* ```PRINT_STEP(...)```: Print a nice line for indicating steps. E.g.: ```[    ] Your formatted text goes here.```
	* Parameters:
		 * ```...```: Standard arguments for printf.
	* Example of usage:
		* ```PRINT_STEP("Executing this fancy step (iteration %d)...", i);```
* ```PRINT_SUCCESS()```: Indicate success on a previous ```PRINT_STEP``` call. E.g.: ```[ OK ] Your formatted text goes here.```
* ```PRINT_FAIL()```: Indicate failure on a previous ```PRINT_STEP``` call. E.g.: ```[FAIL] Your formatted text goes here.```
