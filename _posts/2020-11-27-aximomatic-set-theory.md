---
layout: post
author: robw
title: Axiomatic Set Theory
abstract:
image: /assets/images/electrical.jpg
numbered: false
---

## Naive Set Theory
The foundations of mathematics lie in a set of statements that we are happy to accept as true based on our own perception of the world. Let's start with our fundamental observation **"the world is full of different things and that different things can be grouped together"**. In defining the notion of a mathematical set lets try and make as few assumptions as possible:

1. __"Any two groups are the same if they contain the same things"__: This allows us to define what we mean by $A=B$
2. __"Any things that we can conceive of that satisfy a particular property can be grouped together"__: That is anything we can perceive we can regard as a thing and provided we can conceive of it it can be grouped. For example we could think of a set of "foods" as corresponding to "all things that are edible".

These are *axioms*: a set of assumptions that are assumed True from which everything else follows. In this case:

- **"Different things can belong to more than one group"**: We can comprehend an apple both as satisfying the condition "comes from a plant" and "is a food" (as well as "being a thing") therefore both groups must exits and and it follows that each thing can be long to more than one group.
- **"All things that are not A must be something else"**:  We could quite legitimately think about the set of all things that are not in $A$. This is a perfectly valid statement. And implies that everything else that is not $A$ must be its own set. We refer to this set $A'$ as the *complement* of $A$.
- **"A set can contain no things"**: Lets think about defining a set $C$ which contains all of the elements of $A$ which are also in the set $B$. In the case when $B$ does not contain any things found in $A$ then $C$ must now contain no things. In this case $C$ is an *empty set*.
- **"All things are things"**: This implies that there must be a group containing all things which is referred to as the *universal set*

Any group of things for which the above four statements are true is a set! The mathematical foundation for a set are simply statements which must be true and have nothing to do with the symbols we use to describe them. So why bother with symbols? Symbols allow us to be both succinct and precise in what we are saying. To see this lets consider De Morgans law which states:

De Morgans Law
: "the set of all things that are not in A or B is equal to the set of all things that are not in A and not in B"

I think you will agree that this is quite a mouthful. It is also ambiguous: does the "not" in  "not in A or B" apply just to the A or to both A and B for example? In most cases we can imply the meaning of a sentence from the context. We are happy to take a leap of faith! But in building ever more sophisticated logical statements about the world this will no longer suffice. Instead we introduce a new language which is stricter and more precise. In order to express De Morgans law for example we will need to introduce:
- Equality $A=B$ - "A is the same thing as B"
- The complement $A'$ - "All things that are not in A"
- A intersection B $A \cap B$ - "The set of all things that are both in A and B"
- A union B $A \cup B$  - "The set of all things that are in A or B"

To get around this ambiguity brackets are used when the order in which operations are carried out is ambiguous. For example $(a + b) \times c$ means we have to add $(a + b)$ first before multiplying it by $C$. Having introduced these symbols, de Morgans law becomes:

$$(A \cup B)' = A' \cap B'$$

For completeness, I am going to introduce several other symbols here which are useful when working with sets. Some of them I will be using later on as well:
- $A=B$: Equality. A is the same thing as B
- $A = \{\mathsf{red}, 1, 2, \mathsf{apple} \}$: A set of things
- $U$: The universal set to which all things belong
- $\emptyset$: The empty set containing no things
- $\mathsf{red} \in A$: red is in A
- $\mathsf{blue} \notin A$: blue is not in A
- $A \subset B$: A is a subset of B. All the elements of A are also in B
- $B \supset A$: B is a superset of A.
- $A'$: The set of all things that are not in A
- $A \cap B$: A intersection B. The set of all things that are both in A and B
- $A \cup B$: A union B. The set of all things that are in A or B
- $A / B$:  A complement B. The set of all things in A that are not in B
- $A \times B$: Cartesian Product. The set of all possible combinations of things in A and things in B
- $\mathcal{P}(A)$: The power set of A. The set of all subsets of $A$

## Russel's Paradox
Unfortunately, for the formulation above a contradiction arises. What if we define $A$ to be the set of all sets that are not members of themselves? This is a perfectly legitimate definition satisfying both axioms (1) and (2). But here is the problem...

