## ASCII comments

In We comments are number one concern. We enable several notations that enable ASCII comments. These are standard comments created for a single line or multiple lines of code.

**Single line**

For single line comments we use two symbols: 

{ "--", "==", "**", "##" } 

All these are comments for following reasons.

In Wiki "##" represents title 2. I''m using Wiki notation to write Wee documentation.
A Wiki page can be open and looks good in Wee syntax color works using Notepad++

In Wiki "**" is for making titles bold. It is convenient to use this notation so that syntax color works for bold text. Now these are all advantages. So in Wee there is posibility to create following single line comments.

```
************************
========================
------------------------
########################
```
**Multi-line comments**

For multi-line comments we have 3 possible comments.

```
1. Vertical bar comment:      |* .... *|
2. (+/-) comment  block:      +- .....-+
```

This enable perfect ASCII comments using following two notations:

```
+-----------------------
|                      |
|                      |
-----------------------+

------------------------
|*                    *|
|*                    *|
------------------------
```

3. A possible comment is free double quoted string. This is a rogue string that is not in a statement. Compiler will detect this string and will consider it comment. It can be used anyware. At the beginning of a row, in the middle of an expression or at the end of statement.
```
" This is a comment on a single line"
"  
   This is just a comment
   On multiple lines 
"

let x = 4 "This is a simple comment"
```


## Unicode comments


In Wee there are Unicode symbols used for trivial operations. However, Unicode symbols 
can be also used to make graphic formulas and simple drawings embedded into comments. 

This can makes source code very readable and efficient in size. A 3 row formula can support 
several notations that makes comments readable if the proper font is used in code editor. 

This file is not accurate on your web browser. For better visualization, 
you must use font: Dejavu Sans Serif Mono on your text editor.

**Download:** [Dejavu Fonts](https://dejavu-fonts.github.io/)


**Note:** This is an experimental notation.


## 3RF = 3 Rows Formula

On these formulas you can use spaces to align symbols from first row with symbols from second and third row. The left side operator is always on second row and third row can be missing sometimes. Sometimes 4 rows are required.

If the code is align with tabs or not aligned compiler will detect an error. Unalign formula is easy to spot by developers if the proper font is used. But if one developer try to use a different font than this method is unpractical.

3RF formulas are enclosed in large parenthesis or use a large symbol.

```
------------------------------
|* Three kind are available *|
------------------------------

"
 ⎛ ⎞ ⎡ ⎤ ⎧ ⎫   
 ⎜ ⎟ ⎢ ⎥ ⎨ ⎬  
 ⎝ ⎠ ⎣ ⎦ ⎩ ⎭   
"

```
   
**Using power and subscript**

Most of the time large formulas require subscript and superscript for power. 

**Superscript numbers:**
```
M⁽⁾ ⁺ ⁻ ⁼ · ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹
Aⁿ ʰ ˣ ʸ ʰ ʷ ʳ ʴ ˢ ʲ ʺ ʻ ʼ ™
```
**Subscript numbers:**

```
M . ‚ ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ ₋₊₌₍₎ 
Xₐ … ₑ ₕ ᵢ ⱼ ₖ ₗ ₘ ₙ ₒ ₚ ᵣ ₛ ₜ ᵤ ᵥ ₓ ₔ ⌵ ⌄
```

**Notes:**

* b,c,d,y,z are missing
* The compiler will identify superscript and normal letters as equivalent.
* Power symbol "^" is mandatory when we use subscript variable.

**Power example**
```
let x₁, x₂, x₃ <: (1,2,3);

for n <: [1..3] do
  out x₂^ⁿ  
  out ','
for;

write -- 2,4,8,16,

```

**Create large formulas**

The best way to create a large formula is to copy an existing formula from this file and 
paste in your project. Then modify the content using spaces and lines or symbols. 

Formulas can be included in comments or rogue text. This is a text enclosed in "" that can span 
on multiple rows. Rogue text is also interpreted as a comment by the compiler.


##Sum symbol ( ∑ )

This symbol is on one row but it can start from 0..n or from arbitrary number. So we need 3 rows in text. 


**Example**
```
"
    ⎛ ₙ   ⎞      
y = ⎜ ∑ X ⎟      
    ⎝ ⁰   ⎠          
"
```            

**Average example**
```  
"
    ⎛ ∑(X) ⎞
a = ⎜ ———— ⎟
    ⎝  n   ⎠ 
"
```

## Using hooks and extension bars:

**3RF Fractions**

* Fractions must always be enclosed in large parenthesis.
* Fractions are represented using: —

In next example we use √ to extract square root.

Other symbols: ∛ ∜

``` 
"   
      ⎛ 1 + x ⎞
x = √ ⎜———————⎟   
      ⎝ x²+y² ⎠   
"      
```

**3RF expression**

For complex expressions that require internal () we can use large squiggly brackets. It is not wrong to use large round parantheses 


```
"
    ⎧(x+1)²+(y+1²)⎫³
z = ⎨—————————————⎬   
    ⎩    x²+y²    ⎭    
"    
```

**3RF integral**
```
"
     ⌠ⁿ         
y =  ⎮(a+b+x)ₓ  
     ⌡₀          
"     
```

**n-nary sum ∑**

```
"
    ₘ  ⎛ 1 + x ⎞
a = ∑  ⎜———————⎟   
   ˣ⁼ⁿ ⎝   x²  ⎠
"   
```

**n-nary product ∏**
 
```
"
     ₘ   ⎛  x  ⎞
a =  ∏   ⎜ ——— ⎟   
    ˣ⁼ⁿ  ⎝  x² ⎠
"    
```

**Matrix*

In Wee the matrix are stored in memory by row major order.
Default subscript (DS) start from [0,0] upper left corder to [n,m]


**Larger matrix (DAS):**

Large matrix will start like a normal matrix and will expand: left & bottom.

```
"
M = ⎡e₀₀, e₀₁, e₀₂⎤  
    ⎢e₁₀, e₁₁, e₁₂⎥
    ⎢e₂₀, e₂₁, e₂₂⎥
    ⎣e₃₀, e₃₁, e₃₂⎦
"    
```
