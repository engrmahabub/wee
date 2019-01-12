# Wee program structure

One Wee program has one driver and multiple modules.
All program files have the same extension:  *.wee

## Directives
Compiler directive symbol "#" is used to identify file type.
Wee has 3 kind of program files each with different role: 

```
#library -- reusable library
#module  -- data module/class
#driver  -- main driving program
```

**Notes**
* A program must have one single driver file;
* A program can be created using multiple modules
* A library can be included in driver or modules programs;
* A module can be instantiated once or multiple times

## Declaration

Wee is using 3 kind of declarations:

* def: composite type or sub-type
* let: create/initialize variables
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

* Each block of code start with a specific keyword.
* Block of code is ending with same keyword and ";"

**Keywords:**
* "when"  create a decision block
* "check" value multi-path selector
* "cycle" repetitive group of statements
* "for"   create a range iteration


## Driver file

Wee is a free form language. That means indentation of code and spaces are not relevant.
In Wee method main() is optional. Instead we define a _driver_ file using directive #driver. 
This is the program entry point. One program can have a single _driver_ and many _modules_.

A _driver_ can contain statements that do not belong to any function or method.
These are called _rogue_ statements and are driving the program execution.
Rogue statements are executed top down in synchronous mode.


```
#driver "main"

-- list all parameters
let i ∈ Z  -- declare control variable i
let l = $params.count() -- declare number of parameters

-- check precondition
exit 1 if (l = 0)

cycle
    put $params[i]
    when (i = l):
      stop
    else
      i +: 1
      repeat
    when;
cycle;

end.
```

**Notes:** 
* This program is a #driver having file-name "main.wee";
* $params is a global system variable available in #driver and #module;
* Parameter _params_ is of type [S] that is a list are strings;
* Program _module_, _system_ and _extend_ files do not have _rogue_ statements;
* Wee file is ending with end. Following end with "." is mandatory.

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

**Environment variables**
Environment variables are globals anthat start with $ symbol. 
All system variables are automatic imported from OS environment.
  
## Global scope

**Import a diverse files**

Wee is using one global scope. All modules are using same global scope.
Global variables are unique and are visible in all project modules.
Global variables are lowercase and are predefined in Wee language.

```
#cpp $wee.cpp.myLib.* --import cpp library
#asm $wee.asm.myLib.* --import asm library
#wee $wee.lib.myLib.* --import core library
#wee $pro.lib.myLib.* --import project library
```

Other predefined global variables:

```
$params --contains a list of parameters
$path   --contains a list of folders 
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
--public variable
let .v ∈ N:

--public function
.func(x ∈ N) => y ∈ N: 
   set y =: x+1 
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

fib(n ∈ Z) => x ∈ Z: 
   myLib.fib 
fib.
```

This is the driver file.
```
#driver

wee myLib.*

--use external function
put fib(5)

write
```

To understand more about interacting with other languages check this article about ABI:
[Application Binary Interface](https://en.wikipedia.org/wiki/Application_binary_interface)
 
**Read next:** 

1. [operators](operators.md)
1. [keywords](keywords.md)
1. [syntax](syntax.md)
1. [standard](standard.md)
1. [composite](composite.md)
1. [inference](inference.md)

**See also:**[Wiki Wee](https://github.com/sage-code/wee/wiki)