If A is not a member of itself, then it must contain itself. But it it contains itself then it invalidates its own definition. This results in a *paradox*; it seems to both exist and not exist at the same time. So why is this a problem? In logic the *principal of explosion* says that any statement can be proven as True by proving that it is not False and forms one of the foundations for logical reasoning. Equivalently it can be stated as, "If it is not False then it must be True" or even more simply "statements can either be True or False".

Paradoxes are worrying because they imply a statement which can be seen as neither True nor False. The existence of this paradox calls into question the very meaning of True and False for the systems of sets we have defined above. And everything else we derive from it. As much of the foundation of maths rests on the existence of sets this is very worrying indeed! In order to be compatible with the principle of explosion a system needs to be *consistent*. That is, any statement that is written based on the set of base assumptions must be either True or False.

## ZFT Set Theory
The finding of paradoxes like Russel's sparked a crisis surrounding the foundations of mathematics and led to the development of different definitions of sets. The main idea here is to reformulate sets by adding in new axioms to avoid contradictions whilst simultaneously keeping the axioms as unrestrictive as possible. Of several theories proposed  Zermelo-Fraenkel (ZF) theorem is considered one of the most complete and goes some way to help eliminate the presence of inconsistencies. We start with these two base assumptions:

1. __"Any two groups are the same if they contain the same things"__
2. __"Any things already in a set that satisfy a particular property can be grouped together"__

This is similar to before but with the additional requirement that each thing we are grouping must first belong to a grouping. A natural consequence of (2) means that *the universal set cannot exist* as if it did then the set $\{x \in U  : x \notin x\}$ must also exist (by 2) which cannot as a result of Russel's paradox.

Whilst this is a clear win, we seemingly no longer have any things to group. The onus is now on us to define a sufficiently representative set of things (using just sets alone) before we can apply (2). To do this we need to add in some additional axioms:

3. __"The empty set exists"__: The set containing no things $\emptyset = \{ {} \}$ is a legitimate set and represents the base element of a set.
4. __"We can join any two sets together to make another"__: For any two sets $A$ and $B$ there exists a set $C=\{A, B\}$ containing both $A$ and $B$". That is we can always make a third distinct set from two others by making them elements of. a set. The statement says nothing about $A$ and $B$ representing different sets. Indeed, $\{A, A\}$ is a legitimate paring. This set contains only one element $A$ however and is referred to as a *singleton*. This in combination with the existence of an empty set allows us to define new sets as $\{\emptyset, \emptyset \} = \{\emptyset\}$. Note that $\{\emptyset\}$ is not the same as $\emptyset$; it is a set containing a single empty set. We could repeat this process indefinitely defining an infinite number of unique elements. However, each set can currently only have two elements.
5. __"For every A there exists a set which contains all the subsets of $A$"__:  This is referred to as the power set of $A$ and is written as $\mathcal{P}(A)$. For example the power set of $\{x, y, z\}$ is $$\mathcal{P}(\{x, y, z\}) = \{\{\}, \{x\}, \{y\}, \{z\}, \{x, y\}, \{x, z\}, \{y, z\}, \{x, y, z\}\}$$.  Note that the power set will always contain the empty set $\varnothing = \{ \}$; whilst $\varnothing$ might not be a *member* of the set it is always a subset. Combining the empty set, with paring and the repeated application of the power set law we are now able to define an infinite number of sets with a finite number of elements

        $$\mathcal{P}(\varnothing) = \{\varnothing\} \quad \mathcal{P}(\{\varnothing\})=\{\varnothing,\{\varnothing\}\} \quad \mathcal{P}(\{\varnothing,\{\varnothing\}\}) = \{\varnothing,\{\varnothing\},\{\{\varnothing\}\},\{\varnothing,\{\varnothing\}\}\}$$

