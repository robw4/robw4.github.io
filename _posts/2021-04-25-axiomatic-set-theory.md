---
layout: post
author: robw
title: Axiomatic Set Theory
abstract: "During the first lockdown, with more free time on my hands, 
          I began to think a little more philosophically
          about the foundations of mathematics. In particular how can we know for sure that maths is correct?
          I discovered that at the start of the 20th century this was a question that an enormous amount of time and effort was devoted to trying to answer.
          Of the solutions proposed, the work of Zermelo and Fraenkel alongside the axiom of choice, commonly abbreviated to ZFC, remains one of the most complete answers to date. 
          In this post I begin by looking at why ZFC is necessary, what it is, how it might be used to ground many of the important
          foundations of mathematics today."
numbered: true
tags:
    - Maths
    - Research
    - Set Theory
    - Axioms
    - Goedel's Incompleteness Theorem
---



## Naive Set Theory
### Axiomatic Definition
The foundations of mathematics lie in a set of statements that we
 are happy to accept as true. Let's start with a fundamental observation:
  
> "the world is full of different things and that different things can be grouped together" 

In mathematics, this observations is encoded in our idea of _sets_
. In defining the notion of a mathematical set lets try and make as few assumptions as possible:

A1 Equality
: "Any two groups are the same if they contain the same things". This allows us to define what we mean by $A=B$

A2 Grouping
: "Any things that we can conceive of that satisfy a particular property can be grouped together": That is anything we can perceive we can regard as a thing and provided we can conceive of it it can be grouped. For example we could think of a set of "foods" as corresponding to "all things that are edible".

### Consequences
These are *axioms*: a set of assumptions that are assumed true from which everything else follows. In this case:

- **Different things can belong to more than one group** 

    We can comprehend an apple both as satisfying the condition "comes from a plant" and "is a food" (as well as "being a thing") 
    therefore both groups must exits and and it follows that each thing can be long to more than one group.
 
- **All things that are not A must be something else**  
    
    We could quite legitimately think about the set of all things that are not in $A$. This is a perfectly valid statement. 
    And implies that everything else that is not $A$ must be its own set. We refer to this set $A'$ as the *complement* of $A$.

- **A set can contain no things** 
    
    Lets think about defining a set $C$ which contains all of the elements of $A$ which are also in the set $B$. 
    In the case when $B$ does not contain any things found in $A$ then $C$ must now contain no things. In this case $C$ is an *empty set*.

- **All things are things**
    
    This implies that there must be a group containing all things which is referred to as the *universal set*.

### Russel's Paradox
Naive set theory on the surface appears to provide a powerful framework for reasoning logically about sets relying on two very intuitive axioms that most people would be happy to accept as true.

Unfortunately, for the formulation above several contradictions arise. 
One of the most famous was discover by Bertrand Russel and arises if we consider "the set of all sets that are not members of themselves".
This is a perfectly legitimate definition satisfying both axioms (1) and (2). 
But here is the problem... 
- if A is not a member of itself, then it must contain itself. 
- but it it contains itself then it invalidates its own definition. 

This results in a *paradox*; a statement that appears to be both true and false at the same time. That is, any statement that is written based on the set of base assumptions must be either true or false. 

#### Principle of Logical Explosion
So why is this a problem? 
In logic the *principal of explosion* says that any statement can be proven as true by proving that it is not false and forms one of the foundations for logical reasoning. 
Equivalently it can be stated as, "If it is not false then it must be true" or even more simply "statements can either be true or false". 
Paradoxes are worrying because they imply a statement which can be seen as neither true nor false. 
In order to be compatible with the principle of explosion a system needs to be *consistent*.

#### A Crisis at the Heart of Mathematics

