# Composite Types

Composite types are complex data structure in memory. 
We can use composite types to declare variables, constants or other composite types.

## String composite type "S"

* S strings are _tries_ data structures (radix tree) having unlimited capacity;
* A can be used to create arrays of ASCII characters compatible with C strings; 

```
var s : S ; Unlimited capacity string
var a : [A](25) ; C like string of 25 characters

set  a := 'short string'
set  s := 'This is long ASCII string'   
```

## String conversion
Conversion of a string into number is done using _parse_ function:

```
var x,y: R

set  x := parse('123.5',2,",.")       ;convert to real 123.5
set  y := parse('10,000.3333',2,",.") ;convert to real 10000.33
```

## Control codes:

Wee support escape notation using escape `\` symbol.
For each escape character Wee also define a constant CODE.

** list of supported escape characters:**

DEC|HEX|CODE|ESCAPE|NAME
---|---|----|------|---------
0  |00 |NUL |\0    |Null
7  |07 |BEL |\a    |Bell
8  |08 |BS  |\b    |Backspace
9  |09 |HT  |\t    |Horizontal Tab
10 |0A |LF  |\n    |Line Feed
11 |0B |VT  |\v    |Vertical Tab
12 |0C |FF  |\f    |Form Feed
13 |0D |CR  |\r    |Carriage Return
27 |1B |ESC |\e    |Escape

**Note:** Escape characters are recognized in strings.

```
put('this represents \n new line in string')
```


## Unicode type

Default Unicode character set is UTF8. This has variable size: (1..4) Bytes.

```
var s := "This is a Unicode string"
put(type(s)); Print: U
```

**Note:** String literals '' and "" is an empty string.

See also: https://utf8everywhere.org/

## String concatenation

Strings can be concatenated using operator "+"

```
var u: U
var c: U

set u := "This is" + " a long string."
set c := "Unicode and " + 'ASCII'
```

## String format

We can include numbers into a string using template operator "<+" or "+>".
Inside template we use "{n}" notation to find a value using the member index.

**Template:**
```
set  <variable> := <template> <+ <variable>
set  <variable> := <template> <+ (<var1>,[<var2>,]...)
```

**Examples:**
```
set  x := 30 ; Code ASCII 0
set  y := 41 ; Code ASCII A

;template writing
put('{0} > {1}' <+ (x,y)) ;print "30 > 41"
  
```

## Enumeration

Enumeration is an abstract data set. It is a group of identifiers. Each identifier represents an integer value starting from 0 to n-1.
Enumeration values can start with a different number. First value is specified using assogm "=" operator.

```
def TypeName : { name1 = value ,name2 ... }

var a, b: TypeName

set  a := TypeName.name1
set  b := TypeName.name2

```

**Note:** When element name start with "." no need to use qualifiers for individual values

```
; using public elements in enumeration
def TypeName: { .name1, .name2 }

var a, b := 0

set  a := name1 ;a becomes 0
set  b := name2 ;b becomes 1

```

## Array Collection

Wee define Array variable using notation:[]().

```
var <array_name> : [member_type](n)   ;one dimension with capacity n
var <matrix_name>: [member_type](n,m) ;two dimensions with capacity n x m
```

Elements in array are indexed from 0 to n-1 where n is capacity.

**Example:**
```
var test: [R](10) ; define array with 10 Integer elements

put(test[0]) ; first element
put(test[?]) ; last element

; print all elements of array: 0,1,2,3,4,5,6,7,8,9,
for e :> test do
  put(e,',')
for.

write

; modify all elements of array
var m:N
set m:= length(test)  

for i :> [0.!m] do
  test[i] *= 2
for.
    
; print put the entire array
put(test); expect: [0,2,4,6,8,10,12,14,16,18]
```

**Notes:**
 
* Array of undefined capacity []() is Null. Capacity can be established later.
* Array with capacity is automatically initialized, elements of array are 0 or Null.

## Array Slicing

We can define a view for a section of array using [n..m] notation. This is called slice. 

**Syntax:**

```
; declare an arry with capacity (n)
var <array_name> : [<type>](n)

