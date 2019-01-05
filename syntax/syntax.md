# Wee Syntax

For syntax notation we use modified BNF convention:

* We use <...> to represent identifier names.
* We use  ...  to represent repetitive sequence.
* We use [...] to represent optional things. 

**Note:** This syntax is not deterministic. Sometimes [] represents the real deal. Also "..." can be used as real symbol.

## Expresions
Expresions are created using identifiers, operators, functions and constant literals. 

* can be enumerated using comma separator ","
* can be combined to create more complex expressions;
* have type that is calculated using type inference;
* can be assigned to variables using "set" and ":=";
* can be printed to console using put and out methods;
* can use () to establish order of operations;

**Examples**
```
;simple expressions in put statement
put(10)     ; print 10
put(10,11)  ; print 1011
put(n)      ; print value of n

write

;complex expressions are using ()  
put(10,11,12)    
put(10 + 10) + 15 
put((10 > 5) and (2 < 3))

;multiple expressions in a line
put(1,',',2,',',3) ;expect 1,2,3
put(10, 11, 12)    ;expected 101112   

write
```

**Note:** put statement add new line atuomatically

## Data types

Digital data is based on binary numbers: {0, 1} named bit.
Using this basic values we represent all data types.

Wee use 3 kind of data types:

1. basic data types;
2. composite data types;
3. user defined types;

## Basic Types

Data types have information about: 

1. name
1. representation
1. capacity
1. limits (min/max)
1. access  (private | public | local)
1. storage (memory  | registry)

Wee native types are represented with one uppercase larter.

| Name        |Wee| Description
|-------------|---|-------------------------------------------------------------
| ASCII       |A  | ASCII character       (two bytes)
| Binary      |B  | Positive short number (two bytes)
| Natural     |N  | Positive large numbar 
| Integer     |Z  | Positive or negative number 
| Logical     |L  | Logical number {0,1}
| Real        |R  | Real number (double precision)
| String      |S  | ASCII unlimited capacity
| Unicode     |U  | Unicode strinh: "♙ ♖ ♘ ♗ ♔ ♕ ..." 
| Date        |D  | 'YYYYDDMM' -> YDM, 'DD/MM/YYYY' -> DMY, 'MM/DD/YYYY' -> YDM
| Time        |T  | 'hh:mm,9999ms' -> T12 'hh:mm__, 9999ms' __={am/pm} + {T12, T24}

## Literals

Wee has support for numeric constants. These can be used in expressions to represent numbers.

   Literal     | Description
---------------|-------------------------------------------------------------------------
0              | integer zero
1234567890     | integer number using symbols: (0,1,2,3,4,5,6,7,8,9)
0b10101010     | binary integer using symbols: {0b,0,1}
0xFF           | hexadecimal integer using symbols: (0x,0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F)
0.5            | real number: (.,0,1,2,3,4,5,6,7,8,9)
0.0            | real number: (.,0,1,2,3,4,5,6,7,8,9) 
5E2            | real number: 5*10²  = 500  (E use positive exponent)
5e2            | real number: 5*10⁻² = 0.05 (e use negative exponent)

**Operators** 

 op | purpose
----|--------------------------------------------------------------
 :  | declare variable type or parameter type or result type
 :  | is also used as pair-up operator in composite types
 =  | assign initial value for variables, arguments or parameters
:=  | modify value of a variable using set statement or inference

## Variable declarations

Variables are defined using var keyword and ":" symbol.
One variable can have initial value defined with "=" symbol.

```
var <var_name> : <type>
var <var_name> : <type> = <constant>
```

Multiple variables can be define in one single line using comma separator:
```
var <var_name>[,<var_name>] ... : <type>
var <var_name>[,<var_name>] ... : <type> = <constant>
```

## Constant declaration

```
con <constant_name> : <type> = <value>
```

**Notes**
* Keyword _var_ will create a declaration region. 
* Keyword _con_ can be used to define a constant
* Keyword _set_ will create an initialization region.

## Modify values

We can modify variables using _set_ statement.

```
var a:Z = 10 ; declare integer variable 
var b:Z      ; declare variable b

set b := a ; modify b
put(b)      ; expected 10
```

**Statement _set_** 

* must use at least one modifier ( :=, +=, *=, ++, --, ... )
* can modify multiple variables separated with comma
* can execute multiple expressions separated with comma

**Examples:**
```
; define a constant that can't change it's value
con pi:R = 3.14

; establis a var region for multiple variables
var a   : Z ;Integer 
var x,y : R ;Double
var q,p : L ;Logic

;using modifier operators
set a := 10  ; modify value of a
set a += 1   ; increment value of a-
set a -= 1   ; decrement value of a 

; modify two variables using one constant
set  q, p := True  ; modify value of q
set  x, y := 10.5  ; modify value of x and y

;modify several variables in a single line
set a := 11, q := False, x,y := 20.15
```

