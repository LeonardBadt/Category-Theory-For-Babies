---
share: "true"
---

> [!question] What is a function?
> what does $y = \sin(x)$ mean?

# CATEGORIES!
In Category theory, we don't need set theory! We can use the following axioms called "metacategories", or an even simpler notion, a "metagraph"

> [!info] Metagraph
> Metagraphs consist of the following itesms:
> 1) Objects: $a, b, c, ...$ 
> 2) Arrows: $f, g, h, ...$
> 3) 2 Operations
> 	- Domain : An operation that assigns an arrow $f$ to an object $a = dom f$
> 	- Codomain : An operation that assigns an arrow $f$ to an object $b = cod f$
>  While not clear by their definitions, a visual is best understood, where $f$ is an actual arrow starting at a domain "source" and ending at its codomain "target"
>  $$f : a \to b \quad \text{ or } \quad a\stackrel{f}{\rightarrow} b$$
>  4) Finite Graphs can have visual representation
>  Lets represent an arbitrary object by the following notation $\cdot$
>  $\cdot \rightarrow \cdot \rightarrow \cdot$
>  ![[Pasted image 20240405210358.png|Pasted image 20240405210358.png]]
>  $\cdot \rightrightarrows \cdot$
>  ![[Pasted image 20240405210457.png|Pasted image 20240405210457.png]]

> [!tip] Theorem 1: The same arrows:
> In a category, given two arrows, $f, g$, if $f = g$, then they are the same arrow!
> Draw visual...
> ![[SameArrow.png|SameArrow.png]]

> [!tip] Theorem 2: Commutativity
> Given 2 arrows in a category, $f, g$, which are directed arrows where the $cod f = dom g$. Our diagram becomes commutative if there exists and arrow, call it $g \circ f$ where $dom (g \circ f) = dom f$ and $cod (g \circ f) = cod g$
> ![[Commutativity.png|Commutativity.png]]
> 

> [!note] Terminology
> In mathematics, we often call these arrows "morphisms". It comes from greek to denote meaning shape/form
> https://www.merriam-webster.com/dictionary/-morphism


> [!info] Monic arrows and Monomorphism
> A Monic arrow is an arrow $h$ such that when given two arrows $f_1, f_2$ with the equality $f_1 \circ h = f_2 \circ h\Rightarrow f_1 = f_2$. In other words, $m$ is left cancellable (just think that post-composition of m preserve equality)
> ![[Pasted image 20240406231740.png|Pasted image 20240406231740.png]]
What this picture is basically saying is that whenever we have 2 arrows that are the same, we can construct their composition arrows, and if they are the same by precomposing h, then the original functions are the same!

> [!info] Epi arrows and Epimorphisms
> A epi arrow is an arrow $h: a \to b$ such that when given two arrows $f_1, f_2 : d \to a$ with the equality $h \circ f_1 = h \circ f_2\Rightarrow f_1 = f_2$. In other words, $h$ is right cancellable (just think that post-composition of m preserve equality)
> Excercise : Draw the rest of this diagram:
> ![[Pasted image 20240407093754.png|Pasted image 20240407093754.png]]

# Hard Example:
> [!info] Metacategory
> A metacategory is a metagraph with 2 new operations :
> 1) Identity : for each object a, there is an arrow $id_a = 1_a : a \to a$
> 2) Composition: For each pair $(g, f)$ of arrows where $dom g = cod f$, an arrow $g \circ f$ is called their composite with $g \circ f : dom f \to cod g$ with the following operation :
> ```tikz 
> \usepackage{tikz-cd}
> \begin{document}
> 	\begin{tikzcd} 
> 		& b \\ \\ a && c 
> 		\arrow["f", from=3-1, to=1-2] 
> 		\arrow["g", from=1-2, to=3-3] 
> 		\arrow["g \circ f"', from=3-1, to=3-3] 
> 	\end{tikzcd}
> \end{document}
> ```
> The following operations give consequence to the following axioms
> 1) Law of Associativity
> > Given objects and arrows in the configuration : $a \xrightarrow{f} b \xrightarrow{g} c \xrightarrow{h} d$, it has the following relation: $$\color{red}{k \circ(g\circ f)} \color{white}{=} \color{blue}{(k \circ g) \circ f}$$ Visually its the following diagram:
> > ```tikz
> > \usepackage{tikz-cd}
> > \begin{document}
> > \begin{tikzcd} a && d \\ \\ b && c \arrow[color={blue}, "f"', from=1-1, to=3-1] \arrow["g"', from=3-1, to=3-3] \arrow[color={red}, "h"', from=3-3, to=1-3] \arrow["h \circ(g\circ f) = (h \circ g) \circ f", from=1-1, to=1-3] \arrow[color={red},"{g \circ f}"{description, pos=0.2}, from=1-1, to=3-3] \arrow[color={blue}, "{h \circ g}"{description, pos=0.2}, from=3-1, to=1-3] \end{tikzcd}
> > \end{document}
> > ```
> 2) Law of Unity
> > For all arrows $f:a\to b, g:b\to c$ composition with the identity arrow $1_b$ gives the following: $$f \circ 1_b = f \quad 1_b \circ g = g$$ Pictorially, its :
> > ```tikz
> > \usepackage{tikz-cd}
> > \begin{document}
> > \begin{tikzcd} a && b \\ \\ && b && c \arrow["{1_b}"', from=1-3, to=3-3] \arrow["f"', from=1-1, to=3-3] \arrow["f", from=1-1, to=1-3] \arrow["g", from=1-3, to=3-5] \arrow["g"', from=3-3, to=3-5] \end{tikzcd}
> > \end{document}
> > ``` 
> > By axiom 1, all objects in a metacategory include the identity, and are uniquely determined by property 2!
> > For the sake of succinctness, we will denote the identity : $1_b = b = Id_b$ where $b: b \to b$
>
> > [!example] Sets Theory
> > Sets can be built using metacategories. 
> > 1) Objects can be interpreted as sets 
> > 2) Functions between sets can be interpreted as arrows $$f:A \to b \iff A \xrightarrow{f}B$$, where $x = domf, Y = codf$.
> > 3) Identity and composition: are the same
> > 4) the rule $r : x \to fx$ which is defined by a suitable ordered pair $(x, fx)$. (While we need more theory to truly develop the structures of sets, the idea of mapping sets with arrows is neccessary for a meta category!)
> > > Lots of text include the following: $fx = f_x = f(x)$, we will use $fx$ for the remainder of the text
> > 6) For any set $S$, we can define the assignment $s \mapsto s$ as the identity rule : $1_S$. which is the identity function for all $s \in S$
> > 7) Inclusion or Insertion function: Suppose S is a subset of Y, then the functions $S \to Y$ is the inclusion
> > > Note: the identity and inclusion functions are completely different, unless $S = Y$
> > 7) Composite Function: Let $f:X\to Y$ and $g:Y\to Z$, then the composition is the same as $g \circ f$ where $(g \circ f)x = g(fx)$
> 
> > [!example] Others
> > Groups use Homomorphisms, Topological Spaces use Homeomorphisms
> > The arrows of any meta-category are called morphisms. Morphism from greek etymology means form/shape. In other algebraic structure, homomorphism usually means "one form" or often "structure preserving"!

