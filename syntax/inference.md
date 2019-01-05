# Type inference

Type inference is a logical deduction of type from constant literals.

## Default type
Each literal has a "default" type that is automatic assigned for specific notation.

## Type Bound

Operator ":=" can be used to define variables using type inference.   
**Note** . It is a definition. You can''t use simple "=" for type inference!

**Defaults:**
```
;character expressions
var c := 'a'      ; type = A
var a := 'String' ; type = S
var b := "Unicode"; type = U

; numeric expressions
var i :=  0       ; type = Z
var j :=  0.5     ; type = R

; multiple variables
var x,y,z := 5   ; type = Z

; combination of types
var n := 0, m := 0.5 ; types Z and R
```

## Composite inference

Composite structures are using () [] and {} to create different types:

```
;create one tuple
var t := (1,2,'a','b') 

;create a data structure
var b := {name:'Goliat', age:'30'}

;create a hash map
var c := {1:'storage',2:'string'}

;create a list with unlimited capacity
var d := [1,2,3,4]

;create an array with capacity of 10
var e := [1,2,3,4](10)
```

**Unpacking**

Wee can use a tuple to define values to several variables using ":=" operator.

```
var n,a,b := (1,'A','B')

put(type(n)) ;Z
put(type(a)) ;A
put(type(b)) ;A  
```

## Inference for Parameters
When we define parameters we can use type inference for: 

**Optional Parameters:**
```
f(a, b := 0):Z => (a+b) f.

put(f()   ); 0
put(f(1)  ); 1
put(f(1,2)); 3
```

**Multiple parameters:**

Parameters: a, b are mandatory, c is optional.

```
f(a,b:Z, c := 0 ):Z => (a+b+c) f.

put(f(1,2)  ) ; 3
put(f(1,2,3)) ; 6
put(f(1)    ) ; Error: Expected 2 arguments, 1 is given!
```

**Pass arguments by name:**

We can use parameter name and "=" symbol for argument value:

```
;f has optional parameters a, b, c
f(a,b,c:= 0 ):Z => (a+b+c) f.

put(f(a = 1))   ; b,c are 0
put(f(b = 1))   ; a,b are 0
put(f(c = 1))   ; a,b are 0
```

Read next: [Wee Structure](structure.md)