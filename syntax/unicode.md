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

(λ expression)


**Trivial fractions**
% ½ ¼ ¾ ⅛ ⅜ ⅝ ⅞ 

**Composite Fractions**

Fraction sign: ⁄

¹⁄₂ ²⁄₂ ³⁄₂ ⁴⁄₂ ⁵⁄₂ ⁶⁄₂ ⁷⁄₂ ⁸⁄₂ ⁹⁄₂ 
¹⁄₂ ¹⁄₃ ²⁄₃ ³⁄₃ ⁴⁄₃ ⁵⁄₃ ⁶⁄₃ ⁷⁄₃ ⁸⁄₃ ⁹⁄₃ 
¹⁄₂ ¹⁄₃ ¹⁄₄ ¹⁄₅ ¹⁄₆ ¹⁄₇ ¹⁄₈ ¹⁄₉

ⁿ⁄₂ 

**Power:**
X⁻¹·⁵ 

Superscript numbers:
M⁽⁾ ⁺ ⁻ ⁼ · ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹ 
A ⁿ ʰ ˣ ʸ ʰ ʷ ʳ ʴ ˢ ʲ ʺ ʻ ʼ 

Subscript numbers:
M₍₎ ₋ ₊ ₌ . ‚ ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ ‹ ›  
X …

Table createion/printing:
├ ┤ ┬ ┴ ┼ ═ ║ ╒ ╓ ╔ ╕ ╖ ╗ ╘ ╙ ╚ ╛ ╠ ╬ ╧ 

Chess game:
♔♕♖♗♘♙♚♛♜♝♞♟   

Star shapes:
✡✢✣✤✥✦✬✭✮✯✱✲✳✴✵✶✷✸✹✺✻✼✽✾✿❀❂❃❄❅❆❇❈❉   

### Dice Symbols
⚀ ⚁ ⚂ ⚃ ⚄ ⚅

### Bulet Points
➀ ➁ ➂ ➃ ➄ ➅ ➆ ➇ ➈ ➉

## Unicode Operators

Using  "DejaVu Sans Mono" font we can define new operators and symbols. 
These symbols however can be used only in strings. We do not use Unicode operators in the language. 
This may be a nice feature to have but unfortunately not very practical.

Symbol |UNC    | Description
-------|-------|----------------------------------------------------------
π      |U+03C0 | 3.14 (radian) equivalent to 180°  
λ      |U+03BB | lambda function

**Logical operators**

Symbol |UNC    | Description
-------|-------|----------------------------------------------------------
¬      |U+00AC | NOT
∧      |U+2227 | AND
∨      |U+2228 | OR
≈      |U+2248 | Almost equal to (1.5 ≈ 1) = (1.5 ≈ 2)
=      |U+003D | Equal
≠      |U+2260 | Not equal
≤      |U+2264 | Less then or equal to 
≥      |U+2265 | Greater then or equal to
∴      |U+2234 | Therefore (→) U+2192
∵      |U+2235 | Becouse   (←) U+2190

**Math operators**

Symbol|UNC    | Description
------|-------|----------------------------------------------------------
∞     |U+211E | Infinite number
°     |U+00B0 | Degree symbol
∠     |U+2220 | Angle between lines
∟     |U+221F | Angle between lines 
⊢     |U+22A2 | Is Right Tack 
⊣     |U+22A3 | Is Left Tack 
⊤     |U+22A4 | Is Down Tack  
⊥     |U+22A5 | Is Up Tack 
·     |U+00B7 | Middle Dot
∗     |U+2217 | Middle Asterisk
×     |U+00D7 | Multiplication 
÷     |U+00F7 | Division 
±     |U+00B1 | Change sign unary operator (-1xA) =±A
√     |U+221A | Square root sqrt(m).
∑     |U+2211 | ∑A = A[0] + A[1]+…A[n]
∏     |U+220F | ∏A = A[0] × A[1]×…A[n] |= A[0] + A[1]+…A[n]
∆     |U+2206 | Increment: ∆x=x2-x1, ∆(x,y)=√(x²-y²)
∫     |U+220F | Integral:  ex. ∫\[a..b](x\^2)dx

**Set operators:**

Symbol | Unicode | Description
-------|---------|----------------------------------------------------------
∅      |U+2205   | Empty set
∀      |U+2200   | For all in set
∃      |U+2203   | There exist one or many
∄      |U+2204   | There does not exist any
∈      |U+2208   | Element of set
∉      |U+2209   | Not element of set
∩      |U+2229   | Intersection
∪      |U+220C   | Union
⊂      |U+2282   | Subset of B  (A ⊂ B) 
⊄      |U+2284   | Not subset of 
⊆      |U+2286   | Subset of or equal
⊊      |U+228A   | Proper superset
⊃      |U+2283   | Superset of B  (A ⊃ B) 
⊅      |U+2285   | Mot a superset of
⊇      |U+2287   | Superset of or equal to
⊉      |U+2289   | Not superset and not equal to
⊋      |U+228B   | Superset of and not equal to 
≺      |U+227A   | Precedes
≻      |U+227B   | Succeeds
≼      |U+227C   | Precedes or equal to
≽      |U+227D   | Succeeds or equal to


## Other Resources

Brackets ⟨⟩❬❭❰❱❲❳❴❵

Unicode Math Symbols ∑ ∫ π² ∞

Complete list of math symbols in Unicode 11 grouped by purpose.

Commonly used greek letters 
α β γ δ ε ζ η θ ι κ λ μ ν ξ ο π ρ ς τ υ φ χ ψ ω

superscript 
A ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹ ⁺ ⁻ ⁼ ⁽ ⁾ ⁿ ⁱ

subscript 
A ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ ₊ ₋ ₌ ₍ ₎ ₐ ₑ ₕ ᵢ ⱼ ₖ ₗ ₘ ₙ ₒ ₚ ᵣ ₛ ₜ ᵤ ᵥ ₓ ₔ


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
⋅ 
⋆
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

Using fraction sign: ⁄

A = (¹⁄₂,¹⁄₄,¹⁄₈,¹⁄₁₆)
B = [¹⁄₂,¹⁄₄,¹⁄₈,¹⁄₁₆]
C = {¹⁄₂,¹⁄₄,¹⁄₈,¹⁄₁₆}

Using hooks and extension bar:
```
    ⎡ 1  1  1  1⎤   
A = ⎢——,——,——,——⎥   
    ⎣ 2  4  8 16⎦   
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
Large sum:

 \

    ₙ
y = ∑(x)
    ¹
    ∑(X)
a = ————
     n

A ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹ ⁺ ⁻ ⁼ ⁽ ⁾ ⁿ ⁱ
A ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ ₊ ₋ ₌ ₍ ₎ ₐ ₑ ₕ ᵢ ⱼ ₖ ₗ ₘ ₙ ₒ ₚ ᵣ ₛ ₜ ᵤ ᵥ ₓ ₔ

**Missing**
Some subscript/superscript characters are missing.
I found this proposal: http://unicode.org/L2/L2011/11208-n4068.pdf

**Combining symbols**
xor is not represented correctly
Combining symbols does not help.

**Alternative Historical Research**
There was once upon a time a language called APL.

https://en.wikipedia.org/wiki/APL_(programming_language)