## Exercise: arrows-only metacategories:

> [!note] Arrow-Only Categories
> Consider a category C without any objects and only arrows with the following properties
> 1) There are certain ordered pairs $(g, f)$ denoted as composable pairs
> 2) There is an operation that assigns every composable pair $(g, f)$ to an arrow $g \circ f$
> > In other words, we say $g \circ f$ is defined when $(g, f)$ is a composable pair
> Using this construction we are able to fully show that each axiom of a meta-category holds
>
> > [!example] Arrows Only Meta-Category Axioms
> > 1) Composite : The composite $h \circ (g \circ f)$ is defined if and only if the composite $(h \circ g) \circ f$ is defined. (This gives rise to the triple composite $h \circ g \circ f$)
> > > the triple composite $h \circ g \circ f$ is defined if and only if the composites of $h \circ g$ and $g \circ f$ are defined
> > 2) Identity: We can define the identity of C as an arrow $e$ such that $f \circ e = f$ whenever $f \circ e$ is defined, and $e \circ g = g$ whenever $e \circ g$ is defined!
> > > Using both part 1) and part 2, given any arrow $g$ in the category, there exists an arrow $e, e'$ such that $e' \circ g$ and $g \circ e$ are defined
>
> One thing to note is the uniqueness of identities. The identity rule ensures that the $e$ and $e'$ are unique and for each arrow g, we have a domain of $e$ and a codomain of $e'$
> 
> >[!tip] Theorem 2) Arrows-Only Categories Construction
> >Given a Meta category C with objects and Arrows, then using only its arrows and compistion above, we can construct a meta-category.
> >
> > Conversely, An Arrows-only category, meta-category satisfies the object-arrows axioms when the identity arrows are taken as objects

> [!tip] Prove Theorem 2:

# Application

So why did we just spend 15 minutes learning about categories. ITS BECAUSE THE STUDY OF MATHEMATICS IS JUST THE STUDY OF A SPECIFIC CATEGORY

Given two algebraic obejcts: X, Y

```tikz
\usepackage{tikz-cd}
\begin{document}
	\begin{tikzcd} 
	&&&& {Iso(X, Y)} 
	\\ 
	{Fun(X, Y)} && {Hom(X, Y)} &&&& {Aut(X)} \\ &&&& {End(X)} 
	\arrow["Preserves", hook, from=2-1, to=2-3] 
	\arrow["Structure"', hook, from=2-1, to=2-3] 
	\arrow["{bijective:\varphi }", hook, from=2-3, to=1-5] 
	\arrow["{Y=X}"', hook, from=2-3, to=3-5] 
	\arrow["{Y=X}", hook, from=1-5, to=2-7] 
	\arrow["{bijective:\varphi }"', hook, from=3-5, to=2-7] 
	\end{tikzcd}
\end{document}
```
- That's cool, because homomorphisms need not need to have a concept of injectivity or subjectivity!


- Calculus : Continuous functions from $X \to Y$
- Statistics: Continuous or discrete functions over $[0, 1]$, where the sum of the functions = 1
- Electrical Engineering : They study how electricity moves, and those are just continuous functions : (Fascinatingly enough, you will construct fourier Series to simulate electrical current because they are just a composition of sin and cos. GUESS WHAT, SIN and COS are continuous over $\R$)
- - An example, is linear equations. Solutions to linear equations are just $Hom_F(X, Y)$. Where the group structure is Vector spaces over a field $F$