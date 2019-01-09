# Wee program structure

One Wee program has one driver and multiple modules.
All program files have the same extension:  *.wee

## Directives
Compiler directive symbol "#" is used to identify file type.
Wee has 3 kind of program files each with different role: 

```
#library ;reusable library
#module  ;data module/class
#driver  ;main driving program
```

**Notes;**
* A program must have one single driver file;
* A program can be created using multiple modules
* A library can be included in driver or modules programs;
* A module can be instantiated once or multiple times

## Declaration

Wee is using 3 kind of declarations:

* def: composite type or sub-type
* var: create/initialize variables
* con: define/initialize constants

**Note:**
Wee support Unicode identifiers in declarations.

## Statements

Wee statements start with a keyword.

**Examples:**

* set: assign expression value to variables
* put: output to console result of expressions
* get: accept input from console

## Code blocks
Statements can be contained in blocks of code.
Each block of code start with a specific keyword.
Block of code is ending with same keyword and final dot "."

**Keywords:**
* cycle: repetitive group of statements
* for:   create a range iteration
* is:    create a decision block
* when:  start a selection block

## Driver file

Wee is a free form language. That means indentation of code and spaces are not relevant.
In Wee method main() is optional. Instead we define a _driver_ file using directive #driver. 
This is the program entry point. One program can have a single _driver_ and many _modules_.

A _driver_ can contain statements that do not belong to any function or method.
These are called _rogue_ statements and are driving the program execution.
Rogue statements are executed top down in synchronous mode.


```
#driver "main"

; list all parameters
let i ∈ Z  ; declare control variable i
let l := $params.count() ; declare number of parameters

; check precondition
halt(1) if (l = 0)

cycle
    put $params[i]
    is (i = l)?
      exit
    no:
      i+=1
      repeat
    is.
cycle.

stop(0)
;end program
```

**Notes:** 
* This program is a #driver having file-name "main.wee";
* $params is a global system variable available in #driver and #module;
* Parameter _params_ is of type [S] that is a list are strings;
* Program _module_, _system_ and _extend_ files do not have _rogue_ statements;

## External Code
In Wee external code can be imported like this:

**Imports:**

```
wee math.*
cpp myLib:x, y, z
asm myAsm.*
```

use .* all public members are used
use :x,y,z only x,y,z members are used

**Environment variables*
Environment variables are globals anthat start with $ symbol. 
All system variables are automatic imported from OS environment.
  
## Global scope

**Import a diverse files**

Wee is using one global scope. All modules are using same global scope.
Global variables are unique and are visible in all project modules.
Global variables are lowercase and are predefined in Wee language.

```
#cpp $wee.cpp.myLib.* ;import cpp library
#asm $wee.asm.myLib.* ;import asm library
#wee $wee.lib.myLib.* ;import core library
#wee $pro.lib.myLib.* ;import project library
```

Other predefined global variables:

```
$params ;contains a list of parameters
$path   ;contains a list of folders 
```

**See example:** [gv.wee](../demo/gv.wee)

## Locale scope
A Wee a function or method can have local declarations. 
Local variables are private inside local scope.

**See example:** [lv.wee](../demo/lv.wee)

## Public members
In Wee all members that start with dot "." are public members.
A public member from another module can be access using dot notation.

```
;public variable
let .v ∈ N:

;public function
.func(x:N) => y ∈ N: 
  y := x+1 
 func.
```

## Execution
A #driver is the program main entry point. It is executed only once.
A #library do not contain executable code and can''t receive parameters

A module is executed when is imported first time using _wee_ statement. 
To delay execution modules are declaring function and methods.
Rogue statements can be used for module initialization.

## Function ABI mapping
In Wee one can use external fnctions written in Assembly, Ada, C or CPP.
Usually these mappings are implemented in #system or #extend files.

**Example:**
This is myLib.wee file: 
```
#library

cpp myLib

fib(n:Z) => x ∈ Z: 
   myLib.fib 
fib.
```

This is the driver file.
```
#driver

wee myLib.*

;use external function
put(fib(5))

write
```

