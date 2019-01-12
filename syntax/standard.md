## Standard Library

Standard library is automatically included in Wee language. It contains a type system and standard functions. In the future ee will explain details about each function and data type.


## Type system

**Basic types**

| Name        |Wee| Description
|-------------|---|-------------------------------------------------------------
| ASCII       |A  | ASCII character       (two bytes)
| Binary      |B  | Positive short number (two bytes)
| Natural     |N  | Positive large numbar 
| Integer     |Z  | Positive or negative number 
| Logical     |L  | Logical number {0,1}
| Real        |R  | Real number (double precision)

**Composite types**

| Name        |Wee| Description
|-------------|---|-------------------------------------------------------------
| String      |S  | ASCII unlimited capacity
| Unicode     |U  | Unicode strinh: "♙ ♖ ♘ ♗ ♔ ♕ ..." 
| Date        |D  | 'YYYYDDMM' -> YDM, 'DD/MM/YYYY' -> DMY, 'MM/DD/YYYY' -> YDM
| Time        |T  | 'hh:mm,9999ms' -> T12 'hh:mm__, 9999ms' __={am/pm} + {T12, T24}

 
## Introspection

| Function | Purpose
|----------|------------------------------------------ 
| type     | type name
| size     | type size 
| length   | type length 
| capacity | type capacity
| min      | type minim limit
| max      | type maxim limit
 
## List/strings

| Function | Purpose
|----------|------------------------------------------ 
| split    | Split a string into a list / array
| join     | Join a list into a string 
| find     | Search one sub-string in a string
| replace  | Replace one sub-string in a string
| trim     | Remove blank spaces from string
| right    | Align string to right by adding spaces
| left     | Align string to left by adding spaces
| center   | Align string to center by adding spaces
 
 ## Numeric
 
| Function | Purpose
|----------|------------------------------------------ 
| round    | Convert one real into an integer
| floor    | Convert one real into an integer
| parse    | Convert one string into one number
| random   | Create random numbers

## File IO

| Function | Purpose
|----------|------------------------------------------ 
| exist    | Check if file exist on disk
| list     | Read file list from directory
| open     | Open a file for read or write
| close    | Close a file after using it
| erase    | Remove a file from disk
| clean    | Remove all files from directory
| make     | Make a directory
| remove   | Remove a directory
| tree     | Read directory tree in memory
| find     | Find a list of files in directory

 
## Mathematics

| Function | Purpose
|----------|------------------------------------------ 
| sin      | sinus 
| cos      | cousin
| tan      | tangent
| pow      | power
| sqr      | square root
| fac      | factorial
| mod      | modulo y = \|x\|  

**Read next:** [Syntax Overview](syntax.md)
