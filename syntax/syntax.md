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
* can be assigned to variables using "set" or "let" statements;
* can be printed to console using put and out methods;
* can use () to establish order of operations;

**Examples**
```
-- simple expressions in put statement
-- no need for parentheses for a single value
put 10    -- print 10
put "this is a test"

write

--complex expressions can use ()  
put (10 + 10 + 15)
put (10 > 5) ∧ (2 < 3)

--multiple expressions in a line
put (1,',',2,',',3) --expect 1,2,3
put (10, 11, 12)    --expected 101112   

write
```

**Notes:** 
* put statement add new line automatically
* put statement can receive multiple parameters
* multiple expressions are separated by comma
* we can omit the parentheses when one single value is used.

## Data types

Digital data is based on binary numbers: {0, 1}.
Using this basic values we represent all data types.

Wee use 3 kind of data types:

1. basic data types;
2. composite data types;
3. user defined types;

**Basic Types**

Data types have information about: 

1. name
1. representation
1. capacity
1. limits (min/max)
1. access  (private or public or local)
1. storage (memory  or registry)

Basic types are represented with one single uppercase ASCII character.

| Name        |Wee| Description
|-------------|---|-------------------------------------------------------------
| ASCII       |A  | ASCII character      
| Binary      |B  | Positive short number 
| Natural     |N  | Positive large number 
| Integer     |Z  | Positive or negative number 
| Logical     |L  | Logical number {0,1}
| Real        |R  | Real number 

**Composite types**

| Name        |Wee| Description
|-------------|---|-------------------------------------------------------------
| String      |S  | ASCII unlimited capacity
| Unicode     |U  | Unicode string
| Date        |D  | DD/MM/YYYY
| Time        |T  | hh:mm,ms

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

## Collection types

Wee define a collection using a special notation based on brackets.

| sym| Collection type
|----|-------------------------------------------------------------
| [] | Array \|  Matrix \| List
| {} | Hash Map \| Set \| Queue \| Stack
| () | Tuple \| Collection of expressions


## Variable declarations

Variables are defined using let keyword and 3 symbol:

 sym| purpose
----|--------------------------------------------------------------
 :  | pair-up operator, used to define members or argument values
 =  | create variable or collection of specific data type and value
 ∈  | declare variable same type as member of set or collection

```
let <var_name> = <constant>
let <var_name> = <constructor>
let <var_name> = <composite_type>
let <var_name> ∈ <set_or_type>
```

Multiple variables can be define in one single line using comma separator:
```
let <var_name>, <var_name> ... = <constant>
let <var_name>, <var_name> ... = <constructor>
```

## Constant declaration

```
con <constant_name> = <constant>
con <constant_name> = <constructor>
```

## Modify values

One can modify variables using _set_ statement.

```
let a = 10  -- declare integer variable 
let b ∈ Z   -- declare variable b=0

set b =: a  -- modify b
put b       -- expected 10
```

**Statement _set_** 

* must use at least one modifier { =:, +:, *:, ~:, ... }
* can modify multiple variables separated with comma
* can execute multiple expressions separated with comma
* can''t create a new variable, you must use let for it

**Examples:**
```
-- declare a constant that can't change it's value
con pi = 3.14

-- declare multiple variables using let
let a   ∈ Z --Integer 
let x,y ∈ R --Double
let q,p ∈ L --Logic

--using modifier operators
set a =: 10  -- modify value of a = 10
set a +: 1   -- increment value of a = 11
set a -: 1   -- decrement value of a = 10

-- modify two variables using one constant
set q, p =: True  -- modify value of q
set x, y =: 10.5  -- modify value of x and y

--modify several variables in a single line
set a =: 11, q =: False, x,y =: 20.15
```

## Type declaration

User can define types using keyword _def_ and operator "=".

```
def <type_name> = <subtype constructor> 

--using new type
let <var_name>[,<var_name>] ... ∈ <type_name>
```

## Type conversion

Numeric types are automatically converted when this is safe.

**Safe:**   Binary - > Integer -> Natural -> Real   
**Unsafe:** Real -> Natural -> Integer -> Binary

* Safe conversions are automatic.
* Unsafe conversion is done using operator "->"
* Operator "->" is also called "pipeline operator"

**example:**
```
let a = 0, b = 20   
let v = 10.5, x = 0.0 

--unsafe conversion
set a =: v -> N
put a -- expect 10

--safe conversion
set x =: b
put b -- expect 20
put x -- expect 20.0

--unsafe comparison
put x = b -- 0 False
put a ≈ b -- 1 True
```

**Note:** An Integer is not 100% equal to a Real

## ASCII type

Wee define A = ASCII character as native type.

```
let a,b ∈ A --ASCII character
let x,y ∈ B --Binary number 

set a =: '0'    -- representation of 0
set x =: a -> B -- convert to 30
set y =: 30     -- ASCII code for '0'
set b =: y -> A -- convert to '0'
```
## Type checking

We can use variable type to verify expressions.

```
let a = 0   --integer variable
let b = 0.0 --real variable

set b =: 10  --PASS: automatic safe conversion  
set a =: 10.5--FAIL: a is of type: Integer
```

## Logic type

Logic type is an enumeration of two constants False and True.

```
def .L = {.False, .True}
```

**Notes:** 
* Public members start with dot "." symbol.
* Enumeration have binary values so L is compatible with B

## Logic operations

For Logic type "L" Wee uses two numbers: {0, 1}    
Logical operators in order of precedence: {not, and, or}

## Operator precedence

