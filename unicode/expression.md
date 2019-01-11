## Unicode expressions

3RF = 3 Rows Formula

Advanced Wee compilers can support Unicode large formula expression.This is also known as 3 rows formula. It supports several notations that makes code very scientific and readable if the proper font is used on code editor. You must use font: Dejavu Sans Serif Mono for best rendering.

**Download:** [Dejavu Fonts](https://dejavu-fonts.github.io/)

** Details about 3RF **

On these formulas you can use spaces to align symbols from first row with symbols from second and third row. The left side operator is always on second row and third row can be missing sometimes. Sometimes 4 rows are required.

If the code is align with tabs or not aligned compiler will detect an error. Unalign formula is easy to spot by developers if the proper font is used. But if one developer try to use a different font than this method is unpractical.

3RF formulas are enclosed in large parenthesis or use a large symbol.
                
    ⎛ ⎞ ⎡ ⎤ ⎧ ⎫   
    ⎜ ⎟ ⎢ ⎥ ⎨ ⎬  
    ⎝ ⎠ ⎣ ⎦ ⎩ ⎭   
   
** Using power and subscript **

Most of the time formulas require subscript and superscript for power. We support what Unicode give us. You can use optional ^ or superscipt for power function.

Superscript numbers:
M⁽⁾ ⁺ ⁻ ⁼ · ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹
Aⁿ ʰ ˣ ʸ ʰ ʷ ʳ ʴ ˢ ʲ ʺ ʻ ʼ ™

Subscript numbers:
M . ‚ ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ ₋₊₌₍₎ ⌵ ⌄

Xₐ … ₑ ₕ ᵢ ⱼ ₖ ₗ ₘ ₙ ₒ ₚ ᵣ ₛ ₜ ᵤ ᵥ ₓ ₔ 

**Notes:**

* (b,c,d,y,z missing)
* The compiler will identify superscript and normal letters as equivalent.
* Power symbol "^" is mandatory when we use subscript variable.

```
let x₁, x₂, x₃ <: (1,2,3);

for n <: [1..3] do
  out x₂^ⁿ  
  out ','
for;

write -- 2,4,8,16,

```

**Create large formulas**

The best way to create a large formula is to copy an existing formula from this file and paste in your project then modify the content using spaces and lines or symbols. The let/set statement is in second row all the time no matter how large a formula become.  



##Sum symbol ( ∑ )

This symbol is on one row but it can start from 0..n or from arbitrary number. So we need 3 rows in total. 


**Example**
```
let X = [1,2,3,4,5]   
let n = 3 ∈ N         
        ⎛ ₙ    ⎞      
let y = ⎜ ∑(X) ⎟      
        ⎝ ⁰    ⎠           
put y --> 1+2+3 = 6     
```            

**Average example**
```  
let X = [1,2,3]  
let n = 3

        ⎛ ∑(X) ⎞
let a = ⎜ ———— ⎟
        ⎝  n   ⎠ 
```

## Using hooks and extension bars:
```
In Wee the matrix are stored in memory by row major order.
Default subscript (DS) start from [0,0] upper left corder to [n,m]

**Matrix*

```
-- Declare matrix literal using 3RF

        ⎡ 0, 0, 0 ⎤   
let M = ⎢ 0, 0, 0 ⎥   
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
        ⎡e₀₀, e₀₁, e₀₂⎤  
let M = ⎢e₁₀, e₁₁, e₁₂⎥
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
let x = √ ⎜———————⎟   
          ⎝ x²+y² ⎠   
```

** 3RF expression**

For complex expressions that require internal () we can use large squiggly brackets. It is not wrong to use large round parantheses 


```
        ⎧(x+1)²+(y+1²)⎫³
let z = ⎨—————————————⎬   
        ⎩    x²+y²    ⎭    
```

** 3RF integral**
```
         ⌠ⁿ         
let y =  ⎮(a+b+x)ₓ  
         ⌡₀          
```

** n-nary sum ∑ **

```
        ₘ   ⎛ 1 + x ⎞
set a = ∑   ⎜———————⎟   
        ˣ⁼ⁿ ⎝   x²  ⎠
```

** n-nary product ∏ **
 
```
        ₘ   ⎛ x ⎞
set a = ∏   ⎜———⎟   
        ˣ⁼ⁿ ⎝ x²⎠
```

## Not Supported

Not all kind of fantastic formulas can be supported.

**Example:** 
```         
            _____ 
           ╱ ∑(X)   
let r =  2╱  ————   
        ╲╱    n     
```

**Example:**

Wee can''t parse this formula.

```      _________________ 
let r = √(x₂-x₁)²+(y₂-y₁)²
```

Instead we can use:

```
let r = √((x₂-x₁)²+(y₂-y₁)²)
```