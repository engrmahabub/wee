# Wee Syntax

For syntax notation we use modified BNF convention:

* We use \<name\> to represent identifier names;
* We use  ...  to represent repetitive sequence;
* We use notes to mention optional things;

## Expressions
Expressions are created using identifiers, operators, functions and constant literals. 

* can be enumerated using comma separator ","
* can be combined to create more complex expressions;
* have type that is calculated using type inference;
* can be assigned to variables using "set" and ":=";
* can be printed to console using put and out methods;
* can use () to establish order of operations;

**Examples**
```
-- simple expressions in put statement
put 10    -- print 10
put 10,11 -- print 1011

write

--complex expressions are using ()  
put 10,11,12    
put 10 + 10 + 15 
put (10 > 5) & (2 < 3)

--multiple expressions in a line
put(1,',',2,',',3) --expect 1,2,3
put(10, 11, 12)    --expected 101112   

write
```

**Notes:** 
* put statement add new line automatically
* put statement can receive multiple parameters

## Data types

Digital data is based on binary numbers: {0, 1}.
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
1. access  (private or public or local)
1. storage (memory  or registry)

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

|   Literal | Description
|-----------|---------------------------------------------------------------------
|0          | integer zero
|1234567890 | integer number : (0,1,2,3,4,5,6,7,8,9)
|0b10101010 | binary integer : {0b,0,1}
|0xFF       | hexadecimal integer: (0x,0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F)
|0.5        | real number: (., 0 , 1 , 2 , 3 , 4 , 5 , 6 , 7 , 8 ,9)
|0.0        | real number: (.,0,1,2,3,4,5,6,7,8,9) 
|5E2        | real number: 5*10²  = 500  (E use positive exponent)
|5e2        | real number: 5*10⁻² = 0.05 (e use negative exponent)

**Operators** 

 op | purpose
----|--------------------------------------------------------------
 :  | declare type, function or code block or pair-up operator
 :> | declare type, subtype or composite type (class or pattern)
 := | establish value for a variable or constant using let or set

## Variable declarations

Variables are defined using let keyword and ":=" symbol.

```
let <var_name> := <constant>
let <var_name> := <constructor>
let <var_name> <: <composite_type>
let <var_name> ∈  <base_type> or <user_type>
```

Multiple variables can be define in one single line using comma separator:
```
let <var_name>,<var_name> ... := <constant>
let <var_name>,<var_name> ... := <constructor>
```

## Constant declaration

```
con <constant_name> := <constant>
con <constant_name> := <constructor>
```

**Notes**
* Keyword _var_ will create a declaration region. 
* Keyword _con_ can be used to define a constant
* Keyword _set_ will create an initialization region.

## Modify values

We can modify variables using _set_ statement.

```
let a := 10 -- declare integer variable 
let b ∈ Z   -- declare variable b=0

set b := a  -- modify b
put b       -- expected 10
```

**Statement _set_** 

* must use at least one modifier { :=, +=, *=, :~, ... }
* can modify multiple variables separated with comma
* can execute multiple expressions separated with comma

**Examples:**
```
-- define a constant that can't change it's value
con pi:= 3.14

-- establis a let region for multiple variables
let a   ∈ Z --Integer 
let x,y ∈ R --Double
let q,p ∈ L --Logic

--using modifier operators
set a := 10  -- modify value of a
set a += 1   -- increment value of a-
set a -= 1   -- decrement value of a 

-- modify two variables using one constant
set q, p := True  -- modify value of q
set x, y := 10.5  -- modify value of x and y

--modify several variables in a single line
set a := 11, q := False, x,y := 20.15
```

## Type declaration

User can define types using keyword _def_ and operator "<:".

```
def <type_name> <: <subtype constructor> 

--using new type
let <var_name>[,<var_name>] ... ∈ <type_name>
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
let a := 0, b := 20   
let v := 10.5, x:=0.0 

--unsafe conversion
set a:= v -> N
put a -- expect 10

--safe conversion
set x:= b
put b -- expect 20
```

## ASCII type

Wee define A = ASCII character as native type.

```
let a,b ∈ A --ASCII character
let x,y ∈ B --Binary number 

set a := '0'    -- representation of 0
set x := a -> B -- convert to 30
set y := 30     -- ASCII code for '0'
set b := y -> A -- convert to '0'
```
## Type checking

We can use variable type to verify expressions.

```
let a := 0   --integer variable
let b := 0.0 --real variable

set b := 10  --PASS: automatic safe conversion  
set a := 10.5--FAIL: a is of type: Integer
```

## Logic type

Logic type is an enumeration of two constants False and True.

```
def .L <: {.False, .True}
```
**Notes:** 
* Public members start with dot "." symbol.
* Enumeration have binary values so L is compatible with B

