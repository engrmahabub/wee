## Unicode comments


In Wee there are Unicode symbols used for trivial operations. However, Unicode symbols 
can be also used to make graphic formula and simple drawings embedded into comments. 

This can makes source code very readable and efficient in size. A 3 row formula can support 
several notations that makes comments readable if the proper font is used in code editor. 

This file is not accurate on your web browser. For better visualization, 
you must use font: Dejavu Sans Serif Mono on your text editor.

**Download:** [Dejavu Fonts](https://dejavu-fonts.github.io/)


**Note:** This is an experimental notation that can be used in Unicode strings and comments.


** 3RF = 3 Rows Formula**

On these formulas you can use spaces to align symbols from first row with symbols from second and third row. The left side operator is always on second row and third row can be missing sometimes. Sometimes 4 rows are required.

If the code is align with tabs or not aligned compiler will detect an error. Unalign formula is easy to spot by developers if the proper font is used. But if one developer try to use a different font than this method is unpractical.

3RF formulas are enclosed in large parenthesis or use a large symbol.

```
+----------------------------+
|* Three kind are available *|
+----------------------------+

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
let X = [1,2,3,4,5]   
let n = 3 ∈ N
"
    ⎛ ₙ   ⎞      
y = ⎜ ∑ X ⎟      
    ⎝ ⁰   ⎠          
"
let y = 0
for e <: X[0..n] do
   set y +: e
for;
                   
put y --> 1+2+3 = 6
write     
```            

**Average example**
```  
let X = [1,2,3]  
let n = 3

"
    ⎛ ∑(X) ⎞
a = ⎜ ———— ⎟
    ⎝  n   ⎠ 
"
let a = 0
for e <: X do
    a +: e
for;        

put a
write

```

## Using hooks and extension bars:

**Matrix*

In Wee the matrix are stored in memory by row major order.
Default subscript (DS) start from [0,0] upper left corder to [n,m]


```
-- Declare matrix literal using 3RF

let M = ⎡ 0, 0, 0 ⎤   
        ⎢ 0, 0, 0 ⎥   
        ⎣ 0, 0, 0 ⎦   

-- Initialize all elements
set M[*] =: 1

-- Modify diagonal elements
set M[0,0] =:1
set M[2,2] =:3

-- Modify second row
set M[1,*] =:2        
put M 
write
```

**Expected output:**

```

⎡ 1, 0, 0 ⎤
⎢ 2, 2, 2 ⎥
⎣ 0, 0, 3 ⎦

```

**Larger matrix (DAS):**

Large matrix will start like a normal matrix and will expand: left & bottom.

```

M = ⎡e₀₀, e₀₁, e₀₂⎤  
    ⎢e₁₀, e₁₁, e₁₂⎥
    ⎢e₂₀, e₂₁, e₂₂⎥
    ⎣e₃₀, e₃₁, e₃₂⎦
    
```

** 3RF Fractions **

* Fractions must always be enclosed in large parenthesis.
* Fractions are represented using: —

In next example we use √ to extract square root.

Other symbols: ∛ ∜

```    
      ⎛ 1 + x ⎞
x = √ ⎜———————⎟   
      ⎝ x²+y² ⎠   
```

** 3RF expression**

For complex expressions that require internal () we can use large squiggly brackets. It is not wrong to use large round parantheses 


```
    ⎧(x+1)²+(y+1²)⎫³
z = ⎨—————————————⎬   
    ⎩    x²+y²    ⎭    
```

** 3RF integral**
```
     ⌠ⁿ         
y =  ⎮(a+b+x)ₓ  
     ⌡₀          
```

** n-nary sum ∑ **

```
    ₘ  ⎛ 1 + x ⎞
a = ∑  ⎜———————⎟   
   ˣ⁼ⁿ ⎝   x²  ⎠
```

** n-nary product ∏ **
 
```
     ₘ   ⎛  x  ⎞
a =  ∏   ⎜ ——— ⎟   
    ˣ⁼ⁿ  ⎝  x² ⎠
```