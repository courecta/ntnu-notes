# Formal Languages & Automata [Spring 2024]

## First Lecture - Introduction

> We look at the problems set by Hilbert, Turing & Church, and Chomsky that allows us to examine just what exactly language is.

> Languages can be classified into 4 types, each a subset of the one before

FORMAL --> RECURSIVE --> CONTEXT-SENSITIVE --> CONTEXT-FREE --> REGULAR

> Each language type in the hierarchy also has its own automaton equivalent description

> This brings up the fact that we are actually studying the fundamental capability and limits of what can or cannot be computed by computers (Automata theory, Computability theory, and Complexity theory)

> We may also observe that a fundamental issue is what makes a problem hard or easy. (Is sorting an easy or hard problem? What about a subset sum?) --> (Given a set of integers, is there a subset of integers that sum up to zero?)

The central problem of complexity theory is what makes some problems hard, while some others easy

> We can observe that computability and complexity are closely related.

| Complexity | Computability |
| -----------|---------------|



## Second Lecture - Regex

A finite automata models a computer with little to no memory

- e.g. a vending machine
  - A bottle of water is $15 NTD. The machine only accepts coins of $5 or $10
  - Determine whether a sequence of payments is valid
  - e.g. (5, 5, 5), (10, 5), (5, 10)

We can verify the validity of the sequence by using a finite automata

// figure 1

A finite automation processes the input as such:

- the processing begins at the start stage
- It receives symbols (from the input string) one by one from left to right
- For each symbol the machine moves from one state to another along the transition labeled with the symbol
- It produces an output (either accept or reject) after it reads the last symbol. Accept is outputted if it is in the 'accept' state and rejected if otherwise

A finite automation is a 5-tuple (Q, &Sigma;, &delta;, q<sub>0</sub>, F), where
- Q is a finite set called states
- &Sigma; is a finite set called alphabet
- &delta; is Q x &Sigma; -> Q, called the transition function
- q<sub>0</sub> &isin; Q is the start state
- F &sube; Q is the set of 'accept' states

We can conclude that,

- The language of machine M is L(M): which is the set of all strings that machine M accepts
- Machine M recognizes a language A if A = L(M)
- A language is a regular language if some finite automation recognizes it

// figure 2

Exercise:

- Design a finite automation E<sub>1</sub> with
  - L( E<sub>1</sub> ) = { w: w is a string consisting of odd 1's }
  - Design a finite automation E<sub>2</sub> that recognizes the language of all strings containing 001 as a substring

// answers in figure 3

Regular operations:

- Union: A &cup; B = { x: x &isin; A or x &isin; B }
- Concatenation: A &#9900; B = { xy: x &isin; A and y &isin; B }
- Kleene Star: A* = { x<sub>1</sub>x<sub>2</sub> ... x<sub>k</sub>: k &GreaterEqual; 0 and x<sub>i</sub> &isin; A }

Note:

- &epsilon; ( the empty string ) is always a member of A*, no matter what A is
- For any language A, A &cup; &varnothing; = A, A &#9900; { &epsilon; } = A, A &#9900; &varnothing; = &varnothing; ( remember that an empty string and an empty set is different)

Theorem 1.25

The class of regular languages is closed under the union operation

( In other words A<sub>1</sub> and A<sub>2</sub> are regular => A<sub>1</sub> &cup; A<sub>2</sub> is)

The two machines M<sub>1</sub> and M<sub>2</sub> that processes an input w = w<sub>1</sub>w<sub>2</sub> ... w<sub>n</sub>

We want to construct a machine that accepts w when any of M<sub>1</sub> and M<sub>2</sub> accepts

// figure 4

Proof of Theorem 1.25:

- Let A<sub>1</sub> and A<sub>2</sub> be regular
- By definition, there exists a finite automata
  - M<sub>1</sub> = ( Q<sub>1</sub>, &Sigma;, &delta;<sub>1</sub>, q<sub>1</sub>, F ) and M<sub>2</sub> = ( Q<sub>2</sub>, &Sigma;, &delta<sub>2</sub>, q<sub>2</sub>, F ) that recognizes A<sub>1</sub> and A<sub>2</sub> respectively
- Let M = ( Q, &Sigma;, &delta;, q, F ), where
  - Q = Q<sub>1</sub> x Q<sub>2</sub>
  - &sigma;( ( r<sub>1</sub>, r<sub>2</sub>), a ) = ( &sigma;<sub>1</sub>( ( r<sub>1</sub>, a), &sigma;<sub>2</sub>( ( r<sub>2</sub>, a) ) )
  - q = ( q<sub>1</sub>, q<sub>2</sub> )
  - F = ( F<sub>1</sub> x Q<sub>2</sub> ) &cup; ( Q<sub>1</sub> x F<sub>2</sub> )