## Logic operations

For Logic type "L" Wee uses two numbers: {0, 1}    
Logical operators in order of precendence: {not, and, or}

 A     | B     | A & B | A \| B | !A    |  !B   | A ~ B
-------|-------|-------|--------|-------|-------|--------
 True  | True  | True  | True   | False | False | False
 True  | False | False | True   | False | True  | True
 False | True  | False | True   | True  | False | True
 False | False | False | False  | True  | True  | False
---------------------------------------------------------

## Operator precedence

!  has hugest precedence
~  has the lowest precedence

Precedence: { !, ∈, &, |, ~ }

## Logical expression

Logical expression have value { False or True }

```
-- simple expressions
let x:= False ∈ L
let y:= True  ∈ L

put(x)  -- will print: 0
put(y)  -- will print: 1

--complex expressions
put (x = y) -- equal: 0
put (x < y) -- lt   : 1
put (x > y) -- gt   : 1

--Unicode expressions
put (¬ x  ) -- not   0 is 1
put (x ∧ y) -- 0 or  1 is 0
put (x ∨ y) -- 0 and 1 is 1
put (x ⊕ y) -- 0 xor 1 is 1
```

## Bitwise operators

Bitwise operations are executed on entire binary value.


**Shifting Bits**
 
 A    | A ← 1 | A → 2 | .¬ A
------|-------|-------|-------
 0000 | 0000  | 0000  |1111
 1111 | 1110  | 0011  |0000
 0111 | 1110  | 0001  |1000
 0110 | 1100  | 0001  |1001


 A    | B   | A .∧ B | A .∨ B  | A .⊕ B
------|-----|--------|---------|--------
 00   | 00  | 00     | 00      |  11    
 01   | 00  | 00     | 01      |  10    
 11   | 01  | 01     | 11      |  00    
 10   | 11  | 10     | 11      |  01    

