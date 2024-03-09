---
title: 00. Sets
tags:
  - zk
  - basic
  - set
---

# WTF zk Tutorial Lesson 0: Sets

Abstract algebra, also known as modern algebra, is one of the important foundations of modern mathematics, studying the structural theory of three basic algebraic structures: groups, rings, and fields. The concepts of abstract algebra are extensively used in zk theory; therefore, learners should be familiar with the basic knowledge of abstract algebra.

In this lesson, we mainly learn the basics of abstract algebra: set theory.

## 1. Definition of Sets

Sets are mathematical models (collections of objects) consisting of distinct objects, which are called the elements (elements) of the set. Integers, Rational numbers, Real numbers, Complex numbers, Matrices, Polynomials, Polygons, and many other concepts are essentially sets.

> Common set abbreviations: $\mathbb{N}$ represents the set of all natural numbers (Natural numbers), $\mathbb{Z}$ represents the set of all integers ("Zahl" is Integer in German), $\mathbb{Q}$ represents the set of all rational numbers (Rational numbers), $\mathbb{R}$ represents the set of all real numbers (Real numbers), $\mathbb{C}$ represents the set of all complex numbers (Complex numbers)


We define the number of elements in a set as the set's cardinality. If the cardinality is finite, it is called a finite set; otherwise, it is an infinite set. There is a special type of set that contains no elements, known as the empty set $\emptyset$, which is characterized by:

- The empty set is a proper subset of any non-empty set;
- The empty set is a subset of any set.

## 2. Characteristics of Sets

Definiteness: Given a set $S$ and any element $a$, the element either belongs to the set $a\in S$ or does not belong to the set $a\notin S$. There is no room for ambiguity.

Mutual Exclusivity: Within a set, any two elements are considered distinct, meaning each element appears only once. Sometimes, to describe situations where the same element appears multiple times, a multiset is used, in which elements are allowed to appear multiple times.

```python
S = {1, 1, 2}
for elem in S:
    print(elem)
# 1
# 2
```

In a set, the status of each element is the same, and the elements are unordered. An order relation can be defined on the set, and once an order relation is defined, the elements can be sorted according to the order relation. However, as far as the characteristics of the set itself are concerned, there is no inherent order among the elements.

```python
S = {'0xaa', 123, 'a', 0.123}

# Unorderedness
for elem in S:
    print(elem)
# 0xaa
# 0.123
# 123
# a
```

## 3. Basic Relations Between Sets

### Subsets and Supersets
Consider the set of integers and the set of rational numbers. There seems to be a certain relationship between them: all integers are rational numbers, but not all rational numbers are integers. We define: the set of integers is a subset of the set of rational numbers, conversely, the set of rational numbers is a superset of the set of integers.

Note: For \(A\) to be a subset of \(B\), it is not required that \(A\) is strictly less than \(B\). Thus, it can be said that the set of integers is a subset of itself. When \(A\) is a subset of \(B\) and \(A\) is strictly less than \(B\), then it can further be said: \(A\) is a proper subset of \(B\).

### Intersection and Union

- Intersection: A set consisting of elements that belong to both \(A\) and \(B\), denoted as \(A \bigcap B\) (or \(B \bigcap A\)).
- Union: A set consisting of all elements that belong to either set \(A\) or set \(B\), denoted as \(A \bigcup B\) (or \(B \bigcup A\)).

Both operations follow the commutative, associative, and distributive laws.

### Equality/Equivalence

Two sets are considered equivalent if they contain exactly the same elements (order not considered). In strict mathematical language, this is expressed as: If \(A \subseteq B \wedge B \subseteq A\), then \(A = B\).

### Cardinality

As previously mentioned, the number of elements in a set is defined as its cardinality. Generally, the concept of cardinality is meaningful for finite sets, denoted as \(|A|\). For infinite sets, such as the set of integers, we can describe its elements verbally, calling it countably infinite; whereas for something like the set of complex numbers, which we cannot enumerate, it is referred to as uncountably infinite.

## 4. Ordered Pairs

The elements of a set are unordered, but ordered pairs (or tuples) are a new data structure derived from sets. In the programming world, these are often referred to as tuples.

So how are ordered pairs generated from an unordered set? A specific implementation is to represent the tuple \((a, b)\) as a set in the form \{\{a\}, \{a, b\}\}. Note that in such a set, an element is either a letter or a set with a cardinality of 1. Therefore, we say \((a, b) \neq (b, a)\) because \{\{a\}, \{b\}\} \(\neq\) \{\{b\}, \{a\}\}.

Note that the number of elements in an ordered pair (tuple) can be arbitrary.

## 5. Cartesian Product

Given two sets \(A\) and \(B\), we can define another set \(C\), where the elements of \(C\) are ordered pairs with the first element from \(A\) and the second from \(B\). This set is known as the Cartesian product.

The Cartesian product does not follow the commutative law.

## 6. Functions

With the operation of the Cartesian product, we can define functions from a mathematical perspective. For instance, to define a function \(f\) satisfying \(f(1) = x, f(2) = y, f(3) = z\), we just need to define two sets \(\{1, 2, 3\}\) and \(\{x, y, z\}\), perform a Cartesian product between them, and select a subset of the result to achieve the target mapping relationship \((1, x), (2, y), (3, z)\).

Thus, in set theory, a function is a subset of the Cartesian product of a domain set and a codomain set. In other words, as long as we have a domain set and a codomain set, their Cartesian product can yield all possible mapping relationships from the domain to the codomain, with a function defined as a subset of these mappings.

> Mathematicians seldom care about computability. That is, mathematicians define a function between two sets, but how this function is computed (the specific mathematical formula) is of no concern to them.
> 
> Programmers, on the other hand, believe all functions are computable and have specific mathematical formulas.

In most cases, the term "function" is equivalent to "mapping." Of course, how a mapping (function) is defined determines its usability. For example, mapping everything to 0 is certainly valid, but such a mapping is hardly useful.

Axiom of Choice: The Cartesian product of a set of non-empty sets is non-empty.

## 7. Injection, Surjection, Bijection

While we define a function as a subset of the Cartesian product of two sets, this subset is not arbitrary; it requires restriction: given an input, the output of the function must be unique.

There are three types of mappings that meet the requirements of a function:
- Injective function: Each element of the codomain corresponds at most to one element of the domain (also called a preimage). Elements of the codomain may not correspond to any preimage. However, if a preimage in the domain corresponds to the same element of the codomain, then the function does not satisfy injectivity.
- Surjective function: Each element of the codomain corresponds to at least one element of the domain. If there exists an element in the codomain that does not correspond to any preimage, then the function does not satisfy surjectivity.
- Bijective function: A function is bijective if and only if it is both injective and surjective.

For the above mappings, the most important thing is how to define the domain and codomain, as different domains and codomains produce different mappings.

Bijections and surjections are also very important when discussing concepts of isomorphism and homomorphism. Please remember these fundamental definitions.

## 8. Relations

Relation is a very subtle concept, often encountered when reading ZKP-related papers. In fact
