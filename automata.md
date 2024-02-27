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

// fig 1

A finite automation processes the input as such:
- the processing begins at the start stage
- It receives symbols (from the input string) one by one from left to right
- For each symbol the machine moves from one state to another along the transition labeled with the symbol
- It produces an output (either accept or reject) after it reads the last symbol. Accept is outputted if it is in the 'accept' state and rejected if otherwise

A finite automation is a 5-tuple (Q, &Sigma;, &delta;, q~0~, F), where
- Q is a finite set called states
- &Sigma; is a finite set called alphabet
- &delta; is Q x &Sigma; -> Q, called the transition function
- q~0~ &isin; Q is the start state
- F &sube; Q is the set of 'accept' states