See also:[Bit Manipulation](https://en.wikipedia.org/wiki/Bit_manipulation)


## Unicode usage

Wee is using Unicode for identifier names.

* Names can use Greek alphabet and subscript;
* Superscript numbers can be used as Power (^);
* You have already encounter several Unicode operators;

**Using subscript**
```
let hdd₀,hdd₁,hdd₂,hdd₃,jdd₄ := ('A:','B:','C:','D:','E:')
```

**Example:**
```
+-----------------------------------+
|*             _________________   *| 
|* Distance = √(x₂-x₁)²+(y₂-y₁)²   *|
|*                                 *|
+-----------------------------------+

-- subscript notation for coordinates
let x₁,x₂:= 0
let y₁,y₂:= 10
let d ∈ R

-- use Unicode superscript for power
set d := sqr((x₂-x₁)²+(y₂-y₁)²)
```

**Unicode**: [symbols](symbols.md)

## Conditionals

A conditional is using "if" keyword to control one statement.   
Observe that "if" is not itself a full statement only an augment.

1. Conditional can apply to single line statements or method calls.   
1. Conditional can''t be used with declaration statements.
1. Conditional can''t be used with block statements.
1. Complex expression before conditionals must be enclosed in ()

```
<statement> if <expression>
```

The statement is executed only if the expression is True. 

```
let a ∈ Z

-- conditional execution
set a:= 1 if a = 0 

-- conditional output
put "a is 0" if (a = 0)
put "a >  0" if (a ≥ 0)
 
write 
```

**Notes:** Keyword "if" do not pair-up with "else".

## Control flow
Wee has 3 control flow statements { is, cycle, for }:

**decision**
A decision is based on logical expressions and keywords { is, no } and symbol "?". Logical expression must be enclosed in parenthesis () always.

```
let a:= 10 

-- single branch
is a = 10 ?
   put 'yes'
is;  

-- two branches
is a < 5 ?
  put 'yes'
no:
  put 'no'
is;

-- multiple branches
is a < 0    ?
  put 'yes'
no:is a > 5 ?
  put 'no'
no:is a = 0 ?  
  put "a = 0"  
no:is a = 5 ?  
  put "a = 5"    
no:
  put "a = #n" <+ a  
is;

```  

**Repetition**

Wee can execute a block of code multiple times.

Keywords used: {cycle, repeat, stop}

```
---------------------------
|*    Repetitive block   *|
---------------------------
let a := 10

cycle
  set a -= 1
  
  -- conditional repetition
  repeat if (a % 2 = 0)
  
  out (a, ' ')
  
  -- conditional termination
  stop if (a < 0)
cycle;

write
```

**Notes:** 

* If _stop_ condition is missing the cycle is infinite;
* Nested cycle is not supported in Wee language;
* One cycle can be controled using variables;

**Iteration**

Is used to iterate over one range of values.

Keywords used: {for, do, next,done}

A _range_ is a series of integer numbers between two limits.

* [n..m] is inclusive range
* [n,,m] is exclusive range
* [n.,m] exclude max limit
* [n,.m] exclude min limit

```
let n := 0, m := 20

-- using range to define i
for i ∈ [n..m] do
  is a % 2 = 0 ?
    next --force next iteration
  no:  
    out (a, ' ')
  is;
  --force early stop
  done if (a > 10)
for;    

write
```

## Pattern Matching

Instead of ternary operator we use conditional expressions. 
These expressions are separated by coma and enclosed in (...).

**Syntax:**

```
let <v> ∈ <Type>

-- single matching with default value
set <v> := (<xp> : <cnd>, <dx>)

-- multiple matching with default value
set <v> := (<xp1> : <cnd1>, <xp2> : <cnd2>..., <dx>)

-- alternative code alignment
set <v> := (
  <xp1> : <cnd1>,
  <xp2> : <cnd2>,
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
let  x   := 10
let  a,r := 0

cycle
  set r := x % 2
  set a := (0 : r = 0, 1 : r > 0, 2)
  out (a, ',')
  set x-= 1
  
  stop if (x < -1)
cycle;

write
```

## Declaring a function

* In Wee there is no keyword for function declaration.
* Function result type is declared using ":" and type name.
* Function can use input parameters.
* Function is terminated using function name and dot "."

**Syntax**
```
<name>(<param>:<type>,...) => <result> ∈ <type>:
   [<statement>]
   ...   
   <result> := <expression>
<name>.
```

**Example:** 

```
let z ∈ Z

func(x,y:Z) => z ∈ Z:
  x += 1
  y += 1 
  z := x+y --function result
func.
  
-- call func and assign result to z  
set z := func(1,1) 
put z -- print 4 

--call function func using and print result
put func( 0, 0 ) -- print 2

write
```

**Note:** 
* Functions must have at least one result "=>"
* You can''t interrupt a function execution.
* Arguments for function calls require ()

## Declare a Method

A function that have no result is called a method. 

```
foo():
  put "hello, I am foo"
foo.  

--execute method foo  
foo

end. 
```

**Notes:**
* Method with no parammeters require empty brackets ():
* Method call do not require brackets () when no parameters
* Method call do not need brackets for single argument
* Multiple arguments can be enumerated in a tuple (arg1,arg2...)
* A method can not be used in expression (have no result)
* A method can have side-effects and output parameters
* We can interrupt a method prematurely using "exit" 

Usually a method is bound to a the first parameter using single dispatch.
The first parameter can be called: "self","it","this" or "me". It''s name is not restricted like in Python or Java. We believe freedom is better then restriction.

**Constructor**

A special method is a constructor. This method has usually same name as the user type with lowercase, but can have other name defined by the user imagination. 

Constructor has an explicit declaration and result type is the user type it creates. We believe that explicit is better than implicit.

**example**
```
-- define Foo subtype of set {}
def Foo <: {p1 ∈ N, p2 ∈ N, p3 ∈ S} 

;constructor (same name as Foo)
;create a result of type Foo (me)
foo() => me ∈ Foo:
  me := {0,0,0}
foo.

;initialization method for Foo type
bar(me ∈ Foo, p1, p2 ∈ Z, p3 ∈ S):
  ;precondition
  exit 1 if (p1 < 0 ∨ p2 < 0 ∨ p3 = ∅)
  
  ;modify Foo members
  set me.p1 := p1
  set me.p2 := p2
  set me.p3 := p3
bar.

;second method for Foo type
print(me ∈ Foo):
  put "{p1={0},p2={1},p3={2}}" <+ (me.p1, me.p2, me.p3)
print;

-- declare instance of Foo
let foo₁ ∈ Foo := foo();

foo₁.bar(1,2,'Test')-- initialize foo
foo₁.print-- call second method for foo

write

end.
```
**Note:** 
* Wee is using single dispatch to identify first parameter;
* If the type is public, it''s constructor should be also public;
* Methods of a type can be private to module or public;
* Constructors and methods can be overloaded using multiple dispatch;
* Constructors and methods can be overwritten in other modules;

## Inheritance and Polymorphism

Can be done at module level. Wee do not have classes, it has only user defined types. However doing an explicit design you can create a type hierarchy similar to OOP. 

We can define a new type based on existing type using symbol "<:". This will inherit all methods of the original type, including the constructor.

We can create new methods and a new constructor. The new constructor can call the super constructor explicit. Nothing is implicit in Wee.

Using this technique, one module can extend user defined types in any other module, including the core library modules. So Wee is a modular language.


**Read Next:** [Composite Types](composite.md)   