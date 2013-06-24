CodeSniffer-PSR2-extended
=========================

Extended version of PHP_CodeSniffer's PSR2 rule set.

While CodeSniffer's PSR2 checking is excellent and following the PSR2 standard,
it is not checking all things I would like to be checked (far from it!)

The PSR standards only describe code styling, but lack things like PHPDoc.
Also there are a couple of more checks that can be done to make sure my code looks clean and healthy.

The solution? I've created my own standard for PHP_CodeSniffer. Below a list of the additions I've made to the current PSR2 standard.

Additions
---------
The following addition check are done using this rule set:

### 1. Comments & PHPDocs
- Warns about Fixme's and Todo's in comments
- Verifies that block comments are used appropriately
- Verifies that the stars in a doc comment align correctly
- Empty catch clause must at least have comment
- Parses and verifies the doc comments for functions
    * A comment exists
    * There is a blank newline after the short descriptio
    * There is a blank newline between the long and short description
    * There is a blank newline between the long description and tags
    * Parameter names represent those in the method
    * Parameter comments are in the correct order
    * Parameter comments are complete
    * A type hint is provided for array and custom class
    * Type hint matches the actual variable/class type
    * A blank line is present before the first and after the last parameter
    * A return type exists
    * Any throw tag must have a comment
    * The tag order and indentation are correct
    * Verifies that a @throws tag exists for a function that throws exceptions
    * Verifies the number of @throws tags and the number of throw tokens matches
    * Verifies the exception type
- Verifies that there is adequate spacing between comments
- Verifies that there are no comments after statements
- Parses and verifies the variable doc comment
    * A variable doc comment exists
    * There is a blank line after the short description
    * There is a blank line between the description and the tags
    * Verifies the order, indentation and content of each tag
- Parses and verifies the doc comments for files
    * A doc comment exists
    * There is a blank newline after the short description
    * There is a blank newline between the long and short description
    * There is a blank newline between the long description and tags
    * Verifies the order of the tags
    * Verifies the indentation of each tag
    * Verifies existence of required @copyright tag
    * Verifies existence of required @link tag
    * Verifies existence of required @license tag
    * Verifies required and optional tags and the format of their content
- Parses and verifies the doc comments for classes
    * A doc comment exists
    * There is a blank newline after the short description
    * There is a blank newline between the long and short description
    * There is a blank newline between the long description and tags
    * Verifies existence of required @author tag
    * Verifies the order of the tags
    * Verifies the indentation of each tag
    * Verifies required and optional tags and the format of their content
- Verifies that no perl-style comments are used (Comments using #)

### 2. General code style
- Verifies that there is a single space after cast tokens
- If an assignment goes over two lines, ensure the equal sign is indented
- Verifies that the opening PHP tag is the first content in a file
- Verifies that two strings are not concatenated together; suggests using one string instead.
- Verifies that there are no spaces around square array brackets
- Verifies that the closing braces of scopes are aligned correctly
- Verifies that all arithmetic operations are bracketed
- Verifies that there is only one value assignment on a line, and that it is the first thing on the line
- Verifies that any use of Double Quotes ("") are warranted
- Verifies that there are spaces between the concatenation operator (.) and the strings being concatenated

### 3. Classes
- Verifies that the same class (or interface name) isn't declared in multiple files
- Verifies that only one class is declared per file
- Verifies that only one interface is declared per file
- Verifies that the file name and the name of the class contained within the file match

### 4. Class methods, members & functions
- Verifies PHP 5 constructor syntax, which uses "function __construct()", avoid PHP4 syntax
- Detects unnecessary final modifiers inside of final classes
- Verifies the for unused function parameters
- Detects unnecessary overridden methods that simply call their parent
- Ensures that variables are not passed by reference when calling a function
- Verifies the cyclomatic complexity (McCabe) for functions (Complexity set to 15)
- Verifies the nesting level for methods (Nesting level set to 10)
- Verifies that duplicate arguments are not used in function declarations
- Verifies that class vars have scope modifiers
- Verifies that class members have scope modifiers
- Verifies self member references
    * self:: is used instead of Self::
    * self:: is used for local static member reference
    * self:: is used instead of self ::

### 5. Control structures
- Detects for-loops that can be simplified to a while-loop
- Detects incrementer jumbling in for loops
- Detects unconditional if- and elseif-statements ( if(true){ } )
- Verifies that inline control statements are not present
- Verifies that inline IF statements are not being used
- Verifies that no empty statement exists

### 6. Operators
- Verifies the use of IDENTICAL type operators rather than EQUAL operators
- Verifies that the ++ operators are used when possible and not used when it makes the code confusing
- Verifies that the logical operators 'and' and 'or' are not used
- Ensures that the value of a comparison is not assigned to a variable

### 7. Others
- Discourages the use of deprecated functions that are kept in PHP for compatibility with older versions
- Discourages the use of alias functions that are kept in PHP for compatibility with older versions
- Verifies that the include_once is used in conditional situations, and require_once is used elsewhere
- Verifies that brackets do not surround the file being included
- Warn about commented out code
- Bans the use of size-based functions in loop conditions
- Discourages the use of debug functions
- Bans the use of eval()
- Bans the use of the "global" keyword
- Bans the use of heredoc
- Bans the use of inner functions
- Verifies all calls to inbuilt PHP functions are lowercase
- Warns about code that can never been executed
- Checks for usage of "$this" in static methods
- Verifies that any strings that are "echoed" are not enclosed in brackets like a function call

Note
----
This rule set truly extends the PSR2 rule set of PHP_CodeSniffer.
If your version of PHP_CodeSniffer does not have the PSR2 rule set installed (probably because the version of PHP_CodeSniffer you are using is to old), this will NOT work!
