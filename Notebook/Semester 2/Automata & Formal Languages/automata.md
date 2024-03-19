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

Theorem 1.26

The class of regular languages is closed under the concatenation operation

( In other words A<sub>1</sub> and A<sub>2</sub> are regular => A<sub>1</sub> &#9900; A<sub>2</sub> is)

### Nondeterminism [Michael Rabin & Dana Scott, 1959]

- In a deterministic machine, given a state and the next input symbol, there is exactly one next state
- In a nondeterministic machine, several choices may exist for the next state at any point
- Deterministic and Nondeterministic Finite Automata are abbreviated as DFA and NFA respectively

- Nondeterminism is a sort of parallel computation process, because multiple processes can occur at the same time
- If at least one process ends on the accept state, the entire computation is accepted

Example: Let A be the language consisting of all strings over  {0, 1} containing a 1 in the third position from the end.

// figure 6

## Third Lecture - Regex

> [!IMPORTANT]
> Every NFA has an equivalent DFA

#### Proof of Theorem. 1.39

- A DFA is immediately an NFA
- For an NFA N = { Q, &Sigma;, &delta;, q<sub>0</sub>, F } , the DFA M = { Q', &Sigma;', &delta;', q<sub>0</sub>', F' } , where
- Q' = P(Q) ( Q' is the power series of Q)
- &delta;' ( R, a ) = &cup; E ( &delta; ( R, a ) )
- q<sub>0</sub>' = E ( q<sub>0</sub> )
- F' = { R &isin; Q' : F &cap; R &NotEqual; &empty; }

Let's convert an NFA into a DFA

// Figure 7

### Corollary 1.40 - A language is regular IFF &ForAll;&Exists; ( there exists some ) NFA that recognizes it

#### Theorem 1.45 - The class of regular languages is closed under the union operation

### Regular Expressions [ Stephen Cole Kleene, 1951 ]

- A regular expression ( regex ) is an expression built up with the regular operations, with operands being certain languages
- The value of a regex is also a language

#### Definition : R is a regular expression, if R is

- a , for some a &isin; &Sigma; ( representing the language { a } )
- &epsilon; ( representing the language { &epsilon; } )
- &empty;
- R<sub>1</sub> &cup; R<sub>2</sub>
- R<sub>1</sub> &dot; R<sub>2</sub> ( usually abbreviated as  R<sub>1</sub>R<sub>2</sub> )
- R<sub>1</sub>*

where R<sub>1</sub> and R<sub>2</sub> are regular expressions

Exercise : What are the languages described by he regular expressions? ( assuming &Sigma; = { 0, 1 } )

// figure 8

#### Theorem 1.54 - A language is regular IFF some regular expression describes it

The proof is constructive; namely, in either direction we present an algorithm that converts one to the other

> e.g. using Kleene's algorithm to turn an NFA / DFA &rarr; regex and converting back using Thompson's algorithm

Here is a proof for sufficiency:

The idea here is that we show all the atoms are recognized by some NFA. This along with Theorems 1.45 , 1.47 , and 1.49 , the sufficiency follows

- R = a for a &isin; &Sigma; &rarr;
- R = &epsilon;
- R = &empty;

Exercise : Convert ( ab &cup; a )* to an NFA using the algorithm suggested in the previous proof

// figure 9

Now let's look at the proof for necessity:

- Assume that Q = { q<sub>0</sub>, q<sub>1</sub>, ... , q<sub>n</sub>} and F = { q<sub>0</sub>, q<sub>1</sub>, ... , q<sub>e</sub>}
- Let R<sub>ij</sub><sup>k</sup> be the set of strings for each of which there is a corresponding sequence of transitions from state q<sub>i</sub> to q<sub>j</sub> with all intermediate states less than or equal to k
- the language of the DFA is R<sub>01</sub><sup>n</sup> &cup; R<sub>02</sub><sup>n</sup> &cup; ... &cup; R<sub>0e</sub><sup>n</sup>

Thus, the claim is as follows : For all i , j , k there is a regular expression representing Let R<sub>ij</sub><sup>k</sup>

- We treat each symbol on the transition arcs as its own regular expression
- Then, we eliminate the states one by one, only preserving the languages recognized by the original machine

Example

// figure 10

## Fourth lecture - Regex

There are some cases where there are languages that are not regular. For example:

- B = { 0<sup>n</sup>1<sup>n</sup>: n &GreaterEqual; 0 }
- C = { w: w has an equal number of 0's and 1's }
- D = { w: w has an equal number of occurrences }

#### Theorem 1.70 Pumping Lemma. If A is a regular language, then there is a number p, where if s is any string in A of at least p, then s may be divided into three pieces, s = xyz satisfying the following:

- for each i &GreaterEqual; 0, xy<sup>i</sup>z &isin; A
- |y| > 0
- |xy| &le; p

( such a number p is called the pumping length )

Proof of Lemma:

We can first see an example

The language B = { 0<sup>n</sup>1<sup>n</sup>: n &GreaterEqual; 0 } is not regular
- we can prove the proposition by contradiction
- suppose then, that B is a regular language
- Let p be the pumping length
- COnsider the string s = 0<sup>p</sup>1<sup>p</sup>, which belongs to B
- By theorem 1.70, s can be written as xyz, with |y| > 0, s.t. xy<sup>i</sup>z &isin; B

Now let's see its general proof for Theorem 1.70

- Let M = ( Q, &Sigma;, &delta;, q<sub>0</sub>, F ) be a DFA that recognizes A
- The claim is that |Q| can be the pumping length
- consider a string s of length n ( n &GreaterEqual; |Q| )
- Let r<sub>1</sub>,...,r<sub>n+1</sub> be the sequence of states by which M processes s
- By the pigeonhole principle, there exists j and l ( with j < l ) such that r<sub>j</sub> = r<sub>l</sub>
- We take r<sub>l</sub> to be the very first repeated states

The language C, can also be proven to be irregular, with the same proof we gave language B. Here, we can see that

- If y only has 0's, then xyyz contains more 0's than 1's, and vice versa
- If y consists of both 0's and 1's, then xyyz contains the same number of 0's and 1's but its not contiguous
- Thus there is no p to satisfy the conditions for the pumping lemma &rarr; contradiction

## Fifth lectre - CFG ( Context-Free Grammar)

