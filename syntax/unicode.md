## Unicode

Unicode string is a set of _code points_ using symbols from universal character set (UCS). There are many encoding techniques available. Java uses UTF-32. We will probably use UTF-8 to be more efficient.

*Example:*
```
   us: "I can write Greek: \"αβγδ\".";
   print(us);
```
> I can write Greek: "αβγδ".

To edit source code containing Unicode literals one must use a specific font and UTF-8 source files. The preferred font for Level programming is "DejaVu Sans Mono". 

**See also:** [wikipedia ucs](https://en.wikipedia.org/wiki/Universal_Coded_Character_Set), 
[unicode characters](https://en.wikipedia.org/wiki/List_of_Unicode_characters#Character_reference_overview)

**Greek Alphabet**

ΑΒΓΔΕΖΗΘΙΚΛΜΝΞΟΠΡΣΤΥΦΧΨΩ
αβεδζη θικλμνξοπρσςτυφ

## Implementation
For now we do not have details of Unicode implementation. 
What we know is that will be an iterable collection not a array  of elements. 
Unicode strings are very different than the ASCII Strings used in Level-RC.

## Editor Font
Best fonts for unicode symbols: 

* [DejaVu Sans Mono](https://dejavu-fonts.github.io/)
* [GNU Unifont](http://unifoundry.com/unifont/index.html)

Alternative fonts I have try:
* Lucida Sans Unicode.
* Fixedsys Excelsior.
* Everson Mono.
* GNU Freefont
* Ubuntu Unifont
* Google Roboto Mono

https://en.wikipedia.org/wiki/Lucida_Sans_Unicode
http://www.fixedsysexcelsior.com/
http://evertype.com/emono/
http://www.gnu.org/software/freefont/
http://www.unifoundry.com/unifont.html

## Some examples

Alternative notation for numeric types:
ℤ ℕ ℂ ℙ ℚ ℍ ℝ  

Several Greek letters for variable names:
α β γ δ η ∂ λ μ ξ δ β Ω θ ε π φ ψ ω

π = 180°

** Imaginary number 

ⅈ = √(-1)

(λ expression)

Superscript numbers:
M⁽⁾ ⁺ ⁻ ⁼ · ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹ 
A ⁿ ʰ ˣ ʸ ʰ ʷ ʳ ʴ ˢ ʲ ʺ ʻ ʼ 

Subscript numbers:
M . ‚ ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ 
X ₋₊₌₍₎‹›

Subscript letters: (b,c,d,y,z missing)
Xₐ…ₑₕᵢⱼₖₗₘₙₒₚᵣₛₜᵤᵥₓₔ

**Trivial fractions**
% ½ ¼ ¾ ⅛ ⅜ ⅝ ⅞ 

**Fraction sign**

¹⁄₂ ²⁄₂ ³⁄₂ ⁴⁄₂ ⁵⁄₂ ⁶⁄₂ ⁷⁄₂ ⁸⁄₂ ⁹⁄₂ 
¹⁄₂ ¹⁄₃ ¹⁄₄ ¹⁄₅ ¹⁄₆ ¹⁄₇ ¹⁄₈ ¹⁄₉ ¹/₁₀

examples: 
A = (¹⁄₂,¹⁄₄,¹⁄₈)
B = [¹⁄₂,¹⁄₄,¹⁄₈]
C = {¹⁄₂,¹⁄₄,¹⁄₈}

**Power:**
X⁻¹·⁵, X²+6*A

**Restriction
A variable that is using indice can''t also use power. 
We must use carror "^" operator. x₁^2 for this case.

Table createion/printing:
├ ┤ ┬ ┴ ┼ ═ ║ ╒ ╓ ╔ ╕ ╖ ╗ ╘ ╙ ╚ ╛ ╠ ╬ ╧ 

Chess game:
♔ ♕ ♖ ♗ ♘ ♙ ♚ ♛ ♜ ♝ ♞ ♟   

Star shapes:
✡✢✣✤✥✦✬✭✮✯✱✲✳✴✵✶✷✸✹✺✻✼✽✾✿❀❂❃❄❅❆❇❈❉   

### Dice Symbols
⚀ ⚁ ⚂ ⚃ ⚄ ⚅

### Bulet Points
➀ ➁ ➂ ➃ ➄ ➅ ➆ ➇ ➈ ➉

**Misc.**
 
Δ ▽ Ψ⌁ ϵ ϶ ⍙ ⍫ ◇ ⨯ ∀Ɐ ⎊ ⍜ ⍉ ⌘ ‼ ¿ ǂ ʊ Ұ θ ≡

## Unicode Operators

Using  "DejaVu Sans Mono" font we can define new operators and symbols. 
These symbols however can be used only in strings. We do not use Unicode operators in the language. 
This may be a nice feature to have but unfortunately not very practical.

## Other Resources

Brackets ⟨⟩❬❭❰❱❲❳❴❵

Unicode Math Symbols ∑ ∫ π ∞

-----------------------------------------------------------------

Complete list of math symbols in Unicode 11 grouped by purpose.

Commonly used greek letters 
α β γ δ ε ζ η θ ι κ λ μ ν ξ ο π ρ ς τ υ φ χ ψ ω

superscript 
A ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹ ⁺ ⁻ ⁼ ⁽ ⁾ ⁿ ⁱ

subscript 
A ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ ₊ ₋ ₌ ₍ ₎ 
ₐ ₑ ₕ ᵢ ⱼ ₖ ₗ ₘ ₙ ₒ ₚ ᵣ ₛ ₜ ᵤ ᵥ ₓ ₔ

Roots √ ∛ ∜

**Numbers:**

* ℕ. = Natural Numbers   
* ℤ. = Integers          
* ℚ. = Rational Numbers  
* ℝ. = Real Numbers      
* ℂ. = Complex Numbers  

Infinity ∞

multiplication, division × ✕ ✖ ÷

circled {plus, times, …} ⊕ ⊖ ⊗ ⊘ ⊙ ⊚ ⊛ ⊜ ⊝

squared {plus, minus, times, …} ⊞ ⊟ ⊠ ⊡

other operators
 
− ∕ ∗ 
∘ 2217 Ring Operator
∙ 2219 Bulet Operator
⋅      Middle dot 
⋆      Star operator

… u-2026 (Alt+0133) Horizontal elipsis

⇒ ‼ ⁇ «»

**Set symbols**

∅ ∖ ⊂ ⊃ ⊄ ⊅ ⊆ ⊇ ⊈ ⊉ ⊊ ⊋ ⋐ ⋑

empty set ∅

element of ∈ ∋ ∉ ∌

binary relation of sets. {subset, superset, …} 
⊂ ⊃ ⊆ ⊇ ⊈ ⊉ ⊊ ⊋ ⊄ ⊅ 

Union ∪ 
Intersection ∩

**Order**

Precede and succeed ≺ ≻ ≼ ≽ ≾ ≿ ⊀ ⊁ ⋞ ⋟ ⋠ ⋡ ⋨ ⋩ 
less and greater < > ≮ ≯ ≤ ≥ ≰ ≱ ≦ ≧ ≨ ≩
less and greater 2 ⋜ ⋝ ≶ ≷ ≸ ≹ ⋚ ⋛ 

less and greater with equivalence ≲ ≳ ⋦ ⋧ ≴ ≵
less and greater misc ≪ ≫ ⋘ ⋙ ≬

**Equality, Identity, Equivalence, Approx, Congruence**

equality ≝ ≞ ≟ ≠ ∹ ≎ ≏ ⪮ ≐ ≑ ≒ ≓ ≔ ≕ ≖ ≗ ≘ ≙ ≚ ≛ ≜
Identity ≡ ≢ 
Equivalence ≍ ≭ ≣ 
Approx/almost/asymptotic equality ≁ ≂ ≃ ≄ ⋍ ≅ ≆ ≇ ≈ ≉ ≊ ≋ ≌ ⩯ ⩰
Misc equality ∻
Misc relations ⊏ ⊐ ⊑ ⊒ ⋢ ⋣ ⋤ ⋥

**Logic**

Logic ¬ ⊨ ⊭ ∀ ∁ ∃ ∄ ∴ ∵ ⊦ ⊬ ⊧ ⊩ ⊮ ⊫ ⊯ ⊪ ⊰ ⊱
Logic binary ∧ ∨ 

**Geometry**

Ratio, proportion ∝ ∶ ∷ ∺
Parallel, perpendicular ∥ ∦ 
Angles ∠ ∡ ∟ ⊾ ⊿

**Operators**

Integrals ∫ ∬ ∭ ∮ ∯ ∰ ∱ ∲ ∳

Derivative ∂ ′ ″ ‴ ∆

**Vector** 

⨯ ∇

Tilde Operators ∼ ∽

n-nary sum ∑ 
n-nary product ∏

**Qotation brackets**

« » ‹ ›

**Misc indicators**
 ± ∓ 

**Misc symbols**

Tacks ⊣ ⊢ ⊥ ⊤ 


** Advanced formula.**

Using hooks and extension bar:
```
    ⎡1 1 1⎤   
A = ⎢—,—,—⎥   
    ⎣2 4 8⎦   
```
Function call with formula:
```    
     ⎛  1+x  ⎞   
x = √⎜———————⎟   
     ⎝ x²+y³ ⎠   
```
Power expression:
```
    ⎧  1+x  ⎫²   
x = ⎨———————⎬   
    ⎩ x²+y³ ⎭    
```
Large integrale:
```
    ⌠ⁿ         
y = ⎮(a+b+x)ₓ  
    ⌡₀          
```
```
    ₙ
y = ∑(x)
    ¹
```    
```    
    ∑(X)
a = ————
     n    
```
**Matrix*
```
    ⎡e₁₁,e₂₁⎤   
A = ⎢e₁₂,e₂₂⎥   
    ⎣e₁₃,e₂₃⎦   
```
**Superscript**
A ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹ ⁺ ⁻ ⁼ ⁽ ⁾ 
A ⁿ ⁱ

**Subscript**
A ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ ₊ ₋ ₌ ₍ ₎ 
A ₐ ₑ ₕ ᵢ ⱼ ₖ ₗ ₘ ₙ ₒ ₚ ᵣ ₛ ₜ ᵤ ᵥ ₓ ₔ

**Misc**
Line, oveline, solidus, (large solidus is missing)

```
___
\
/
‾‾‾
```
Note: We can''t do large sum using DejaVu even though exist in unicode.

Arrows:
 ⇤ ⇥ ↼ ⇀ 

*Logic*
∧ ∨ & | ! ∀  

‡ ⍜ ⍛ ⍶ ⍙ ⍚ ¦ Ɐ ♇ ◻ ◯ ◬ ⍭ ⌽ ↹ ↯ ⁉ ⁈ ⁇ ‼ ‡ † ւ ǂ ǁ ǀ ÷ ¿ ⸮ ? ¬ 

 
**Missing**
Some subscript/superscript characters are missing.
I found this proposal: http://unicode.org/L2/L2011/11208-n4068.pdf

* Imaginary number ⅈ, ⅉ
* Euler''s number, base of natural log ℯ, ⅇ (Missing)

**Combining symbols**
xor is not represented correctly
Combining symbols does not help.

**Alternative Historical Research**
There was once upon a time a language called APL.

https://en.wikipedia.org/wiki/APL_(programming_language)

**Bit Manipulation**

https://en.wikipedia.org/wiki/Bit_manipulation