## Type declaration

User can define types using keyword _def_ and operator ":".

```
def <type_name> : <type_specification> 

;using new type
var <var_name> : <type_name>
var <var_name>[,<var_name>] ... : <type_name>
```

## Type conversion

Numeric types are automatically converted when this is safe.

**Safe:**   Binary - > Integer -> Natural -> Real   
**Unsafe:** Real -> Natural -> Integer -> Binary

* Safe conversions are automatic.
* Unsafe convesion is done using operator "->"
* Operator "->" is also called "pipeline operator"

**example:**
```
var a:N=0, b:N=20
var v:R=10.5, x:R=0

;unsafe conversion
set a:= v -> N;
put(a) ; expect 10

;safe conversion
set x:= b
put(b) ; expect 20
```

## ASCII type

Wee define A = ASCII character as native type.

```
var a,b :A ;ASCII character
var x,y :B ;Binary number 

set a := '0'    ; representation of 0
set x := a -> B ; convert to 30
set y := 30     ; ASCII code for '0'
set b := y -> A ; convert to '0'
```
## Type checking

We can use variable type to verify expressions.

```
var a: Z = 0   ;integer variable
var b: R = 0.0 ;real variable

set b := 10   ; PASS: automatic safe conversion  
set a := 10.5 ; FAIL: a is of type: Integer

```

## Logic type

Logic type is an enumeration of two constants False and True.

```
def .L: {.False, .True}
```
**Notes:** 
* Public members start with dot "." symbol.
* Enumeration have binary values so L is compatible with B

## Logic operations

For Logic type "L" Wee uses two numbers: {0, 1}    
Logical operators in order of precendence: {not, and, or}

 A    | B     | A and B  | A or B | not A |  not B  | A xor B
------|-------|----------|--------|-------|---------|--------
 True | True  | True     | True   | False | False   | False
 True | False | False    | True   | False | True    | True
 False| True  | False    | True   | True  | False   | True
 False| False | False    | False  | True  | True    | False
-----------------------------------------------------------

## Operator precedence

not: has higest precedence
xor: has the lowest precendence

Precedence: { not, in, and, or, xor }

## Logical expression

Logical expression have value { 0 or 1 }

```
; simple expressions
var x:L = False
var y:L = True 

put(x)  ; will print: 0
put(y)  ; will print: 1

;complex expressions
put(x == y)  ; Will print 0
put(x and y) ; will print 0
put(x or y)  ; Will print 1

```

## Bitwise operators

Bitwise operations are executed on entire binary value.


 operator | meaning
----------|-------------------------------
  .\<    | shift left
  .\>    | shift right
  .\~    | bitwise not
  .\&    | bitwise and
  .\|    | bitwise or
  .\^    | bitwise xor

**Shifting Bits**
 
 A    | A .< 1  | A .> 2  
------|---------|----------
 0000 | 0000    | 0000
 1111 | 1110    | 0011
 0111 | 1110    | 0001
 0110 | 1100    | 0001


 A    | B   |A .\& B | A .\| B| A .\^ B| .\~ A
------|-----|--------|--------|--------|------
 00   |00   | 00     | 00     |  11    |  00 
 01   |00   | 00     | 01     |  10    |  01 
 11   |01   | 01     | 11     |  00    |  10 
 10   |11   | 10     | 11     |  01    |  01 


## Conditional

A conditional is using "if" keyword to enable or disable it''s execution.   
Observe that "if" is not a statement and can''t be used alone.

1. Conditional can apply to single line statements or method calls.   
1. Conditional can''t be used with declaration statements.
1. Conditional can''t be used with block statements.
1. Expression before the conditional must be enclosed in ()

```
<statement> if <expression>
```

The statement is executed only if the expression is True. 

```
var a:Z

; conditional execution
set a:=1 if (a == 0) 

; conditional output
put("a is 0") if (a == 0)
put("a >  0") if (a >= 0)
 
write 
```

**Notes:** 
* "if" do not pair with "else" like in other languages.
* logical expression is enclosed in (...)


## Control flow
Wee has 4 control flow statements { is, check, cycle, for }:

**decision**
A decision is based on logical expressions and keywords { is, no } and symbol "?".
Logical expression must be enclosed in paranthesis () alwais.

```
var a:= 10

; single brach
is (a == 10) ? 
   put('yes')
is.   

; two branches
is (a < 5) ?
  put('yes')
no
  put('no')
is.
```  

