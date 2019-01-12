## Operators

In Wee the most common operators are using ASCII symbols.    
Uncommon operators are using Unicode symbols and are difficult to input.

symbol| description
------|----------------------------------------------------------
 =    | Define new data type, variable or parameter 
\+    | Numeric addition \| list concatenation
\-    | Numeric subtraction \| difference between two collections 
\^    | Numeric power alternative notation for: xⁿ
\*    | Numeric multiplication
 ↻    | String repetition: `"*" ↻ 3` makes a = `"***"`
 /    | Numeric division
 %    | Numeric reminder 
 &    | String concatenation 

## Single Symbols

All these single symbols you find on your standard keyword.

symbol| description
------|-------------------------------------------------------------
 \#   | Compiler directives prefix
  ;   | End of block {is; cycle; for;} \| statement separator
  .   | Dot operator: Member \| Public \| smart concatenation
  .   | Dot symbol: end of function \| method \| module
  :   | Declaration \| Definition \| Key:Value Pairs
  '   | ASCII string literals are using single quotes "'"
  "   | Unicode string literals are using double quotes '"'
  $   | Global variables prefix \| System environment constants
  @   | Context variable prefix \| Static variable prefix
  !   | Factorial: y = n!     \| First element subscript a[!]   
  ?   | Decision "yes" branch \| Last element subscript  a[?]
  \|  | Used in modulo function y = \|x\|
  \*  | Parameter prefix for variable arguments
  \_  | Anonymous variable \| Ignore value received
  \\  | Escape literal character (\\n = New Line) 
  

## Brackets

Wee is using brackets for expressions and data structures.

symbol| description
------|-----------------------------------------------------
  ()  | Expression or group of expressions \| tuple
  {}  | Enumeration, structure, set or hash map
  []  | List, array or range \| access of element by index 


## Double Symbols

Double symbols are ASCII symbols found on your keyboard.    
I have charefuly selected these symbols for maximum usability.

symbol| description
------|------------------------------------------------------
\|\*  | Begin expression comment, or nested comment
 \*\| | End expression comment or nested comment
 \--  | Start for single line comment or separator
 \==  | Start for a separator comment
 \**  | Start for a separator comment
 ..   | Define range or array slice between two values [n..m]
 ...  | Fall-through in _check_ statement before is or in
 ->   | Function pipeline \| unsafe conversion 
 <+   | Insert one or more values into a string template 
 

## Modifiers

Modifiers use a common pattern `μ:` where μ is a suggestive symbol:

symbol| description
------|---------------------------------------------------
 =:   | Assign a new value and forget the old value
 +:   | Addition modifier \| Append element in collection
 ~:   | Remove \| pop  \| dequeue  (LO/FO)
 -:   | Subtraction modifier 
 ^:   | Numeric power modifier
\*:   | Multiplication modifier 
 /:   | Division modifier 
 %:   | Reminder modifier
 <:   | Unpacking from tuple \| Enumerate values
 
## Logical

Logical operators return: 1 = True or 0 = False

|symbol| meaning
|------|-----------------------
|  ¬   | Logic NOT
|  ∧   | Logic AND
|  ∨   | Logic OR 
|  ⊕   | Logic XOR

** The table of through**

 A     | B     | A ∧ B | A ∨ B  | ¬ A   | ¬ B   | A ⊕ B
-------|-------|-------|--------|-------|-------|--------
 True  | True  | True  | True   | False | False | False
 True  | False | False | True   | False | True  | True
 False | True  | False | True   | True  | False | True
 False | False | False | False  | True  | True  | False
---------------------------------------------------------

## Bitwise Operators

Bitwise operations are executed on entire binary value.

**Note:** We use "." to represent "bit" prefix. 


| symbol | description
|--------|----------------------------------
|   ←    | shift bits to left  
|   →    | shift bits to right
|  .¬    | bit not
|  .∧    | bit and
|  .∨    | bit or
|  .⊕    | bit xor

**Examples**

 A    | B   | A .∧ B | A .∨ B  | A .⊕ B
------|-----|--------|---------|--------
 00   | 00  | 00     | 00      |  11    
 01   | 00  | 00     | 01      |  10    
 11   | 01  | 01     | 11      |  00    
 10   | 11  | 10     | 11      |  01    

**Bit Manipulation**

 A    | A ← 1 | A → 2 | .¬ A
------|-------|-------|-------
 0000 | 0000  | 0000  | 1111
 1111 | 1110  | 0011  | 0000
 0111 | 1110  | 0001  | 1000
 0110 | 1100  | 0001  | 1001


See also:[Bit Manipulation](https://en.wikipedia.org/wiki/Bit_manipulation)

 
## Relations

Relation operators are used to compare expressions.

|symbol | meaning
|-------|----------------------------------------------
|  =    |equality of two values of the same type
|  ≠    |divergence of two values (not equal)
|  ≈    |almost equal (ignore type and decimals)
|  \>   |value is greater than 
|  \<   |value is less than
|  ≥    |greater than or equal to
|  ≤    |less than or equal to

## Set operators

|symbol | meaning
|-------|--------------------------------------------------
|  ∅    | Represents empty collection: {},[],()
|  ≡    | Equivalent objects, collections or structures
|  ⊂    | Is subset of a larger set
|  ⊆    | Is subset of or equal to another set
|  ∩    | Intersection between two sets
|  ∪    | Union between two sets or maps. For lists use "+"
|  ∀    | For all elements in defined in set: (for ∀ e ∈ X).
|  ∃    | Exist element element in set (∃ 2 ∈ X)
|  ∈    | Define or check element belonging to set 

Read Next: [keywords](keywords.md)