¬  has hugest precedence
⊕  has the lowest precedence

Precedence: { ¬, ∈, ∧, ∨, ⊕ }

## Logical expression

Logical expression have value { False or True }

```
-- simple expressions
let x = False ∈ L
let y = True  ∈ L

put x  -- will print: 0
put y  -- will print: 1

--complex expression
put (x = y) -- equal: 0
put (x < y) -- lt   : 1
put (x > y) -- gt   : 1

--Unicode expressions
put (¬ x  ) -- not   0 is 1
put (x ∧ y) -- 0 or  1 is 0
put (x ∨ y) -- 0 and 1 is 1
put (x ⊕ y) -- 0 xor 1 is 1
```

## Unicode usage

Wee is using Unicode for identifier names and operators.

* Names can use Greek alphabet and subscript;
* Superscript numbers can be used as Power (^);
* You have already encounter several Unicode operators;

**Using subscript**
```
let hdd₀,hdd₁,hdd₂,hdd₃,jdd₄ = ('A:','B:','C:','D:','E:')
```

**Example:**
```
+------------------------------------
|              _________________    | 
|  Distance = √(x₂-x₁)²+(y₂-y₁)²    |
|                                   |
------------------------------------+

-- subscript notation for coordinates
let x₁,x₂ = 0
let y₁,y₂ = 10
let d ∈ R

-- use normal notation for power and sqr function
set d =: sqr((x₂-x₁)^2+(y₂-y₁)^2)

-- use Unicode superscript for power and sqr function
set d =: √((x₂-x₁)²+(y₂-y₁)²)

```

**See also:**

* [Unicode:symbols.md](../unicode/symbols.md)
* [Unicode:comments.md](../unicode/comments.md)

## Control Flow

Wee has 4 control flow statements { when, check, for, cycle }:

**when**

```
when <logical expression>:
  <true branch>
when <logical expression>:
  <alternate branch>
...  
else
  <false branch>
when;
```

**check**

```
check <expression> | <constant>
   is <value>:
      <statement>
      ... 
   in (<v1>,<v2>,...<vn>):      
      <statement>
      ...
other
   <default_statement>
check;      

```

**for**

```
for <var> <: <range|collection> do
  ...
  next -- force next iteration 
  ...
  done --force early stop
  ...
for;    
```

**cycle**

```
cycle
  <statement block>
  ...
  repeat if <continue condition>
  ...
  
  stop if <stop condition>
  ...
cycle;
```

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
set a =: 1 if a = 0

-- conditional output
put "a is 0" if a = 0
put "a >  0" if a ≥ 0
 
write 
```

**Notes:** Keyword "if" do not pair-up with "else".

It is time to see some more complex examples and learn more about control flow.

**Examples:** [control](control.md)

## Pattern Matching

Instead of ternary operator we use conditional expressions. 
These expressions are separated by coma and enclosed in (, , ,).

**Syntax:**

```
let <v> ∈ <Type>

-- single matching with default value
set <v> =: (<xp> if <cnd>, <dx>)

-- multiple matching with default value
set <v> =: (<xp1> if <cnd1>, <xp2> if <cnd2>..., <dx>)

-- alternative code alignment
set <v> =: (
  <xp1> if <cnd1>,
  <xp2> if <cnd2>,
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
let  x   = 10
let  a,r = 0

cycle
  set r =: x % 2
  set a =: (0 if r = 0, 1 if r > 0, 2)
  out (a, ',')  
  set x -: 1  
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
   <result> = <expression>
<name>.
```

**Example:** 

```
let z ∈ Z

func(x,y ∈ Z) => z ∈ Z:
  x +: 1
  y +: 1 
  z = x+y --function result
func.


-- call func and assign result to z  
set z =: func(1,1) 
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
* Method with no parameters require empty brackets ():
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
def Foo = {p₁ ∈ N, p₂ ∈ N, p₃ ∈ S} 

-- constructor (same name as Foo)
-- create a result of type Foo (me)
foo() => me ∈ Foo:
  set me =: {0,0,0}
foo.

-- initialization method for Foo type
bar(me ∈ Foo, p1, p2 ∈ Z, p3 ∈ S):
  ;precondition
  exit 1 if (p1 < 0 ∨ p2 < 0 ∨ p3 = ∅)
  
  ;modify Foo members
  set me.p₁ =: p1
  set me.p₂ =: p2
  set me.p₃ =: p3
bar.

-- second method for Foo type
print(me ∈ Foo):
  put "{p1={0},p2={1},p3={2}}" <+ (me.p₁, me.p₂, me.p₃)
print;

-- declare instance of Foo
let foo₁ ∈ Foo = foo();

foo₁.bar(1,2,'Test') -- initialize foo
foo₁.print -- call second method for foo

write

end.
```
**Note:** 
* Wee is using single dispatch to identify first parameter;
* If the type is public, it''s constructor should be also public;
* Methods of a type can be private to module or public;
* Constructors and methods can be overloaded using multiple dispatch;
* Constructors and methods can be overwritten in other modules;

## Using Modules

Wee do not have classes. However doing an explicit design you can create a type hierarchy 
similar to OOP using module encapsulation, user defined types and methods. 

Users can define new types based on existing types using symbol "=". This will inherit all methods 
of the original type, including the constructor.

After this you can create new methods and a new constructor in your module. The new constructor can 
call the super constructor explicit. Nothing is implicit in Wee.

Using this technique, one module can extend user defined types in any other module, including the 
core library modules. So Wee is a modular language.


**Read Next:** [Composite Types](composite.md)   