**selector**

This is a block statement based on keywords {check, when, else} and symbol "...".

* Using check statement we can evaluate multiple conditions.
* When first condition is true the other conditions are not evaluated.
* If no condition is true the _else_ branch is executed.

```
set a := 10

; default check 
check
  when (a == 10)
    put 'a is 10'
  when (a == 20)
    put 'a is 20'
  else
    put 'a is not 10 or 20'
check.

write
```

Using "..." (ellipsis) to continue.

```
var a = 15

; fallthrough using: "..."
check
   when (a < 0)
     put 'a <0' 
     ...
   when (a > 0)
     put 'a >0'
     ...
   when (5 <= a or a <= 10)
     put 'a >= 5 and a <= 10'
     ...
   when (a > 10)
     put 'a > 10'
   else
     put 'a == 0'
check.   
```  

**repetition**

Repetition is a block of code that execute multiple times. It is using keywords: {cycle, repeat, exit}

```
var a:Z=10

cycle
  set a-=1
  
  ; conditional repetition
  repeat if (a % 2 == 0)
  
  out(a, ' ')
  
  ;conditional termination
  exit if (a < 0)
cycle.

write
```

**Notes:** 

* If _exit_ condition is missing the cycle is infinite;
* Nested cycle is not supported in Wee language;
* One cycle can be controled using variables;


**range**
Range is a series of integer numbers between two limits.

* [n..m] is inclusive range
* [n!!m] is exclusive range
* [n.!m] is exclude max limit
* [n!.m] is exclude min limit


```
var n := 0, m := 20

; using range to define i
for i :> [n..m] do
  is (a % 2 == 0) ?
    next ;force next iteration
  no  
    put (a, ' ')
  is.
  ;force early exit
  done if (a > 10)
for.    

write
```

## Pattern Matching

Instead of ternary operator we use conditional expressions. 
These expressions are separated by coma and enclosed in (...).

**Syntax:**

```
var <v>:<t>

; single matching with default value
set <v> := (<xp> | <cnd>, <dx>)

; multiple matching with default value
set <v> := (<xp1> | <cnd1>[, <xp2> | <cnd2>...], <dx>)

; alternative code alignment
set <v> := (
  <xp1> | <cnd1>,
  <xp2> | <cnd2>,
  <dx>)
```

**Legend:**
 
```
<v>    = predefined variable
<t>    = predefined type
<xp>   = expression of same type with <var>
<cnd>  = condition for <xp>
<dx>   = default expression (no condition).
```

**Example**

```
var  x   := 10
var  a,r := 0

cycle
  set r := x%2
  set a := (0 | r == 0, 1 | r > 0, 2)
  out (a, ',')
  set x-=1
  exit if (x < -1)
cycle.

write
```

## Declaring a function

* In Wee there is no keyword for function declaration.
* Function result type is declared using ":" and type name.
* Function can use input parameters.
* Function is terminated using function name and dot "."

**Syntax**
```
<name>(<param>:<type>,...):<result_type>
   [<statement>]
   ...   
   => <expression>
<name>.
```


**Example:** 

```
var z:Z

func(x,y:Z):Z
  set x += 1
  set y += 1 
  => x+y ;function result
func.
  
; call func and assign result to z  
set z := func(1,1) 
put(z); print 4 

;call function func using and print result
put(func(0,0)) ; print 2

write
```

**Note:** 
* Functions must have at least one resilt "=>"
* You can''t intrerupt a function execution.
* Next statements after "=>" are also executed.

## Declare a Method

A function that have no result is called a method. 

```
foo():
  put("hello, I am foo")
foo.  
  
foo; execute method
```

**Notes:**
* A method can not be used in expressions
* A method can have side-effects
* We cann be intrerupt using "halt". 

Usually a method is working for a specific type.

**example**
```
def Foo: { p1:N, p2:N, p3:S } 

;initialization method for Foo type
bar(x:Foo,p1,p2:Z,p3:S):
  ;precondition
  halt if (p1<0 or p2<0 or p3=='')
  
  ;modify Foo members
  set x.p1 := p1
  set x.p2 := p2
  set x.p3 := p3
bar.

;second method for Foo type
print(x:Foo):
  put('{p1={0},p2={1},p3={2}}' <+ (x.p1, x.p2, x.p3));
print.

; declare instance of Foo
var foo:Foo;

foo.bar(1,2,'Test'); initialize foo
foo.print; call second method for foo

write

```
**Note:** 
* Wee is using single dispatch to identify first parameter.
* Methods must be bublic otherwise can be used only in current module.

Read Next: [Composite Tyepes](composite.md)   