The existence of paradoxes like the one above calls into question the very meaning of true and false for the systems of sets we have defined above. 
And everything else we derive from it. 
As much of the foundation of maths rests on the existence of sets this is very worrying indeed! 
This sparked a crisis in mathematics at the turn of the 20th century and led to the [Hilbert programme](https://en.wikipedia.org/wiki/Hilbert%27s_program); a challenge to the mathematical world to sure up the foundation of modern mathematics.

## ZFC Set Theory
Zermelo-Franco set theory along with the axiom of choice (ZFC) is one of the most complete approaches proposed to meet this challenge.
The central observation here is that paradoxes like Russel's arise from too general a definition of sets.
In shoring up the foundations of modern mathematics, we must forgo the notion of the _universal set_, instead insisting that only sets satisfying particular properties are allowed to exist.

For this to work, we now need to define the set of rules that dictate which sets are okay, ideally using as few and as un-restrictive rules as possible, so as to maintain a sufficiently rich theory to describe everything in modern mathematics without contradiction or paradox. 

### Axiomatic Definition
In ZFC the following axioms are proposed to this end:

ZF1 Extensionality (Equality)
: "Any two groups are the same if they contain the same things"

ZF2 Empty Set
: "The empty set exists". The set containing no things $\varnothing = \\{ \\}$ is a legitimate set and represents the base element of a set.

ZF3 Pairing
: "We can join any two sets together to make another". For any two sets $A$ and $B$ there exists a set $C=\\{A, B\\}$ containing both $A$ and $B$". That is we can always make a third distinct set from two others by making them elements of a set. 
The statement says nothing about $A$ and $B$ representing different sets. Indeed, $\\{A, A\\}$ is a legitimate paring. This set contains only one element $A$ however and is referred to as a *singleton*. 
This in combination with the existence of an empty set allows us to define new sets as $\\{\varnothing, \varnothing \\} = \\{\varnothing\\}$. Note that $\\{\varnothing\\}$ is not the same as $\varnothing$; it is a set containing a single empty set. 
We could repeat this process indefinitely defining an infinite number of unique elements. However, each set can currently only have two elements.

ZF4 Power Sets
: "For every A there exists a set which contains all the subsets of $A$"  This is referred to as the power set of $A$ and is written as $\mathcal{P}(A)$. For example the power set of $\{x, y, z\}$ is $$\mathcal{P}(\{x, y, z\}) = \{\{\}, \{x\}, \{y\}, \{z\}, \{x, y\}, \{x, z\}, \{y, z\}, \{x, y, z\}\}$$.  Note that the power set will always contain the empty set $\varnothing = \{ \}$; whilst $\varnothing$ might not be a *member* of the set it is always a subset. Combining the empty set, with paring and the repeated application of the power set law we are now able to define an infinite number of sets with a finite number of elements $$\mathcal{P}(\varnothing) = \{\varnothing\} \quad \mathcal{P}(\{\varnothing\})=\{\varnothing,\{\varnothing\}\} \quad \mathcal{P}(\{\varnothing,\{\varnothing\}\}) = \{\varnothing,\{\varnothing\},\{\{\varnothing\}\},\{\varnothing,\{\varnothing\}\}\}$$

ZF5 Unions
: "For every set A there exists a set who's elements are the union
 of all the elements of A". This is written as $\cup A$. For
  example, $$\cup\{\{x\}, \{y\}, \{z\}, \{x, y\}, \{x, z\}, \{y, z
  \}, \{x, y, z\}\} = \{x, y, z\}$$. Once again the union operator
   allows us to generate sets with more than two elements after the
    application of (3) and (4). For example, $\cup \\{\\{a, b
     \\}, \\{c, d\\}\\} = \\{a, b, c, d\\}$. The idea of unions and
      power sets are need in conjunction in order to define a sufficiently rich set of sets.

ZF6 Infinity
: "It is okay to have a set with an infinite number of members" Using the axioms above we are already in a position to define an infinite number of sets. But it would be nice to be able to group them in a single set. This is allowed by the axiom of infinity.

ZF7 Regularity
: "Every non empty set $x$ contains a member $y$ which such that $x$ and $y$ are *disjoint* sets". This is admittedly quite a difficult sentence to parse. 
It is the condition needed to ensure that chains such as $x \in \ y \in z \in x$ are prohibited. A consequence of this axiom is also that no set may contain itself $x \in x$ a atatement essential for avoiding Russel's paradox.
In fact it is not strictly necessary to prove many mathematical results. But its inclusion in many cases significantly reduces the complexity of proofs and can thought of as enabling the central process of ZF set theory. 
Namely, enabling ever more complex sets to be constructed from simpler ones.

ZF7 Replacement
: "If we can define a function $f$ consistent with our system and mapping each element in one set to elements in another then the set the function maps must exist!" This is referred to as the axiom of replacement schema as each
element of our starting set $A$ can be thought of as being
replaced by our function $f$ to produce $B$. It is
referred to as a _schema_ as it must be stated for every possible
function $f$. It can be viewed as a more restrictive form of the second axiom proposed in the Naive case.

C Choice
: Informally put, the axiom of choices says that given any collection of bins, each containing at least one object, it is possible to make a selection of exactly one object from each bin, even if each bin contains an infinite number of objects.
If each bin is finite then it is always possible to define a rule; namely select the smallest element. Even if each bin contained an infinite number of natural numbers then this would still be a legitimate choice function. 
However, if we instead consider an infinite number of real numbers a legitimate choice is no longer defined. There is no distinguishable feature over which we could make a choice. At this point we must invoke the axiom of choice. 

#### Comprehension vs Replacement
Note, the axiom of replacement is similar to another axiom often included in ZF set theory referred to as the the _Axiom Schema of Comprehension_. 
The [wikipedia articles](https://en.wikipedia.org/wiki/Axiom_schema_of_specification) gives a good discussion about the differences between the two. 
It turns out that the axiom schema of comprehension can be derived from the axiom schema of replacement alongside the existence of the empty set and it is often emitted from modern statements of ZF set theory as a result.

#### Choice
The axiom of choice was somewhat controversial and took a while to be accepted by the mathematics community. It is perhaps better understood through an analogy coined by Betrand Russel: 

>"for any (even infinite) collection of pairs of shoes, one can pick out the left shoe from each pair to obtain an appropriate selection; this makes it possible to directly define a choice function. 
For an _infinite_ collection of pairs of socks (assumed to have no distinguishing features), there is no obvious way to make a function that selects one sock from each pair. 
At least, not without the axiom of choice, which always allows you to say 'choose one sock from each pair'"

When combined with ZF the theorem is referred to as ZFC and remains the most widely accepted, complete, and well studied theorem to date.

### Constructions
So far these axioms are pretty abstract. To see how and why they might be useful in this section several important mathematical objects will be constructed using only the axioms proposed above. We will start with the definition of the ordered pair.
This will allow us to define the natural numbers, the integers, rationals and finally the reals. These sets and their properties represent key foundation elements of mathematics which underpins much of modern mathematics. Throughout, the approach to construction is similar. 
We begin with a set of simpler entities and use these to generate the next level of complexity.

#### Ordered pairs $(x, y)$
Perhaps one of the most basic ideas we rely on in mathematics is the idea of ordering; that one thing comes before another. 
Using the axioms above we are able to formally define this notion through the definition of an _ordered pair_  written as, 

  $$(x, y) = \{x ,\{x, y \} \}$$
  
To see which element of the set comes first we check to see if each element in the set contains the other. 

#### The Natural Numbers $\mathbb{N}$
What is so special about natural numbers $0, 1, 2, 3, ....$? Perhaps the most glaring obvious property of natural numbers is that they are ordered. 
That is we can say $0$ is less than $1$ is less than $2$ and so on! We write this (and similar statements) more succinctly by defining the comparison operators greater than $>$ and less than $<$. This allows us to write $0 < 1 <2$. 

The axioms defined above provide us with an elegant way of defining the natural numbers, alongside their order. 
We represent each number as a particular set. We start by considering $0$ to be the empty set $0 = \varnothing$. 
After this we make each number the set of all the numbers that came before it. 
This gives:

$$0 = \varnothing$$ 

$$1 = \{0\} = \{\varnothing \}$$ 

$$2 = \{0, 1\} = \{\varnothing,\{\varnothing\} \}$$ 

$$3 = \{0, 1, 2\} =  \{\varnothing,\{\varnothing\} ,  \{\varnothing,\{\varnothing\} \}$$ 

$$\vdots$$

As a result of the infinity axiom we can also group these numbers together into a single set, the set of natural numbers $\mathbb{N} = \\{0, 1, 2, ... \\}$.

So why is this definition useful? Just as for the ordered pair, it allows us to concretely define what we mean by ordering. 
We can check whether any number is bigger than another by seeing if that number is a member. 
For example if we wanted to check whether a number $3$ is less than $100$ we simply check whether $3$ is in $100 = \\{1, 2, 3, ..., 99\\}$. 

Through the inherent ordering of the natural numbers we can see that every number follows another. 
The successor $s(x)$ of each number $x$ is the set $x \cup \\{x \\}$. For example the successor of 
$1 = \\{0\\} = \\{\varnothing \\}$ is given as 

$$s(1) = 1 \cup \{1 \}  = \{\varnothing \} \cup \{\{\varnothing \}\} = \{\varnothing,\{\varnothing\} \} = 2$$
 
Using the idea of a successor we have just defined we are able to define the basic arithmetic operations:

- __Addition $(+)$:__ 
	1. $x + 0 = x$
	2. $x + s(n) = s(x +n)$
- __Multiplication $(\times)$__: For each number $x$,
	1. $x \times 1 = x$
	2. $x \times s(n) = (x \times n) + x$
- __Subtraction $(-)$__: For each number $x$,
	1. $x - x = 0$
	2. $s(x) - n = s(x -n)$

To see that these rules do in deed give us the answers that we would expect lets consider adding $4$ to $3$. We do this by following rule (2) recursively until we end up at a rule (1) so that,

$$\begin{aligned} 4+3 &=4+s(2) \\ &=s(4+2) \\ &=s(4+s(1)) \\ &=s(s(4+1)) \\ &=s(s(4+s(0))) \\ &=s(s(s(4+0))) \\ &=s(s(s(4))) \\ &=s(s(5)) \\ &=s(6) \\ &=7 \end{aligned}$$

which we can see gives us the right answer. 
A key property of addition is that the order with which we add two numbers together does not matter. 
To check that this is the case consider adding $3$ to $4$ using the same rules. 
This will still give us $7$! For additional examples for multiplication and subtraction see [here](https://link.springer.com/content/pdf/bbm%3A978-94-009-2213-6%2F1%2F1.pdf).

Unfortunately, $a - b$ is only defined when $a \geq b$ for the natural numbers (using our definition as greater than as $a \notin b$). We will revisit this shortly!

#### The Ordinals
The set $\omega = \\{0, 1, 2, ... \\}$ is referred to as the [first
 infinite ordinal](https://en.wikipedia.org/wiki/Ordinal_number). Intuitively the arithmetic operations do not stop once we reach $\omega$. We can still think of doing something like  $\omega + 1$. The result is still infinite but we would expect it to be bigger than $\omega$. Likewise we could think about $\omega \times \omega$ and $\omega^\omega$. We are also able to write down similar relations for each of these terms. These result can be thought of as generalising the idea of performing operations on ordered sets to infinite sized sets. Collectively they are referred to as ordinal arithmetic. However, these operations do not always work as we might expect. For example $\omega + 1 \neq 1 + \omega$. A story for another time!

#### The Integers $\mathbb{I}$
The set of _integers_ $\mathbb{I}=\\{..., -\mathsf{2}, -\mathsf{1
}, \mathsf{0}, \mathsf{1}, \mathsf{2}, ...\\}$ allows us to write $
\mathsf{3} - \mathsf{7} = -\mathsf{4}$. Commonly we think of the integers $\mathbb{I}$ as the natural numbers and their negatives, so that the integers *contain* the natural numbers. However, in defining the integers we are better off thinking about them as an entirely new set of things. To make this perfectly clear $3$ will represent the natural number $3$ whilst $\mathsf{3}$ will represent an integer (in sans serif font). After this we can go back to thinking of the positive integers (and zeros) as the natural numbers.

As for the natural numbers, we now need to define the integers in terms of sets. Armed with the idea of an ordered pair, each integer is represented _as a pair of natural numbers_ $(a, b)$ who's difference $a - b$ can be thought of as representing the value of the integer. For example we write $\mathsf{4} = (7, 3)$ and $-\mathsf{4} = (3, 7)$.

As $$4 = 8 - 4 = 6 - 2 = 10 - 6 = ....$$ in defining integers in this way, each integer is now equivalently represented by multiple sets. For example $4 = (8, 4)$, $4 = (6, 2)$ and $4 = (10, 6)$. Whilst this means the sets $(8, 4)$ and $(6, 2)$ are equivalent in the sense of integers they are *not* in the sense of sets: $(8, 4)$  and $(6, 2)$ have different elements. In order to define sets as being equivalent we need to:
1. Disambiguate equivalence in terms of sets from equivalence in terms of integers. We do this by defining the equivalence relation $\sim$. This allows us to write $(8, 4) \sim (6, 2)$ whilst maintaining $(8, 4) \neq (6, 2)$.
2. Decide a condition which makes two sets equivalent in terms of integers. Two pairs of natural numbers represent the same integer if  $(a, b) \sim (c, d)$ if $$a + d = b + c$$. When $a \geq b$ and $c \geq d$ this is the same as saying $a - b = c - d$ and when $a < b$ and $c < d$ the same as $b - a = d - c$.

So far our choice to represent integers in this way seems fairly arbitrary. So why bother? It allows us to define integer arithmetic in terms of only natural number arithmetic. Given integers $\mathsf{x} = (a, b)$ and  $\mathsf{y} = (c, d)$ we can define the integer arithmetic operations as:
- __Ordering__  $\mathsf{x} > \mathsf{y}$
	
	$$(a, b) > (c, d) \text{  if  } a + d > c + b$$

- __Addition__  $\mathsf{x} + \mathsf{y}$ 
	
	$$(a, b) + (b, c) = (a + c, b + d)$$

- __Subtraction__ $\mathsf{x} - \mathsf{y}$

	$$(a, b) - (c, d) = (a, b) + (d, c) = (a + d, b +c)$$

- __Multiplication__ $\mathsf{x} \times \mathsf{y}$

	$$(a, b) \times (c, d) = \big((a \times c) + (b \times d), (a \times d) + (b \times c)\big)$$

For example:
- $\mathsf{3} > \mathsf{1}$ as $\mathsf{3} = (6, 3)$, $\mathsf{1} = (2, 1)$ and $6 + 1 > 2 + 3$
- $\mathsf{0} > -\mathsf{3}$ as $\mathsf{0} = (4, 4)$, $-\mathsf{3}=(2, 5)$ and $4 + 5 > 2 + 4$.
-  $\mathsf{3} + \mathsf{2} = \mathsf{5}$ as $(6, 3) + (4, 2) = (10, 5) = \mathsf{5}$

For more see [here](https://link.springer.com/content/pdf/bbm%3A978-94-009-2213-6%2F1%2F1.pdf)

#### The Irrational Numbers $\mathbb{Q}$
In the same way integers allowed us to answer questions like _"What must we add to 7 to give us 4?"_ the rational numbers allow us to ask _"How many lots of 7 do we need to make 4?"_. They allow us to define an inverse for multiplications for all the integers. We do this by considering ordered pairs, this time of integers instead of natural numbers. We can think of $(\mathsf{7}, \mathsf{3})$ as representing the fraction $\frac{7}{3}$. As $$\frac{7}{3} = \frac{70}{30} = \frac{21}{9}=...$$, we say that two rational numbers are equivalent $(a, b) \sim (c, d)$ if $a \times d = c \times b$.   Using this representation it can be shown that the arithmetic operations on natural numbers can all be defined:
- __Ordering__  $\mathsf{x} > \mathsf{y}$
	
	$$(a, b) > (c, d) \text{ if } a \times d > c \times b$$

- __Addition__  $\mathsf{x} + \mathsf{y}$ 

	$$(a, b) + (b, c) = (a \times d + c \times b, b \times d)$$

- __Subtraction__ $\mathsf{x} - \mathsf{y}$
	
	$$(a, b) - (c, d) =  (a \times d - c \times b, b \times d)$$

- __Multiplication__ $\mathsf{x} \times \mathsf{y}$
	
	$$(a, b) \times (c, d) = (a \times c, b \times d)$$

- __Division__  $\mathsf{x} / \mathsf{y}$

	$$(a, b) / (c, d) = (a \times d, c \times b)$$

#### Functions $f(x)$
Numbers are not very useful unless we can do something with them. In defining addition and subtraction for the natural numbers we defined a set of rules which when followed allowed us to take two numbers as input and generate a third. This is an example of what we refer to as a *function*.

By using the idea of ordered pairs we are able to **define what a function is in terms of only sets**. A function which takes in two inputs is thought of as taking in an ordered pair. This allows us to define which input is first and which input is second. 
Of course for addition we don't care about the order but for other functions this might not be the case. 

We can think of addition as taking the ordered pair $(3, 4)$ as input and producing $7$ from it. It also produces $2$ from $(1, 1)$ and $101$ from $(99, 2)$ as well as from $(2, 99)$. 
We can represent each of these cases also as an ordered pair where the first element is always the input and the second element is always the output for example, $((3, 4), 7)$ represents the case $3 + 4 = 7$. 
In this sense the function addition is thought of as the set of all ordered pairs of its inputs and outputs. For addition we have,

$$f_{+} = \{\big((0, 0), 0\big), \big((0, 1), 1\big), \big((0, 2), 2\big), ..., \big((1, 0), 1\big),  \big((1, 1), 2\big), \big((1, 2), 3\big), ...\}$$

Any two functions which produce the exact same outputs from all of the exact same inputs are exactly the same function, or two functions will be the same if $f_1 = f_2$. 

#### Intersections $\cap$, Complements $\cup$, Cartesian Product $\times$
As a result of the _axiom schema of replacement_ some particularly useful sets can be constructed:
- $A \cap B$: The set of all elements that are in $A$ and in $B$ referred to as "A _intersection_ B"
- $A / B$: The set of all the elements that are in $A$ once the elements that are in $B$ have been removed referred to as "A _complement_ B".
- $A \times B$: The set of all pairs $(a, b)$ of elements where $a$ is in $A$ and $b$ is in $B$ "The _cartesian product_ between $A$ and $B$" 

#### The Real Numbers $\mathbb{R}$
Not all numbers can be expressed as fractions. To see that this is the case lets consider representing fractions as decimals. 
We can think of the decimal numbers as a short-hand way of writing

$$0.078125 = 0 \frac{1}{1} + 0  \frac{1}{10} +  7  \frac{1}{100} + 8  \frac{1}{1000} + 1  \frac{1}{10000} + 2  \frac{1}{100000} + 5  \frac{1}{1000000}$$
 
Two cases arise for fractions expressed in this way. Either we can express a sequence in a finite number of terms (as above) or their will be finitely many terms followed by a term that will repeat itself in a regular pattern for example $1 / 3 = 0.333...$ or $1 / 99 = 0.01010...$. But what happens if we consider adding digits to a decimal indefinitely and never forming a repeated pattern. For example,

$$0.078125136729420100357399387401377382...$$

Each time we add a decimal point we can think of adding an ever increasingly small part to the number $0.078125$. 
Expressing this slightly differently we can think of the number $0.07812513...$ as corresponding to a sequence $0, 0.0, 0.07, 0.0781, 0.07812, ...$ where the difference between elements becomes arbitrarily small as the sequence progresses. 
Sequences of this kind are referred to as [Cauchy Sequences](https://en.wikipedia.org/wiki/Cauchy_sequence) and in the limit can be thought of as converging to a single fixed value. In this way we can think of each real number as a unique cauchy sequence!

In order to represent real numbers in this way we need to construct a sequence from sets. We can think of a sequence of a set of pairs between the natural numbers $(0, 1, 2, ..)$ and the rational numbers $\mathbb{Q}$. For example the sequence  $0, 0.0, 0.07, 0.07, 0.0781, ...$ can be thought of as a set $$\{(0, 0), (1, 0.0), (2, 0.07), (3, 0.078), (4, 0.0781), ... \}$$. Sets of this kind can be generated from the axioms we have defined so far as follows:
1. First we generate all possible pairs of natural and rational numbers using the cartesian product $\mathbb{N} \times \mathbb{Q}$ we just defined.
2. From this set of pairs we choose a set of pairs which correspond to a valid Cauchy sequence such that their natural numbers ascend in terms of the natural number in each pair and their rational numbers become arbitrarily close to one another.
4. Repeat this process for all the possible sequences of elements in order to form the set of real numbers $\mathbb{R}$.

Steps 2 and 3 can be thought of as a function mapping the set $\mathbb{N} \times \mathbb{Q}$ onto the set of real numbers. As we know  $\mathbb{N} \times \mathbb{Q}$ already exists and the steps 2 and 3 can be carried out by using natural number and integer arithmetic to check which pairs are valid by the axiom of replacement the real numbers are therefore defined!

Once again we can define arithmetic operations on the real numbers by defining functions which take in one Cauchy sequence and produce another. It can be [shown](http://mathonline.wikidot.com/cauchy-sequences-of-real-numbers) that the sum, product, difference and cauchy sequences all result in cauchy sequences. In each case the operators are defined by summing over corresponding elements of the sequence. For example if $a = (1, 1.01, 1.0105, 1.01052, ...)$ and $b = (2, 2.7, 2.75, 2.758...)$ then $a + b = (3, 3.71,  3.7605,  3.76852)$.

## So Crisis Avoided?
### Solving Russel's Paradox
We have seen that ZFC set theory allows us to build increasingly
 complex mathematical ideas: starting with the idea of sets we were
  able to define the natural numbers, the integers, the rationals and the reals. Continuing, we might also derive imaginary numbers, continuity, vectors and in fact nearly all of modern day mathematics.  All while avoiding paradoxes like Russels, putting the foundation of mathematics on a much surer footing. Turn of the century mathematicians began to sigh a sigh of relief...

### Goedel's Incompleteness Theorem
Unfortunately, this relief was short lived. In 1931 Goedel published his famous "incompleteness theorem" which ensures that for any formal axiomatic system describing the arithmetic of the natural numbers there will be statements which are impossible to prove nor refute. This means that for ZFC there will be statements that are neither provable nor disprovable. An approach to overcoming this limitation is to add in whatever axioms are needed to make the unprovable statement provable. But this just kicks the can down the road; eventually, much like a game of wack a mole, another unprovable statement will appear. 

The first unprovable statement discovered for ZFC was the continuum hypothesis, and several others have been discovered since (eg. [incompleteness from finite trees and incompleteness from functions](https://plus.maths.org/content/picking-holes-mathematics)). The perhaps one upside is that the unprovable statements that have been discovered so far all seem to fall a long way from what we might consider as useful maths. The maths that we rely on to ensure the world continues to function as expected. For example the continum hypothesis is concerned with whether the infinity of the real numbers is greater than that of the natural numbers. Whilst it would be reassuring to have an answer to such a question, not being able to do so does not seem to have limited our understanding of the real world. And if we get to a point where we think it has become a limitation, we can always add in another axiom to see where that gets us. 

In some ways Goedel's hypothesis does not change much. All the results which were previously provable by the set of axioms we were previously willing to accept as true still remain valid; this still hinges on the axioms themselves being correct in the first place.
Regardless ZFC is a truly remarkable achievement of human perseverance and ingenuity.

## Appendix
### Useful Links and References
- Wikipedia
	- [Naive Set Theory](https://en.wikipedia.org/wiki/Naive_set_theory)
	- [Zermelo-Franenkel Set Theory](https://en.wikipedia.org/wiki/Zermelo%E2%80%93Fraenkel_set_theory)
	- [Russels Paradox](https://en.wikipedia.org/wiki/Russell%27s_paradox)
	- [Von Neuman Universe](https://en.wikipedia.org/wiki/Talk%3AVon_Neumann_universe)
		- An Interesting discussion on the role of SFD in reality
	- [Principle of Explosion](https://en.wikipedia.org/wiki/Principle_of_explosion)
	- [Sequence](https://en.wikipedia.org/wiki/Sequence#c_and_c0)
	- [Sequence Space](https://en.wikipedia.org/wiki/Sequence_space)
	- [Axiom Schema of Specification](https://en.wikipedia.org/wiki/Axiom_schema_of_specification)
	- [Cartesian Product](https://en.wikipedia.org/wiki/Cartesian_product)
	- [Cardinality](https://en.wikipedia.org/wiki/Cardinality)
	- [Real Number](https://en.wikipedia.org/wiki/Real_number)
	- [Ordered Pair](https://en.wikipedia.org/wiki/Ordered_pair)
- Quora
	- [A Good discussion on using ZFC to construct N, Z and Q](https://www.quora.com/How-can-I-prove-the-existence-of-the-real-number-set-based-on-the-ZFC-axioms-and-the-existence-of-N-Z-and-Q)
- Stack Exchange
	- [Representing Real Numbers as Sets](https://math.stackexchange.com/questions/62852/in-set-theory-how-are-real-numbers-represented-as-sets)
- Stanford Encyclopedia of Philosophy
	- [Set Theory](https://plato.stanford.edu/entries/set-theory/#AxiZFC)
- Good articles
    - [Further Discussion on Godels Theorem](https://www.scientificamerican.com/article/what-is-godels-theorem/).
	- [Searching for the missing truth](https://plus.maths.org/content/searching-missing-truth)
- Other
	- [Ohio-State lectures](https://www.asc.ohio-state.edu/pollard.4/680/slides/setssl.pdf)
    - [Brown University Lecture Series](https://www.math.brown.edu/reschwar/INF/handout1.pdf)
    - [Math Online - Cauchy Sequences of Real Numbers](http://mathonline.wikidot.com/cauchy-sequences-of-real-numbers)
    - [Bath University C196 Lecture Notes](https://people.bath.ac.uk/masnnv/Teaching/C196_7.pdf)
    - [Cauchys Construction of R](http://www.math.ucsd.edu/~tkemp/140A/Construction.of.R.pdf)
    - [Set Theory Definition of Numbers](https://link.springer.com/content/pdf/bbm%3A978-94-009-2213-6%2F1%2F1.pdf)