;we use := to create a slice from array
set <slice_name> := <array_name>[n..m]
```

**Notes:** 
* Slice is a view for a series of members in original array.
* Slice members are references to original array members not a copy.
* Last element is simbolized by "?"

```
var a:=[1,2,3,4]
var b,c,d:[Z]

set b:=a[1..?] ; [2,3,4]
set c:=a[0..2] ; [1,2,3]
```

## Matrix

It is an array with 2 or more indexes. We can have 2D or 3D array.

**Example:** 
```
var m:[R](4,4) ; define matrix

; initialize matrix using new ":="
set m := [[1,2,3,4],[5,6,7,8],[9,10,11,12],[13,14,15,16]]


put(m[0,0]) ; first element
put(m[3,3]) ; last element

```

**Note:** Elements are organized in _row-major_ order.

So next program will print: 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,

```
; elements in matrix can be accessed using single loop
for e :> m do
  out (e, ',')
for.

write
```

## Tuple Notation

Tuple is an immutable enumeration of constants, separated by coma and enclosed in round brackets (...).
Notice a tuple is not a variable data type, it is a constant embeded in the source code as literal.

**Syntax**
```
(<value1>, <value2>...<,value3>)
```

**Notes**: Tuple members can have different data types;

**Immutable**

Tuples are immutable. Once a tuple is initialized it can''t be modified.

```
; define a tuple using type inference
var v := (1,'a',2,'b') 

set(v[0]) :=  4 ;error you try to modify a tuple
put(v[0]) ;members of a tuple are not accesible using index
```

**Unit***

An empty tuple () represents an _"unit"_ 

```
var c:(); empty tuple is not initialized

set c:= (1,2,3); initialize empty tuple
set c:= (2,3,4); throw to garbage (1,2,3)

```

### Unpacking

Tuples can be assigned to multiple variables using unpacking:

**Example:**

```
;create 3 new variables using tuple notation
var x, y, z  := (97, 65, True)

;unpacking is using type inference
put(x) ;  97
put(y) ;  65
put(z) ;  1

;template unpacking into string
set s := "{0} > {1}, {2}" <+ (2,1,'True'); 
put(s) ; "2 > 1, True"
```


### Multiple results

A function can create as a results a tuple.

```
test(x,y:Z):(Z,Z) 
  => (x+1, y+1) 
test.

var n,m:Z

;unpacking the result
set n,m := test(1,2)

put(n) ;will print 2
put(m) ;will print 3

; ignoring the result
set _,_ := test(3,4)

```

### Partial unpacking
Tuple members can be ignored when unpacking using anonymous variable: "_"

```
var t := (0, 1, 2, 3, 4, 5)
var x,y,z:Z

; first element and last 2 are ignored
set _, z, y, z, _, _ := t

```

**Note:** When we unpack a tuple all members of the tuple must be unpack. If the number of variables is less or more then the touple member you will get a compilation error.

## Static Structure

Is an ordered enumeration of elements. Each element has a name and a type.
Structure members are enclosed in curly brackets {...}. 
This is the reason Wee is not a curly bracket language. We use the brackets for collections.

**Syntax:**
```
def <TypeName>: {<element>:<type> [,<element>:<type>]...}
var <name>:<TypeName>

;using qualifier with attributes
set <var_name.element> := <value>

;pair-up literal and values using ":"
set <var_name> := {
     <element> :<value>,
     <element> :<value>,
     ...}
```

**Nested structure:** can be created using similar to Json notation.

**Example:**
```
def Person: {
      name:S, age:W,  
      child: {name:S, age:W}
    }  

var r1,r2 : Person

set r1 := {name:'Barbu', age:25, {name:'Telu', age:4}};
set r2 := {name:'Mica',  age:21, {name:'Radu', age:1}};

```
## Structure _size_

Structure size is a constant that can be calculated using size(T).
For variable size elements Wee is using _implicit references_.

**Example:**
```
def Person: {name:U, age:N}
var catalog : [Person](10) ;array of 10 persons
  