6. __"For every set A there exists a set who's elements are the union of all the elements of A"__ This is written as $\cup A$. For example, $$\cup\{\{x\}, \{y\}, \{z\}, \{x, y\}, \{x, z\}, \{y, z\}, \{x, y, z\}\} = \{x, y, z\}$$. Once again the union operator allows us to generate sets with more than two elements after the application of (3) and (4). For example, $\cup \{\{a, b \}, \{c, d\}\} = \{a, b, c, d\}$. The idea of unions and power sets are need in conjunction in order to define a sufficiently rich set of sets.

Through the addition of these axioms we are now in a position to define an infinite number of sets, through the repeated application of (3) and (4) with the repeated application of (5) and / or (6). But these sets are so far pretty abstract. What do we mean by the set of a set of a set of nothing for example?

### Defining the natural numbers
What is so special about natural numbers $0, 1, 2, 3, ....$? Perhaps the most glaring obvious property of natural numbers is that they are ordered. That is we can say $0$ is less than $1$ is less than $2$ and so on! We write this (and similar statements) more succinctly by defining the comparison operators greater than $>$ and less than $<$. This allows us to write $0 < 1 <2$.  By agreeing on what this order is, we can say "there are 10 apples on the tree" and someone immediately knows this is more than $2$. The axioms defined above provide us with an elegant way of defining the symbols for the natural numbers, alongside their order, whilst at the same time remaining consistent. We represent each number as a particular set. We start by considering $0$ to be the empty set $0 = \varnothing$. After this we make each number the set of all the numbers that came before it. This gives:

