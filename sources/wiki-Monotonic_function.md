---
source: https://en.wikipedia.org/wiki/Monotonic_function
fetched: 2026-06-19
---

Order-preserving mathematical function "Monotonicity" redirects here. For information on monotonicity as it pertains to [voting systems](./Voting_systems), see [monotonicity criterion](./Monotonicity_criterion). For information on monotonicity as it pertains to logical systems, see [Monotonicity of entailment](./Monotonicity_of_entailment). "Monotonic" redirects here. For other uses, see [Monotone (disambiguation)](./Monotone_(disambiguation)). [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/86/Monotonicity_example1.svg/250px-Monotonicity_example1.svg.png)](./File:Monotonicity_example1.svg)Figure 1. A monotonically non-decreasing function [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a0/Monotonicity_example2.svg/250px-Monotonicity_example2.svg.png)](./File:Monotonicity_example2.svg)Figure 2. A monotonically non-increasing function [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/73/Monotonicity_example3.svg/250px-Monotonicity_example3.svg.png)](./File:Monotonicity_example3.svg)Figure 3. A function that is *not* monotonic 

In [mathematics](./Mathematics), a **monotonic function** (or **monotone function**) is a [function](./Function_(mathematics)) between [ordered sets](./List_of_order_structures_in_mathematics) that preserves or reverses the given [order](./Order_relation).[[1]](./Monotonic_function#cite_note-1)[[2]](./Monotonic_function#cite_note-:1-2)[[3]](./Monotonic_function#cite_note-:0-3) This concept first arose in [calculus](./Calculus), and was later generalized to the more abstract setting of [order theory](./Order_theory).

 

## In calculus and analysis

 

In [calculus](./Calculus), a function     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) defined on a [subset](./Subset) of the [real numbers](./Real_numbers) with real values is called  *monotonic* if it is either entirely non-decreasing, or entirely non-increasing.[[2]](./Monotonic_function#cite_note-:1-2) That is, as per Fig. 1, a function that increases monotonically does not exclusively have to increase, it simply must not decrease.

 

A function is termed *monotonically increasing* (also *increasing* or *non-decreasing*)[[3]](./Monotonic_function#cite_note-:0-3) if for all     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) and     y   {\displaystyle y}  ![{\displaystyle y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b8a6208ec717213d4317e666f1ae872e00620a0d) such that     x ≤ ≤  y   {\displaystyle x\leq y}  ![{\displaystyle x\leq y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c07a0bc023490be1c08e6c33a9cdc93bec908224) one has      f   ( x )  ≤ ≤  f   ( y )    {\displaystyle f\!\left(x\right)\leq f\!\left(y\right)}  ![{\displaystyle f\!\left(x\right)\leq f\!\left(y\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a6cddeb7f21c061d758a435783ad57163a15c632), so     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) preserves the order (see Figure 1). Likewise, a function is called *monotonically decreasing* (also *decreasing* or *non-increasing*)[[3]](./Monotonic_function#cite_note-:0-3) if, whenever     x ≤ ≤  y   {\displaystyle x\leq y}  ![{\displaystyle x\leq y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c07a0bc023490be1c08e6c33a9cdc93bec908224), then     f   ( x )  ≥ ≥  f   ( y )    {\displaystyle f\!\left(x\right)\geq f\!\left(y\right)}  ![{\displaystyle f\!\left(x\right)\geq f\!\left(y\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6eb27491d0ae751c3d53fc364a89524623dfba77), so it *reverses* the order (see Figure 2).

 

If the order     ≤ ≤    {\displaystyle \leq }  ![{\displaystyle \leq }](https://wikimedia.org/api/rest_v1/media/math/render/svg/440568a09c3bfdf0e1278bfa79eb137c04e94035) in the definition of monotonicity is replaced by the strict order     <   {\displaystyle <}  ![{\displaystyle <}](https://wikimedia.org/api/rest_v1/media/math/render/svg/33737c89a17785dacc8638b4d66db3d5c8670de1), one obtains a stronger requirement. A function with this property is called *strictly increasing* (also *increasing*).[[3]](./Monotonic_function#cite_note-:0-3)[[4]](./Monotonic_function#cite_note-:2-4) Again, by inverting the order symbol, one finds a corresponding concept called *strictly decreasing* (also *decreasing*).[[3]](./Monotonic_function#cite_note-:0-3)[[4]](./Monotonic_function#cite_note-:2-4) A function with either property is called *strictly monotone*. Functions that are strictly monotone are [one-to-one](./One-to-one_function) (because for     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) not equal to     y   {\displaystyle y}  ![{\displaystyle y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b8a6208ec717213d4317e666f1ae872e00620a0d), either     x < y   {\displaystyle x<y}  ![{\displaystyle x<y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aeb239de6fee56ea8b6a65f7858d95b87632069f) or     x > y   {\displaystyle x>y}  ![{\displaystyle x>y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e8432c5c4451b66818abae111d41f27d6de8623) and so, by monotonicity, either     f   ( x )  < f   ( y )    {\displaystyle f\!\left(x\right)<f\!\left(y\right)}  ![{\displaystyle f\!\left(x\right)<f\!\left(y\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7e45fc569a5e9624c01674fc06cb02b3d4cd35de) or     f   ( x )  > f   ( y )    {\displaystyle f\!\left(x\right)>f\!\left(y\right)}  ![{\displaystyle f\!\left(x\right)>f\!\left(y\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/728fae40f016d92409c728fcda0e38bab9b8cd80), thus     f   ( x )  ≠ ≠  f   ( y )    {\displaystyle f\!\left(x\right)\neq f\!\left(y\right)}  ![{\displaystyle f\!\left(x\right)\neq f\!\left(y\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af8a7e076236ea003e1d23c3b3269d00091f4d9a).

 

To avoid ambiguity, the terms *weakly monotone*, *weakly increasing* and *weakly decreasing* are often used to refer to non-strict monotonicity.

 

The terms "non-decreasing" and "non-increasing" should not be confused with the (much weaker) negative qualifications "not decreasing" and "not increasing". For example, the non-monotonic function shown in figure 3 first falls, then rises, then falls again. It is therefore not decreasing and not increasing, but it is neither non-decreasing nor non-increasing.

 

A function     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is said to be *absolutely monotonic* over an interval      (  a , b  )    {\displaystyle \left(a,b\right)}  ![{\displaystyle \left(a,b\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4c254f2a8eaae4e3c7e8f2192c196d621e6c8659) if the [derivatives](./Derivative) of all orders of     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) are [nonnegative](./Nonnegative) or all [nonpositive](./Nonpositive) at all points on the interval.

 

### Inverse of function

 

All strictly monotonic functions are [invertible](./Inverse_function) because they are guaranteed to have a one-to-one mapping from their range to their domain.

 

However, functions that are only weakly monotone need not be invertible; they may be constant on some interval (and therefore not one-to-one).

 

A function may be strictly monotonic over a limited a range of values and thus have an inverse on that range even though it is not strictly monotonic everywhere. For example, if     y = g ( x )   {\displaystyle y=g(x)}  ![{\displaystyle y=g(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/26c08f8fd3471dad5e2c45c2f753ffd7c9aba4ed) is strictly increasing on the range     [ a , b ]   {\displaystyle [a,b]}  ![{\displaystyle [a,b]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c4b788fc5c637e26ee98b45f89a5c08c85f7935), then it has an inverse     x = h ( y )   {\displaystyle x=h(y)}  ![{\displaystyle x=h(y)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/04605d887de339e440c9b6a6026f3bc8c53d70ee) on the range     [ g ( a ) , g ( b ) ]   {\displaystyle [g(a),g(b)]}  ![{\displaystyle [g(a),g(b)]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/091dac07a170589d4ed7e965623e55d374a9de23).

 

The term *monotonic* is sometimes used in place of *strictly monotonic*, so a source may state that all monotonic functions are invertible when they really mean that all strictly monotonic functions are invertible.[*[citation needed](./Wikipedia:Citation_needed)*]

 

### Monotonic transformation

 

The term *monotonic transformation* (or *monotone transformation*) may also cause confusion because it refers to a transformation by a strictly increasing function. This is the case in economics with respect to the ordinal properties of a [utility function](./Utility_function) being preserved across a monotonic transform (see also [monotone preferences](./Monotone_preferences)).[[5]](./Monotonic_function#cite_note-5) In this context, the term "monotonic transformation" refers to a positive monotonic transformation and is intended to distinguish it from a "negative monotonic transformation," which reverses the order of the numbers.[[6]](./Monotonic_function#cite_note-6)

 

### Some basic applications and results

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/67/Monotonic_dense_jumps_svg.svg/960px-Monotonic_dense_jumps_svg.svg.png)](./File:Monotonic_dense_jumps_svg.svg)Monotonic function with a dense set of jump discontinuities (several sections shown) [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Growth_equations.png/960px-Growth_equations.png)](./File:Growth_equations.png)Plots of 6 monotonic growth functions 

The following properties are true for a monotonic function     f : :   R  → →   R    {\displaystyle f\colon \mathbb {R} \to \mathbb {R} }  ![{\displaystyle f\colon \mathbb {R} \to \mathbb {R} }](https://wikimedia.org/api/rest_v1/media/math/render/svg/b1cacd5f7bbe1027cc75fbe2fbd9cb5e79485302):

 
-     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) has [limits](./Limit_of_a_function) from the right and from the left at every point of its [domain](./Domain_of_a_function);
-     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) has a limit at positive or negative infinity (    ± ±  ∞ ∞    {\displaystyle \pm \infty }  ![{\displaystyle \pm \infty }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c586ae37f8efec026b8a4ea3f6a5253576c2c4e6)) of either a real number,     ∞ ∞    {\displaystyle \infty }  ![{\displaystyle \infty }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c26c105004f30c27aa7c2a9c601550a4183b1f21), or     − −  ∞ ∞    {\displaystyle -\infty }  ![{\displaystyle -\infty }](https://wikimedia.org/api/rest_v1/media/math/render/svg/ca2608c4b5fd3bffc73585f8c67e379b4e99b6f1).
-     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) can only have [jump](./Jump_discontinuities) and [removable discontinuities](./Removable_discontinuity).
-     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) can only have [countably](./Countably) many [discontinuities](./Discontinuities_of_monotone_functions) in its domain. The discontinuities, however, do not necessarily consist of isolated points and may even be [dense](./Dense_set) in an interval (*a*, *b*). For example, for any [summable sequence](./Summable_sequence)    (  a  i   )  (a_{i})  ![(a_{i})](https://wikimedia.org/api/rest_v1/media/math/render/svg/6b5da80cd4cfba3b02a32730b725b17fbad89cc0) of positive numbers and any enumeration     (  q  i   )   {\displaystyle (q_{i})}  ![{\displaystyle (q_{i})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8c9c8341c4e830b2e3c6213262f4f3ecc59887d6) of the [rational numbers](./Rational_number), the monotonically increasing function     f ( x ) =  ∑ ∑    q  i   ≤ ≤  x    a  i     {\displaystyle f(x)=\sum _{q_{i}\leq x}a_{i}}  ![{\displaystyle f(x)=\sum _{q_{i}\leq x}a_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fcecfc2a94fa633d8dc35dddbe646241412337e5) is continuous exactly at every irrational number (cf. picture). It is the [cumulative distribution function](./Cumulative_distribution_function) of the [discrete measure](./Discrete_measure) on the rational numbers, where      a  i     {\displaystyle a_{i}}  ![{\displaystyle a_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0bc77764b2e74e64a63341054fa90f3e07db275f) is the weight of      q  i     {\displaystyle q_{i}}  ![{\displaystyle q_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2752dcbff884354069fe332b8e51eb0a70a531b6).
- If     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is [differentiable](./Differentiable) at      x  ∗ ∗    ∈ ∈    R     {\displaystyle x^{*}\in {\mathbb {R}}}  ![{\displaystyle x^{*}\in {\mathbb {R}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b27381c729d63c931d5b5d3a06a52bda2e68e222) and      f ′  (  x  ∗ ∗    ) > 0   {\displaystyle f'(x^{*})>0}  ![{\displaystyle f'(x^{*})>0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/260fbceb8bc06a13f43fbe16f5058d87b4aa3087), then there is a non-degenerate [ interval](./Interval_(mathematics)) *I* such that      x  ∗ ∗    ∈ ∈  I   {\displaystyle x^{*}\in I}  ![{\displaystyle x^{*}\in I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/195b95e733ef44a2740ced7741bb85c93a96c847) and     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is increasing on *I*.
- As a partial converse, if     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is differentiable and increasing on an interval,     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f), then its derivative is nonnegative at every point in     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f). Furthermore, the set     A = { x ∈ ∈  I :  f ′  ( x ) > 0 }   {\displaystyle A=\{x\in I:f'(x)>0\}}  ![{\displaystyle A=\{x\in I:f'(x)>0\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2396b39354669ffcfa068d92be9a0cf3c80dc02f) is dense with positive [Lebesgue measure](./Lebesgue_measure). Not much more can be said about     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3); for instance,     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) may be [ meagre](./Meagre_set), as in the case of a [Pompeiu derivative](./Pompeiu_derivative), and for fixed     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f), the Lebesgue measure of     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) can be made arbitrarily close to     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) via a suitable choice of     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61).

 

These properties are the reason why monotonic functions are useful in technical work in [analysis](./Mathematical_analysis). Other important properties of these functions include:

 
- if     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is a monotonic function defined on an [interval](./Interval_(mathematics))     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f), then     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is [differentiable](./Derivative) [almost everywhere](./Almost_everywhere) on     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f); i.e. the set of numbers     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) in     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f) such that     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is not differentiable in     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) has [Lebesgue](./Lebesgue_measure) [measure zero](./Measure_zero). In addition, this result cannot be improved to countable: see [Cantor function](./Cantor_function).
- if this set is countable, then     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is absolutely continuous
- if     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is a monotonic function defined on an interval      [  a , b  ]    {\displaystyle \left[a,b\right]}  ![{\displaystyle \left[a,b\right]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f30926fb280a9fdf66fd931e14d4363cb824feaa), then     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is [Riemann integrable](./Riemann_integral).

 

An important application of monotonic functions is in [probability theory](./Probability_theory). If     X   {\displaystyle X}  ![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) is a [random variable](./Random_variable), its [cumulative distribution function](./Cumulative_distribution_function)      F  X     ( x )  =  Prob    (  X ≤ ≤  x  )    {\displaystyle F_{X}\!\left(x\right)={\text{Prob}}\!\left(X\leq x\right)}  ![{\displaystyle F_{X}\!\left(x\right)={\text{Prob}}\!\left(X\leq x\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3c3b7294a8678c1ed20b608eb9e4a6d8267760f1) is a monotonically increasing function.

 

A function is *[unimodal](./Unimodal_function)* if it is monotonically increasing up to some point (the *[mode](./Maximum_and_minimum)*) and then monotonically decreasing.

 

When     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is a *strictly monotonic* function, then     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is [injective](./Injective) on its domain, and if     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) is the [range](./Range_of_a_function) of     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61), then there is an [inverse function](./Inverse_function) on     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) for     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61). In contrast, each constant function is monotonic, but not injective,[[7]](./Monotonic_function#cite_note-7) and hence cannot have an inverse.

 

The graphic shows six monotonic functions. Their simplest forms are shown in the plot area and the expressions used to create them are shown on the *y*-axis.

 

## In topology

 

 

A map     f : X → →  Y   {\displaystyle f:X\to Y}  ![{\displaystyle f:X\to Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/abd1e080abef4bbdab67b43819c6431e7561361c) is said to be *monotone* if each of its [fibers](./Fiber_(mathematics)#Fiber_in_naive_set_theory) is [connected](./Connected_(topology)); that is, for each element     y ∈ ∈  Y ,   {\displaystyle y\in Y,}  ![{\displaystyle y\in Y,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/75e1353f0febe9bcf693d849ec82ce8d94e5f7bc) the (possibly empty) set      f  − −  1   ( y )   {\displaystyle f^{-1}(y)}  ![{\displaystyle f^{-1}(y)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b357745fa4a2178733a502b4432072be8222fd4) is a connected [subspace](./Subspace_topology) of     X .   {\displaystyle X.}  ![{\displaystyle X.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5ba76c5a460c4a0bb1639a193bc1830f0a773e03)

 

## In functional analysis

 

In [functional analysis](./Functional_analysis) on a [topological vector space](./Topological_vector_space)     X   {\displaystyle X}  ![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab), a (possibly non-linear) operator     T : X → →   X  ∗ ∗      {\displaystyle T:X\rightarrow X^{*}}  ![{\displaystyle T:X\rightarrow X^{*}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4f5555d4d4e14041de9e01c07a31cd646455e1a1) is said to be a *monotone operator* if

 

    ( T u − −  T v , u − −  v ) ≥ ≥  0  ∀ ∀  u , v ∈ ∈  X .   {\displaystyle (Tu-Tv,u-v)\geq 0\quad \forall u,v\in X.}  ![{\displaystyle (Tu-Tv,u-v)\geq 0\quad \forall u,v\in X.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fb7241966275cad3f2d61c6d7e8078c8196b088) [Kachurovskii's theorem](./Kachurovskii's_theorem) shows that [convex functions](./Convex_function) on [Banach spaces](./Banach_space) have monotonic operators as their derivatives.

 

A subset     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b) of     X × ×   X  ∗ ∗      {\displaystyle X\times X^{*}}  ![{\displaystyle X\times X^{*}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aa423f368993d2d9347913501622e3cebc17374f) is said to be a *monotone set* if for every pair     [  u  1   ,  w  1   ]   {\displaystyle [u_{1},w_{1}]}  ![{\displaystyle [u_{1},w_{1}]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/42f2c67bc4887974d491ba4a419dc798ed50d8cd) and     [  u  2   ,  w  2   ]   {\displaystyle [u_{2},w_{2}]}  ![{\displaystyle [u_{2},w_{2}]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/32202d66739c2039a8b74e861330c713a44db704) in     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b),

 

    (  w  1   − −   w  2   ,  u  1   − −   u  2   ) ≥ ≥  0.   {\displaystyle (w_{1}-w_{2},u_{1}-u_{2})\geq 0.}  ![{\displaystyle (w_{1}-w_{2},u_{1}-u_{2})\geq 0.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/356e18f7b81113ab34d4866f4a9177c86cb4c3d4)     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b) is said to be *maximal monotone* if it is maximal among all monotone sets in the sense of set inclusion.  The graph of a monotone operator     G ( T )   {\displaystyle G(T)}  ![{\displaystyle G(T)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/140a25dc4428018d67e29b3eb54b07f2bc68d4de) is a monotone set. A monotone operator is said to be *maximal monotone* if its graph is a *maximal monotone set*.

 

## In order theory

 

Order theory deals with arbitrary [partially ordered sets](./Partially_ordered_set) and [preordered sets](./Preorder) as a generalization of real numbers. The above definition of monotonicity is relevant in these cases as well. However, the terms "increasing" and "decreasing" are avoided, since their conventional pictorial representation does not apply to orders that are not [total](./Total_order). Furthermore, the [strict](./Strict_order) relations     <   {\displaystyle <}  ![{\displaystyle <}](https://wikimedia.org/api/rest_v1/media/math/render/svg/33737c89a17785dacc8638b4d66db3d5c8670de1) and     >   {\displaystyle >}  ![{\displaystyle >}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1b27b77ab4e3293ea9ce65cef60fea655c398423) are of little use in many non-total orders and hence no additional terminology is introduced for them.

 

Letting     ≤ ≤    {\displaystyle \leq }  ![{\displaystyle \leq }](https://wikimedia.org/api/rest_v1/media/math/render/svg/440568a09c3bfdf0e1278bfa79eb137c04e94035) denote the partial order relation of any partially ordered set, a *monotone* function, also called *isotone*, or *order-preserving*, satisfies the property

 

    x ≤ ≤  y  ⟹ ⟹   f ( x ) ≤ ≤  f ( y )   {\displaystyle x\leq y\implies f(x)\leq f(y)}  ![{\displaystyle x\leq y\implies f(x)\leq f(y)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5678041c134b3e6451e1feaaf8e670565522e63)

 

for all x and y in its domain. The composite of two monotone mappings is also monotone.

 

The [dual](./Duality_(order_theory)) notion is often called *antitone*, *anti-monotone*, or *order-reversing*. Hence, an antitone function f satisfies the property

 

    x ≤ ≤  y  ⟹ ⟹   f ( y ) ≤ ≤  f ( x ) ,   {\displaystyle x\leq y\implies f(y)\leq f(x),}  ![{\displaystyle x\leq y\implies f(y)\leq f(x),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a02e77af95ab9aef1f6230243aea212f3a0f36f1)

 

for all x and y in its domain.

 

A [constant function](./Constant_function) is both monotone and antitone; conversely, if f is both monotone and antitone, and if the domain of f is a [lattice](./Lattice_(order)), then f must be constant.

 

Monotone functions are central in order theory. They appear in most articles on the subject and examples from special applications are found in these places. Some notable special monotone functions are [order embeddings](./Order_embedding) (functions for which     x ≤ ≤  y   {\displaystyle x\leq y}  ![{\displaystyle x\leq y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c07a0bc023490be1c08e6c33a9cdc93bec908224) [if and only if](./If_and_only_if)     f ( x ) ≤ ≤  f ( y ) )   {\displaystyle f(x)\leq f(y))}  ![{\displaystyle f(x)\leq f(y))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ca2b65c72e2f561be6f1f2cfdb5120f9b07b98da) and [order isomorphisms](./Order_isomorphism) ([surjective](./Surjective) order embeddings).

 

## In the context of search algorithms

 

In the context of [search algorithms](./Search_algorithm) monotonicity (also called consistency) is a condition applied to [heuristic functions](./Heuristic_function).  A heuristic     h ( n )   {\displaystyle h(n)}  ![{\displaystyle h(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/125976c5970a395422e1baf572a26f31ae5e0b7d) is monotonic if, for every node n and every successor n' of n generated by any action a, the estimated cost of reaching the goal from n is no greater than the step cost of getting to n' plus the estimated cost of reaching the goal from n',

 

    h ( n ) ≤ ≤  c  (  n , a ,  n ′   )  + h  (  n ′  )  .   {\displaystyle h(n)\leq c\left(n,a,n'\right)+h\left(n'\right).}  ![{\displaystyle h(n)\leq c\left(n,a,n'\right)+h\left(n'\right).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/95a8ffad18b7c44ad1d8b8f1c6e5875d462797c0)

 

This is a form of [triangle inequality](./Triangle_inequality), with n, n', and the goal Gn closest to n.  Because every monotonic heuristic is also [admissible](./Admissible_heuristic), monotonicity is a stricter requirement than admissibility.  Some [heuristic algorithms](./Heuristic_algorithm) such as [A*](./A*_search_algorithm) can be proven [optimal](./Asymptotically_optimal_algorithm) provided that the heuristic they use is monotonic.[[8]](./Monotonic_function#cite_note-8)

 

## In Boolean functions

 
| With the nonmonotonic function "ifathen bothbandc",falsenodes appear abovetruenodes. |
| --- |

 
| Hasse diagram of the monotonic function "at least two ofa,b,chold". Colors indicate function output values. |
| --- |

 

In [Boolean algebra](./Boolean_algebra), a monotonic function is one such that for all a*i* and b*i* in {0,1}, if *a*1 ≤ *b*1, *a*2 ≤ *b*2, ..., *a**n* ≤ *b**n* (i.e. the Cartesian product {0, 1}n is ordered [coordinatewise](./Coordinatewise_order)), then f(*a*1, ..., *a**n*) ≤ f(*b*1, ..., *b**n*). In other words, a Boolean function is monotonic if, for every combination of inputs, switching one of the inputs from false to true can only cause the output to switch from false to true and not from true to false. Graphically, this means that an n-ary Boolean function is monotonic when its representation as an [n-cube](./Hypercube) labelled with truth values has no upward edge from *true* to *false*.  (This labelled [Hasse diagram](./Hasse_diagram) is the [dual](./Duality_(mathematics)#Dimension-reversing_dualities) of the function's labelled [Venn diagram](./Venn_diagram), which is the more common representation for *n* ≤ 3.)

 

The monotonic Boolean functions are precisely those that can be defined by an expression combining the inputs (which may appear more than once) using only the operators *[and](./Logical_conjunction)* and *[or](./Logical_disjunction)* (in particular *[not](./Negation)* is forbidden). For instance "at least two of a, b, c hold" (the ternary [majority function](./Majority_function)) is a monotonic function of a, b, c, since it can be written for instance as ((a and b) or (a and c) or (b and c)).

 

The number of such functions on n variables is known as the [Dedekind number](./Dedekind_number) of n.

 

[SAT solving](./SAT_solving), generally an [NP-hard](./NP-hard) task, can be achieved efficiently when all involved functions and predicates are monotonic and Boolean.[[9]](./Monotonic_function#cite_note-9)

 

## See also

 
- [Monotone cubic interpolation](./Monotone_cubic_interpolation)
- [Pseudo-monotone operator](./Pseudo-monotone_operator)
- [Spearman's rank correlation coefficient](./Spearman's_rank_correlation_coefficient) - measure of monotonicity in a set of data
- [Total monotonicity](./Total_monotonicity)
- [Cyclical monotonicity](./Cyclical_monotonicity)
- [Operator monotone function](./Operator_monotone_function)
- [Monotone set function](./Monotone_set_function)
- [Absolutely and completely monotonic functions and sequences](./Absolutely_and_completely_monotonic_functions_and_sequences)

 

## Notes

  
1. [↑](./Monotonic_function#cite_ref-1) Clapham, Christopher; Nicholson, James (2014). *Oxford Concise Dictionary of Mathematics* (5th ed.). Oxford University Press.
2. [1](./Monotonic_function#cite_ref-:1_2-0) [2](./Monotonic_function#cite_ref-:1_2-1) Stover, Christopher. ["Monotonic Function"](http://mathworld.wolfram.com/MonotonicFunction.html). *Wolfram MathWorld*. Retrieved 2018-01-29.
3. [1](./Monotonic_function#cite_ref-:0_3-0) [2](./Monotonic_function#cite_ref-:0_3-1) [3](./Monotonic_function#cite_ref-:0_3-2) [4](./Monotonic_function#cite_ref-:0_3-3) [5](./Monotonic_function#cite_ref-:0_3-4) ["Monotone function"](https://www.encyclopediaofmath.org/index.php/Monotone_function). *Encyclopedia of Mathematics*. Retrieved 2018-01-29.
4. [1](./Monotonic_function#cite_ref-:2_4-0) [2](./Monotonic_function#cite_ref-:2_4-1) [Spivak, Michael](./Michael_Spivak) (1994). *Calculus*. Houston, Texas: Publish or Perish, Inc. p. 192. [ISBN](./ISBN_(identifier)) [0-914098-89-6](./Special:BookSources/0-914098-89-6).
5. [↑](./Monotonic_function#cite_ref-5) See the section on Cardinal Versus Ordinal Utility in [Simon & Blume (1994)](./Monotonic_function#CITEREFSimonBlume1994).
6. [↑](./Monotonic_function#cite_ref-6) Varian, Hal R. (2010). *Intermediate Microeconomics* (8th ed.). W. W. Norton & Company. p. 56. [ISBN](./ISBN_(identifier)) [9780393934243](./Special:BookSources/9780393934243).
7. [↑](./Monotonic_function#cite_ref-7) if its domain has more than one element
8. [↑](./Monotonic_function#cite_ref-8) Conditions for optimality:  Admissibility and consistency pg. 94–95 ([Russell & Norvig 2010](./Monotonic_function#CITEREFRussellNorvig2010)).
9. [↑](./Monotonic_function#cite_ref-9) Bayless, Sam; Bayless, Noah; Hoos, Holger H.; Hu, Alan J. (2015). [*SAT Modulo Monotonic Theories*](https://ojs.aaai.org/index.php/AAAI/article/view/9755). Proc. 29th AAAI Conf. on Artificial Intelligence. AAAI Press. pp. 3702–3709. [arXiv](./ArXiv_(identifier)):[1406.0043](https://arxiv.org/abs/1406.0043). [doi](./Doi_(identifier)):[10.1609/aaai.v29i1.9755](https://doi.org/10.1609%2Faaai.v29i1.9755). [Archived](https://web.archive.org/web/20231211023402/https://ojs.aaai.org/index.php/AAAI/article/view/9755) from the original on Dec 11, 2023. 

 

## Bibliography

 
- Bartle, Robert G. (1976). *The elements of real analysis* (second ed.).
- Grätzer, George (1971). *Lattice theory: first concepts and distributive lattices*. W. H. Freeman. [ISBN](./ISBN_(identifier)) [0-7167-0442-0](./Special:BookSources/0-7167-0442-0).
- Pemberton, Malcolm; Rau, Nicholas (2001). *Mathematics for economists: an introductory textbook*. Manchester University Press. [ISBN](./ISBN_(identifier)) [0-7190-3341-1](./Special:BookSources/0-7190-3341-1).
- Renardy, Michael & Rogers, Robert C. (2004). *An introduction to partial differential equations*. Texts in Applied Mathematics 13 (Second ed.). New York: Springer-Verlag. p. 356. [ISBN](./ISBN_(identifier)) [0-387-00444-0](./Special:BookSources/0-387-00444-0).
- Riesz, Frigyes & Béla Szőkefalvi-Nagy (1990). *Functional Analysis*. Courier Dover Publications. [ISBN](./ISBN_(identifier)) [978-0-486-66289-3](./Special:BookSources/978-0-486-66289-3).
- Russell, Stuart J.; Norvig, Peter (2010). *Artificial Intelligence: A Modern Approach* (3rd ed.). Upper Saddle River, New Jersey: Prentice Hall. [ISBN](./ISBN_(identifier)) [978-0-13-604259-4](./Special:BookSources/978-0-13-604259-4).
- Simon, Carl P.; Blume, Lawrence (April 1994). *Mathematics for Economists* (first ed.). Norton. [ISBN](./ISBN_(identifier)) [978-0-393-95733-4](./Special:BookSources/978-0-393-95733-4). (Definition 9.31)

 

## External links

 
- ["Monotone function"](https://www.encyclopediaofmath.org/index.php?title=Monotone_function), *[Encyclopedia of Mathematics](./Encyclopedia_of_Mathematics)*, [EMS Press](./European_Mathematical_Society), 2001 [1994]
- [Convergence of a Monotonic Sequence](http://demonstrations.wolfram.com/ConvergenceOfAMonotonicSequence/) by Anik Debnath and Thomas Roxlo (The Harker School), [Wolfram Demonstrations Project](./Wolfram_Demonstrations_Project).
- [Weisstein, Eric W.](./Eric_W._Weisstein) ["Monotonic Function"](https://mathworld.wolfram.com/MonotonicFunction.html). *[MathWorld](./MathWorld)*.

 
| vteOrder theory |
| --- |
| TopicsGlossaryCategory |
| Key concepts | Binary relationBoolean algebraCyclic orderLatticePartial orderPreorderTotal orderWeak ordering |
| Results | Boolean prime ideal theoremCantor–Bernstein theoremCantor's isomorphism theoremDilworth's theoremDushnik–Miller theoremHausdorff maximal principleKnaster–Tarski theoremKruskal's tree theoremLaver's theoremMirsky's theoremSzpilrajn extension theoremZorn's lemma |
| Properties&Types(list) | AntisymmetricAsymmetricBoolean algebratopicsCompletenessConnectedCoveringDenseDirected(Partial)EquivalenceFoundationalHeyting algebraHomogeneousIdempotentLatticeBoundedComplementedCompleteDistributiveJoin and meetPartial orderChain-completeEulerianGradedLocally finiteStrictPrefix orderPreorderTotalReflexiveSemilatticeSemiorderSymmetricToleranceTotalTransitiveWell-foundedWell-quasi-ordering(Better)(Pre)Well-order |
| Constructions | CompositionConverse/TransposeLexicographic orderLinear extensionProduct orderReflexive closureSeries-parallel partial orderStar productSymmetric closureTransitive closure |
| Topology&Orders | Alexandrov topology&Specialization preorderOrdered topological vector spaceNormal coneOrder topologyOrder topologyTopological vector latticeBanachFréchetLocally convexNormed |
| Related | AntichainCofinalCofinalityComparabilityGraphDualityFilterHasse diagramIdealNetSubnetOrder morphismEmbeddingIsomorphismOrder typeOrdered fieldPositive cone of an ordered fieldOrdered vector spacePartially orderedPositive cone of an ordered vector spaceRiesz spacePartially ordered groupPositive cone of a partially ordered groupUpper setYoung's lattice |