;assign value by position using implicit constructor
set catalog[0] := Person("Cleopatra",15)
  
;assign value using literal
set catalog[1] := {name:"Martin", age:17}

;using one element with dot operators
put(caralog[0].name) ;will print Cleopatra
put(caralog[1].name) ;will print Martin

;member type is can be check using _type()_ built in
put(type(Person.name)) ; will print U
put(type(Person.age) ) ; will print W

;print size of structure
put(size(Person));
```

## Dynamic structures

These are data structures that can grow or shrink size during program execution.
Dynamic structures are implicit references. Default value is Empty collection.

**Syntax:**
```
var  <var_name> : [<type>]        ;list 
var  <var_name> : {<type>}        ;set
var  <var_name> : {<type>:<type>} ;map
```

**Example:**
```
; define a string
var  m,n : S  ;string 

set  m := 'This is '           
set  n := 'a very long string'

; define lists of strings
var  lst1,lst2,list : [S] 
  
set lst1 := split(m)
set lst2 := split(n)

set list := lst1 ++ lst2 ; concatenate two lists
put(list.join(n))        ; This is a very long string

write
```

## Dynamic set

A mathematical set is a collection of unique elements.

```
;define 3 collections
var s1 :{N} = {1,2,3} 
var s2 :{N} = {2,3,4}
var s  :{N} ;this is an empty set

; empty collection
put("set s is empty") if s == {}

; collection operations
set s := s1 & s2 ;{2,3}     ;intersection
set s := s1 + s2 ;{1,2,3,4} ;union
set s := s1 - s2 ;{1}       ;difference 1
set s := s2 - s1 ;{4}       ;difference 2

; append/remove operators
var a := {1,2,3}
set a += 4 ; {1,2,3,4}
set a -= 3 ; {1,2,4}
```

**Note:** Wee sets are internally sorted not indexed.   

## Dynamc List
A list is a collection of non unique elements.   

```
var l1 := [1,2,3]
var l2 := [2,3,4]

;concatenation "+" is different than for sets.
set l := l1 + l2 ;[1,2,3,2,3,4]

;intersection is similar to set
set l := l1 & l2 ;[2,3]

;difference is similar to set
set l := l1 - l2  ;[1]
set l := l2 - l1  ;[4]
```

Fist element in a list is [0] last is [?]

```
var ls := ['a','b','c']

;first and last
set first:=  ls[0] ; 'a'
set last :=  ls[?] ; 'c'
```

**Stack**

A stack is a LIFO sparsed collection of elements. We use "*" on right side.

```
var a:[N*] = [1,2,3]
var last:N

; using push operator "+="
set a += 4 ; [1,2,3,4]

; using pop operator "--"
set last :=   a[?] ; last = 4, a = [1,2,3,4]
set last := --a[?] ; last = 4, a = [1,2,3]

**Queue**

A queue is a FIFO sparsed collection of elements. We use "*" on left side.

```
var a:[*N] = [1,2,3]
var first:M

; using engueue operator "+="
set a += 4 ; [1,2,3,4]

; using dequeue operator "--"
set first :=   a[0] ; 1 and a = [1,2,3,4]
set first := --a[0] ; 1 and a = [2,3,4]
```

## Dynamic Map
A map is a hash collection of data indexed by a key.

```
var map :  {A:S}
set map := {'a':'first', 'b':'second'}

; create new element
set map['c'] := 'third'

put(map['a']) ;'first'
put(map['b']) ;'second'
put(map['c']) ;'third'

write
```

**Note:** Map operators work like for set


## Check for inclusion

We can check if an element is included in a collection.

```
var map := {'a':'first', 'b':'second'}

is ('a' in map) ?
  put("a is found")
no
  put("not found")
is.
  
write  
```

## Scalar operations

To avoid loops we introduce notation notation [*] for all elements.