$$0 = \varnothing$$ $$1 = \{0\} = \{\varnothing \}$$ $$2 = \{0, 1\} = \{\varnothing,\{\varnothing\} \}$$ $$3 = \{0, 1, 2\} =  \{\varnothing,\{\varnothing\} ,  \{\varnothing,\{\varnothing\} \}$$ $$\vdots$$

So why is this useful? It allows us to concretely define what we mean by ordering. We can check whether any number is bigger than another by seeing if that number is a member. For example if we wanted to check whether a number $3$ is less than $100$ we simply check whether $3$ is in $100 = \{1, 2, 3, ..., 99\}$. Through the inherent ordering of the natural numbers we can see that every number follows another. The successor $s(x)$ of each number $x$ is the set $x \cup \{x \}$. For example the successor of $1 = \{0\} = \{\varnothing \}$ is given as $$s (1) = 1 \cup \{1 \}  = \{\varnothing \} \cup \{\{\varnothing \}\} = \{\varnothing,\{\varnothing\} \} = 2$$. Using the idea of a successor we have just defined we are able to define the basic arithmetic operations:

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

which we can see gives us the right answer. A key property of addition is that the order with which we add two numbers together does not matter. To check that this is the case consider adding $3$ to $4$ using the same rules. This will still give us $7$! For additional examples for multiplication and subtraction see [here](https://link.springer.com/content/pdf/bbm%3A978-94-009-2213-6%2F1%2F1.pdf).

Unfortunately, $a - b$ is only defined when $a \geq b$ for the natural numbers (using our definition as greater than as $a \notin b$). We will revisit this shortly!

## Introducing Infinity $\infty$
We have defined an infinite number of a natural numbers. But it would be nice to be able to group them in a single set! Unfortunately the axioms allowed so far do not allow us to do this. In order to enable this we need to take another leap of faith by defining a new axiom:

7. __"It is okay to have a set with an infinite number of members__"

We are now in a position to define the set of all natural numbers $\mathbb{N} = \{0, 1, 2, ... \}$.

>The set $\omega = \{0, 1, 2, ... \}$ is referred to as the *first infinite ordinal*. Intuitively the arithmetic operations do not stop once we reach $\omega$. We can still think of doing something like  $\omega + 1$. The result is still infinite but we would expect it to be bigger than $\omega$. Likewise we could think about $\omega \times \omega$ and $\omega^\omega$. We are also able to write down similar relations for each of these terms. These result can be thought of as generalising the idea of performing operations on ordered sets to infinite sized sets. Collectively they are referred to as ordinal arithmetic. However, these operations do not always work as we might expect. For example $\omega + 1 \neq 1 + \omega$. A story for another time!

## Ordered pairs $(x, y)$
In defining the natural numbers we introduced the idea of ordering; if one number contains another then we know it must be larger. Grouping two sets together in this way is a neat way of defining relationships (not just ordering) between two things  and turns out to be very useful. An *ordered pair* of any two sets is written as, $$(x, y) = \{x ,\{x, y \} \}$$. To see which element of the set comes first we check to see if each element in the set contains the other.

## The integers $\mathbb{I}$
The set of _integers_ $\mathbb{I}=\{..., -\mathsf{2}, -\mathsf{1}, \mathsf{0}, \mathsf{1}, \mathsf{2}, ...\}$ allows us to write $\mathsf{3} - \mathsf{7} = -\mathsf{4}$. Commonly we think of the integers $\mathbb{I}$ as the natural numbers and their negatives, so that the integers *contain* the natural numbers. However, in defining the integers we are better off thinking about them as an entirely new set of things. To make this perfectly clear $3$ will represent the natural number $3$ whilst $\mathsf{3}$ will represent an integer (in sans serif font). After this we can go back to thinking of the positive integers (and zeros) as the natural numbers.

As for the natural numbers, we now need to define the integers in terms of sets. Armed with the idea of an ordered pair, each integer is represented _as a pair of natural numbers_ $(a, b)$ who's difference $a - b$ can be thought of as representing the value of the integer. For example we write $\mathsf{4} = (7, 3)$ and $-\mathsf{4} = (3, 7)$.

As $$4 = 8 - 4 = 6 - 2 = 10 - 6 = ....$$ in defining integers in this way, each integer is now equivalently represented by multiple sets. For example $4 = (8, 4)$, $4 = (6, 2)$ and $4 = (10, 6)$. Whilst this means the sets $(8, 4)$ and $(6, 2)$ are equivalent in the sense of integers they are *not* in the sense of sets: $(8, 4)$  and $(6, 2)$ have different elements. In order to define sets as being equivalent we need to:
1. Disambiguate equivalence in terms of sets from equivalence in terms of integers. We do this by defining the equivalence relation $\sim$. This allows us to write $(8, 4) \sim (6, 2)$ whilst maintaining $(8, 4) \neq (6, 2)$.
2. Decide a condition which makes two sets equivalent in terms of integers. Two pairs of natural numbers represent the same integer if  $(a, b) \sim (c, d)$ if $$a + d = b + c$$. When $a \geq b$ and $c \geq d$ this is the same as saying $a - b = c - d$ and when $a < b$ and $c < d$ the same as $b - a = d - c$.

So far our choice to represent integers in this way seems fairly arbitrary. So why bother? When define integers in this way can define integer arithmetic in terms of only natural number arithmetic. Given integers $\mathsf{x} = (a, b)$ and  $\mathsf{y} = (c, d)$ we can define the integer arithmetic operations as:
- __Ordering__  $\mathsf{x} > \mathsf{y}$
	-  $(a, b) > (c, d)$ if $a + d > c + b$
- __Addition__  $\mathsf{x} + \mathsf{y}$
	- $(a, b) + (b, c) = (a + c, b + d)$
- __Subtraction__ $\mathsf{x} - \mathsf{y}$
	- $(a, b) - (c, d) = (a, b) + (d, c) = (a + d, b +c)$
- __Multiplication__ $\mathsf{x} \times \mathsf{y}$
	- $(a, b) \times (c, d) = \big((a \times c) + (b \times d), (a \times d) + (b \times c)\big)$

For example:
- $\mathsf{3} > \mathsf{1}$ as $\mathsf{3} = (6, 3)$, $\mathsf{1} = (2, 1)$ and $6 + 1 > 2 + 3$
- $\mathsf{0} > -\mathsf{3}$ as $\mathsf{0} = (4, 4)$, $-\mathsf{3}=(2, 5)$ and $4 + 5 > 2 + 4$.
-  $\mathsf{3} + \mathsf{2} = \mathsf{5}$ as $(6, 3) + (4, 2) = (10, 5) = \mathsf{5}$
- $\mathsf{3} \times \mathsf{2} = 6$ as $\mathsf{3}.= (6, 3)$ and $\mathsf{2}.= (4, 2) = ((6 \times 4) + (3 \times 2), (6 \times 2 + 3 \times 4)) = (24 + 6, 12 + 12) = (30, 24) = \mathsf{6}$

For more see [here](https://link.springer.com/content/pdf/bbm%3A978-94-009-2213-6%2F1%2F1.pdf)

## The Irrational Numbers $\mathbb{Q}$
In the same way intergers allowed us to define answers questions like _"What must we add to 7 to give us 4"_ the rational numbers allow us to ask _"How many lots of 7 do we need to make 4"_. They allow us to define an inverse for multiplications for all the integers. We do this by considering ordered pairs, this time of integers instead of natural numbers. We can think of $(\mathsf{7}, \mathsf{3})$ as representing the fraction $\frac{7}{3}$. As $$\frac{7}{3} = \frac{70}{30} = \frac{21}{9}=...$$, we say that two rational numbers are equivalent $(a, b) \sim (c, d)$ if $a \times d = c \times b$.   Using this representation it can be shown that the arithmetic operations on natural numbers can all be defined:
- __Ordering__  $\mathsf{x} > \mathsf{y}$
	-  $(a, b) > (c, d)$ if $a \times d > c \times b$
- __Addition__  $\mathsf{x} + \mathsf{y}$
	- $(a, b) + (b, c) = (a \times d + c \times b, b \times d)$
- __Subtraction__ $\mathsf{x} - \mathsf{y}$
	- $(a, b) - (c, d) =  (a \times d - c \times b, b \times d)$
- __Multiplication__ $\mathsf{x} \times \mathsf{y}$
	- $(a, b) \times (c, d) = (a \times c, b \times d)$
- __Division__  $\mathsf{x} / \mathsf{y}$
	- $(a, b) / (c, d) = (a \times d, c \times b)$

## Functions $f(x)$
Numbers are not very useful unless we can do something with them. In defining addition and subtraction for the natural numbers we defined a set of rules which when followed was able to take two numbers as input and generate a third. This is an example of what we refer to in maths as a *function*.

By using the idea of an ordered pairs we are able to **define what a function is in terms of only sets**. A function which takes in two inputs is thought of as taking in an ordered pair. This allows us to define which input is first and which input is second. Of course for addition we don't care about the order but for other recipes this might not be the case.

We can think of addition as taking the ordered pair $(3, 4)$ as input and producing $7$ from it. But this isn't the only thing that addition can do. It is also able to produce $2$ from $(1, 1)$ and $101$ from $(99, 2)$ as well as from $(2, 99)$. We can represent each of these cases also as an ordered pair where the first element is always the input and the second element is always the output for example, $((3, 4), 7)$ represents the case $3 + 4 = 7$. In this sense the function addition is thought of as the set of all ordered pairs of its inputs and outputs. For addition we have,

$$f_{+} = \{\big((0, 0), 0\big), \big((0, 1), 1\big), \big((0, 2), 2\big), ..., \big((1, 0), 1\big),  \big((1, 1), 2\big), \big((1, 2), 3\big), ...\}$$.

Any two functions which produce the exact same outputs from all of the exact same inputs are exactly the same function, or two functions will be the same if $f_1 = f_2$.

It certainly seems intuitive that if we have a set, and can define a set of rules which are consistent with our axioms then we should be able to define a set $f$ in this way. However, we do not know for definite that this set exists. This is another leap of faith and so we need another axiom:

9. __"Axiom of replacement"__: This says that if we can define a set of rules which follow from our axioms which allows us to define a function from one set to another, then the set the function maps to exists!

This is referred to as the axiom of replacement as each element of our starting set $A$ can be thought of as being replaced by our function $f$ individually to produce $B$.

This can be thought of as a stricter version of __"Any things that we can conceive of that satisfy a particular property can be grouped together"__, allowing us to consider things that can be found in a set that already exists (and so avoiding Russel's paradox).

As a result of (9) some particularly useful sets can now be constructed:
- $A \cap B$: The set of all elements that are in $A$ and in $B$ referred to as "A _intersection_ B"
- $A / B$: The set of all the elements that are in $A$ once the elements that are in $B$ have been removed referred to as "A _complement_ B".
- $A \times B$: The set of all pairs $(a, b)$ of elements where $a$ is in $A$ and $b$ is in $B$ "The _cartesian product_ between $A$ and $B$"

In order to prove that these operations are valid a set containing each of their elements must first be proved to exist. For example all the elements of the cartesian product can be found in $\mathcal{P}(\mathcal{P}(X \cup Y))$.


## The Real Numbers $\mathbb{R}$
Not all numbers can be expressed as fractions. This might not necessarily be what you were expecting? To see (at least intuitively) why this is the case lets consider representing fractions as decimals. Each fraction can be equivalently written as a decimal number. For example $5 / 64$ is given by $0.078125$. What do we mean by this? We can think of the decimal numbers as a short-hand way of writing $$0.078125 = 0 \frac{1}{1} + 0  \frac{1}{10} +  7  \frac{1}{100} + 8  \frac{1}{1000} + 1  \frac{1}{10000} + 2  \frac{1}{100000} + 5  \frac{1}{1000000}$$. Two cases arise for fractions expressed in this way. Either we can express a sequence in a finite number of terms (as above) or their will be finitely many terms followed by a term that will repeat itself in a regular pattern for example $1 / 3 = 0.333...$ or $1 / 99 = 0.01010...$. But what happens if we consider adding digits to a decimal indefinitely and never forming a repeated pattern. For example,
$$0.078125136729420100357399387401377382...$$

Each time we add a decimal point we can think of adding an ever increasingly small part to the number $0.078125$. Expressing this slightly differently we can think of the number $0.07812513...$ as corresponding to a sequence $0, 0.0, 0.07, 0.07, 0.0781, 0.07812, 0.07812, ...$ where the difference between elements becomes arbitrarily small as the sequence progresses. Sequences of this kind are referred to as Cauchy Sequences and in the limit can be thought of as converging to a single fixed value. In this way we can think of each real number as a unique cauchy sequence!

If each element of a sequence become arbitrarily small to one another then the sequence is referred to as a *cauchy sequence* and in the limit can be thought of as converging to a single fixed value. We can think of each real number as a unique cauchy sequence!

In order to represent real numbers in this way we need to construct a sequence from sets. We can think of a sequence of a set of pairs between the natural numbers $(0, 1, 2, ..)$ and the rational numbers $\mathbb{Q}$. For example the sequence  $0, 0.0, 0.07, 0.07, 0.0781, ...$ can be thought of as a set $$\{(0, 0), (1, 0.0), (2, 0.07), (3, 0.078), (4, 0.0781), ... \}$$. Sets of this kind can be generated from the axioms we have defined so far as follows:
1. First we generate all possible pairs of natural and rational numbers using the cartesian product $\mathbb{N} \times \mathbb{Q}$ we just defined.
2. From this set of pairs we choose a sets of pairs which correspond to a valid Cauchy sequence such that their natural numbers ascend in terms of the natural number in each pair and their rational numbers become arbitrarily close to one another.
4. Repeat this process for all the possible sequences of elements in order to form the set of real numbers $\mathbb{R}$.

Steps 2 and 3 can be thought of as a function mapping the set $\mathbb{N} \times \mathbb{Q}$ onto the set of real numbers. As we know  $\mathbb{N} \times \mathbb{Q}$ already exists and the steps 2 and 3 can be carried out by using natural number and integer arithmetic to check which pairs are valid by the axiom of replacement the real numbers are therefore be defined!

Once again we can define arithmetic operations on the real numbers by defining functions which take in one Cauchy sequence and produce another. It can be [shown](http://mathonline.wikidot.com/cauchy-sequences-of-real-numbers) that the sum, product, difference and cauchy sequences all result in cauchy sequences. In each case the operators are defined by summing over corresponding elements of the sequence. For example if $a = (1, 1.01, 1.0105, 1.01052, ...)$ and $b = (2, 2.7, 2.75, 2.758...)$ then $a + b = (3, 3.71,  3.7605,  3.76852)$.