To understand more about interacting with other languages check this article abput ABI:
[Application Binary Interface](https://en.wikipedia.org/wiki/Application_binary_interface)

## Single symbols

symbol| description
------|----------------------------------------------------------
  #   | Compiler directives prefix
  ;   | Single line comment  \| End of block
  .   | Dot operator: Member \| Public
  :   | Declaration \| Definition \| Key:Value Pairs
  '   | ASCII string literals are using single quotes "'"
  "   | Unicode string literals are using double quotes '"'
  $   | Global variables prefix \| System environment constants
  @   | Context variable prefix \| Static variable prefix
  !   | Factorial: y = n!     \| First element subscript a[!]   
  ?   | Decision "yes" branch \| Last element subscript  a[?]
  \|  | Used in modulo function y = \|x\|
  *   | Parameter prefix for variable arguments
  _   | Anonymous variable \| Ignore value received

## Operators

symbol| description
------|----------------------------------------------------------
 +    | Numeric addition |\ string concatenation
 -    | Numeric subtraction |\ difference between two collections 
 ^    | Numeric power 
 *    | Numeric multiplication
 ↻    | String multiplication a = "*" ↻ 3 => a = "***"   
 /    | Numeric division
 %    | Numeric reminder 
 


## Brackets
symbol| description
------|----------------------------------------------------------
  ()  | Expression or group of expressions \| tuple
  {}  | Enumeration, structure, set or hash map
  []  | List, array or range \| access of element by index 



## Double Symbols

symbol| description
------|-----------------------------------------------------------------------
 \\   | Escape literal character (\n = New Line)
  <:  | Define new data type from a supertipe or create a composite type 
 ..   | Define range between two values [n..m] \| array slice [n..m]
 .,   | Define range and exclude left limit  [n.,m]
 ,.   | Define range and exclude right limit [n,.m]
 ,,   | Define range and exclude the limits [n,,m]
 ->   | Function pipeline \| unsafe conversion 
 <+   | Insert one or more values into a string template
 
 
## Modifiers

symbol| description
------|-----------------------------------------------------------------------
 :=   | Modify variable value \| Initialize variables
 +=   | Addition modifier 
 -=   | Subtraction modifier 
 ^=   | Numeric power modifier
 *=   | Multiplication modifier 
 /    | Numeric division
 /=   | Division modifier 
 %    | Numeric reminder 
 %=   | Reminder modifier
 :+   | Append \| push \| enqueue (LI)
 :~   | Remove \| pop  \| dequeue  (LO/FO)
 
## Logical

Logical operators return: 1 = True or 0 = False

|symbol| meaning
|------|-----------------------------------
|  ∈   | Element belong to set 
|  ∉   | Not element of set
|  ¬   | Logic NOT
|  ∧   | Logic AND
|  ∨   | Logic OR 
|  ⊕   | Logic XOR


## Bitwise Operators

We use "." to represent "bit" prefix.

 symbol | description
--------|----------------------------------
  <<    | shift bits to left  
  >>    | shift bits to right
  .¬    | bit not
  .∧    | bit and
  .∨    | bit or
  .⊕    | bit xor
 
## Relations

Relation operators are used to compare expressions.

|symbol| meaning
|------|-----------------------------------
  =    |equality of two values  
  ≠    |divergence of two values (not equal)
  ≈    |almost equal (ignore decimals)
  \>   |value is greater than 
  \<   |value is less than
  ≥    |greater than or equal to
  ≤    |less than or equal to

## Statements

Wee has 23 keywords to create statements.

| Keyword  | Purpose
|----------|--------------------------------------------------
| wee      | Import Wee module
| asm      | Import Assembly
| cpp      | Import C or C++ module
| stop     | stop program execution with no message
| halt     | stop program with error message
| def      | Define user data type or type alias using :
| let      | Declare variables using : with type or :=
| set      | Establish or modify value for variables using :=
| out      | Add something to console buffer but no new line 
| get      | Accept input from console and wait for read
| read     | Accept user input from console 
| put      | Put some parameters to console and add new line
| write    | Output expression result to console 
| for      | Start _range iteration_ or _collection iteration_
| do       | Used with iteration _for_
| next     | Continue iteration _for_ from beginning
| done     | Terminate iteration _for_ and continue after for.
| cycle    | Start point for repetitive block
| repeat   | Jump to beginning of _cycle_ block
| exit     | exit inner cycle and continue after cycle.
| if       | Conditional statement execution 
| is       | Start logical decision block
| no       | Second path of conditional block

## Basic types

Wee define 6 basic types:
  
| Type    |Wee|Description
|---------|---|-----------------------------  
| ASCII   | A |Define one ASCII character
| Logic   | L |Logic data type
| Integer | Z |Integer numbers
| Natural | N |Natural numbers
| Real    | R |Double precision numbers

## Composite types

Wee define composite types:

| Type    |Wee|Description
|---------|---|-----------------------------------  
| String  | S |Define ASCII long string
| Unicode | U |Define unicode based string
| Date    | D |Date:YDM DMY MDY
| Time    | T |Time data type

## Collection types
In Wee there are available following collection types:

* [] = Array   
* [] = Matrix   
* [] = List
* {} = Hash Map
* {} = Set 
* {} = Queue
* {} = Stack
 
## Built-in functions/methods
 
**Introspection** 

| Function | Purpose
|----------|------------------------------------------ 
| type     | type name
| size     | type size 
| length   | type length 
| capacity | type capacity
| min      | type minim limit
| max      | type maxim limit
 
**List/strings** 

| Function | Purpose
|----------|------------------------------------------ 
| split    | Split a string into a list / array
| join     | Join a list into a string 
| find     | Search one sub-string in a string
| replace  | Replace one sub-string in a string
| trim     | Remove blank spaces from string
| right    | Allign string to right by adding spaces
| left     | Allign string to left by adding spaces
| center   | Allign string to center by adding spaces
 
 **Numeric**
 
| Function | Purpose
|----------|------------------------------------------ 
| round    | Convert one real into an integer
| floor    | Convert one real into an integer
| parse    | Convert one string into one number
| random   | Create random numbers
 
**Mathematics**

| Function | Purpose
|----------|------------------------------------------ 
| sin      | sinus 
| cos      | cosinus
| tan      | tangetn
| pow      | power
| sqr      | square root
| fac      | factorial
| mod      | modulo y = \|x\|  

**Read next:** [Syntax Overview](syntax.md)