```
var a:[1,2,3]

; modify all elements
set a[*] += 1 ; [2,3,4]
set a[*] -= 1 ; [1,2,3]

; multiply all elements
set a[*] *= 2 ; [2,4,6]
set a[*] /= 2 ; [1,2,3]
```

Scalar operators works also on slices.

```
var a:[0,1,2,3]

; modify first 2 elements
set a[0..1] += 1 ; [1,2,2,3]
set a[0..1] -= 1 ; [0,1,2,3]

; multiply last elements startinx from index 2
set a[2..?] *= 2 ; [0,1,4,6]
set a[2..?] /= 2 ; [0,1,2,3]
```

## Partial declaration

Declare empty collections are initialized later.

**Unbound literals:**
```
var a : []  ; define empty list
var b : {}  ; define empty set or map
var c : ()  ; define empty tuple
    
put(a == [])  ; 1 
put(b == {})  ; 1 
put(c == ())  ; 1 
  
set a := ['A','B','C'] ;Bound to List of A elements
set b := {'a','b','c'} ;Bound to Set of A elements
set c := ('a','b','c') ;Bound to Tuple of A elements 
```

More examples: [ct.wee](ex/ct.wee)

## Range Subtype

Range notation is used to define a range of values.

```
var a := 0
var b := 10
 
put [a..b] ;include both limits [0,1,2,3,4,5,6,7,8,9,10]
put [a!!b] ;exclude both limits [1,2,3,4,5,6,7,8,9]
put [a.!b] ;exclude upper linit [0,1,2,3,4,5,6,7,8,9]
put [a!.b] ;exclude lower linit [1,2,3,4,5,6,7,8,9,10]

write
```

**Examples:**

```
;sub-type declarations
def SmallRange    : B[0..9]
def NegativeRange : Z[-10..-1]
def AlfaChar      : A[a..Z]
def NumChar       : A[0..9]
def Positive      : Z[0!.]
def Negative      : Z[.!0]

;Check variable belong to sub-type
is ('x' in AlfaChar)? 
  put('yes')
no
  put('no')
is.
```

**Notes:**

* Anonymous range expression [n..m] is of Integer
* Range can apply only to discrete types (A,B,Z,N)
* Control variable can be declared in range using ":>"
* To check value in range use operator "in"

## Collection generators

Wee is using a special notation to create a sub-set.

```
var a,b: {Z}

set  a := { e | e :> [0.!10] }
set  b := { x | x :> [0!.10] }

put(a) ; {0,1,2,3,4,5,6,7,8,9}
put(b) ; {1,2,3,4,5,6,7,8,9,10}
```

## Copy collection

Assignment and slicing do not copy member collections.

```
var a:=[0,1,2,3,4]
var c,d:[Z]

; coppy the entire collection
set c:= [ x | x:> a ] ; now c == a

; coppy slice starting from a[2]
set d:= [ x | x:> a[2..?]] ; => [2,3,4]
```

## Collection filters

A filter is a logical expression after "if" keyword enclosed in paranthesis ().
In next example we convert a set into a list of elements.


```
var a:{N}
var n:[N]

set a := {0,1,2,3,4,5,6,7,8,9} 
set b := [ x | x :> a, (x % 2 == 0)]
  
put(b);will print [0,2,4,6,8]
```

## Expression mapping

A convenient way create sub-lists or sub-sets is to use an expression:

**Example:**
```
var test:   [R](10) = [0,1,2,3,4,5,6,7,8,9]
var result: [R](5)

result := [ x*2 | x :> test[0..4] ]
```

**Examples:** [ct.wee](ex/ct.wee)

## Variable arguments

One function or method can receive variable number of arguments into an array using prefix "*".

```
;parameter *bar must be an array 
foo(*bar:[Z]):Z
  var result:Z 
  for i :> bar do
      result +=bar[i]
  for.
  => result
foo.

;we can call foo with variable number of arguments
put(foo()     ); 0
put(foo(1)    ); 1
put(foo(1,2)  ); 3
put(foo(1,2,3)); 6

write
```

**Read next:** [Type Inference](inference.md) 