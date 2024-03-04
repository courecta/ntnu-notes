# Discrete Mathematics [Spring 2024]

## First lecture (23/2) - Logic & Proofs pt. 1

### Propositional logic and proofs

We have symbols pertaining to propositions  
  
Let's assume we have 2 propositions, P and Q.

- AND (^) will be TRUE if both P and Q are true
- OR (V) will evaluate to TRUE if either P or Q are true
- NOT (~) will take proposition P to be TRUE if it is false

### Implication

Implication is the relation of two propositions, that is P --> Q. Here are it's evaluations.

- If P is true, then Q is true, thus the evaluation is TRUE
- If P is false, then the evaluation does not break the initial condition, because it was not fulfilled in the first place. Thus, it evaluates to TRUE

Therefore, we can see here, that P is the sufficient condition of Q, while Q is the necessary condition of P.  

> Here we can see the difference
> 
> - A necessary condition is one where if the necessary condition is not met, the event cannot occur
> - A sufficient condition is one where if the condition is met, the event must occur

### Equivalence

P <--> Q is true if both (P --> Q) and (Q --> P) is true

*   P if and only if Q (P iff Q)
*   P is equivalent to Q
*   Q is the necessary and sufficient condition of P

### Predicate logic

A predicate is a sentence with a variable. A quantifier is a symbol that allows us to make statements about the scope of quantity of a variable

The universal quantifier ( ∀ )

~for all

The existential quantifier ( ∃ )

~there exists

Here is an example, for a proposition, in which we will evaluate Let n be an integer. If n is an odd number, then n<sup>2</sup> is also odd  
We can first extract our P and Q statements.

- P: If n is an odd number
- Q: then n2 is also odd

We know the definition of an odd number, n = 2k + 1 , k ∈ Z  
Thus, n2 is equal to (2k + 1)<sup>2</sup> which is equal to <sup>2</sup> + 4k + 1, which for any n, will evaluate to be odd. Now what if we were to reverse the P and Q statements, in which,

- P: if n<sup>2</sup> is an odd number
- Q: then n is also odd

∀n∈Z , Q(n) --> P(n)  
thus we can prove by, ~P(n) --> ~Q(n), meaning "if n is even, then n<sup>2</sup> is even"

|P|Q|P --> Q|~Q --> ~P|~P --> ~Q|~P V Q|
|-|-|-------|---------|---------|------|
|T|T|   T   |    T    |    T    |   T  |
|T|F|   F   |    F    |    T    |   F  |
|F|T|   T   |    T    |    F    |   T  |
|F|F|   T   |    T    |    T    |   T  |


We can then prove by using the contrapositive (~Q --> ~P)

- Contrapositive statement: "If n is even, then n2 is even"
- Since n is even, there exists an integer k, s.t. n = 2k (even number formula)
- Thus, n<sup>2</sup> = (2k)<sup>2</sup> = 4k<sup>2</sup>, which is even, which evaluates to even

Here, we can see that there are many different types of proofs

- Direct proof
- Proof by contraposition
- Proof by contradiction
- To prove that statement R is true, we can show that if ~R --> ~F, where F is a known fact, F
- This implies that the premise R, was in fact false

### Proposition: √2 is irrational

_how do we prove this one?_

1.  We can tackle this elementary proof by using the aforementioned _proof by contradiction_
2.  This means that we must first _assume that √2 is rational_
3.  Now, the definition of a rational number is that the number can be represented by a/b, in which a and b are positive integers, and b ≠ 0
4.  Next, we must also assume that the gcd of a and b is, and only can be 1 (if there is any other number that both are divisible by, then the fraction is not in simplest form, in which, you can just simplify the expression until **gcd(a, b) = 1**)
5.  We can then re-arrange the equation √2 = a/b, to become a<sup>2</sup> = 2b<sup>2</sup>
6.  Thus, by definition, a will always be an even number (it is equal to b<sup>2</sup> multiplied by 2)
7.  If this is the case, then we can define c, an integer which a = 2c. This is valid because we already know a is an even number integer
8.  And since a2 = 2b<sup>2</sup>, we will then have 4c<sup>2</sup> = 2b<sup>2</sup>, which proves that b is also even!
9.  Since both a and b are even, they still share some gcd, s.t. **gcd(a, b) ≥ 2** which CONTRADICTS the statement made in step 4, **gcd(a, b) = 1**

  
## Second lecture(26/2) - Logic & Proofs pt. 2 and Modular Arithmetics pt. 1

### Here we have another proposition: Show that there exists irrational numbers x and y such that xy is rational

1.  First, we must state any known facts that can help us that we can write as a statement
2.  Known fact: The real power of a positive real number is real
3.  Then, we can let x = y = √2. As seen, we use the square root of 2 as our irrational number
4.  thus, if √2<sup>√2</sup> is rational, then we have the requested numbers by the proposition
5.  Finally, let x = √2<sup>√2</sup> and y = √2. Then (√2<sup>√2</sup>)<sup>√2</sup> = √2<sup>2</sup> = 2

### Sets

- The beginning of set theory started with Cantor in 1874 in a paper he wrote
- Here is how sets are represented:
- roster method (listing out all elements in the set): e.g. {a, b, c, d, e}
- set comprehension: S = {x | x has property P}
- S is the set of all elements x such that x has property P
- e.g. S = {x ∈ N | 0 < x < 5}

Sets serve as the primitive concept of most fields in mathematics  
An example is Gottlob Frege in the 1900s, used set theory to define the natural numbers  
One of the famous set problems/paradoxes is as such, Let S = {X | X is a set and X ∉ X}  
In other words, is S ∈ S or is S ∉ S?  
  
This is known as _Russell's Paradox_  
  

### Modular Arithmetics pt. 1
  
Definition: Given two integers a and b, and a positive integer m, we say that a is congruent to b modulo m if m | (a - b)  
Notation: a ≡ b (mod m)  
Proposition: Let a, b, c, d ∈ Z and m ∈ N. The following two congruences hold,

- a ≡ b (mod m), c ≡ d (mod m) ==> (a + c) ≡ (b + d) (mod m)
- a ≡ b (mod m), c ≡ d (mod m) ==> ac ≡ bd (mod m)

  
Now lets prove each statement one by one -- the first is the statement that [ a ≡ b (mod m) and c ≡ d (mod m) ==> (a + c) ≡ (b + d) (mod m) ]

  
## Third lecture(1/3) - Modular Arithmetics pt. 2

### Let's take a look at the RSA system

Let's say that Alice wants to send a message to Bob via a very unsafe communication channel. Can Alice find a way to properly encrypt the message with Bob's help so that only Bob can decrypt the original message? Let's see the preprocessing that Bob must first do to prep for this message.

1.  Choose 2 BIG prime numbers p & q
- Let n = p * q, r = ( p - 1 ) * ( q - 1 )
  - Choose a pair of numbers e and d s.t. d * e ≡ 1 ( mod r )
- e: the public encryption key  
- d: the private decryption key

Then, Bob announces (n , e) in public, and keeps p, q, r, d in private. Alice encrypts her message m as c and sends c via the public channel to Bob (assume that m < n)

> [!NOTE]
> In conclusion, Alice has c &equiv; m<sup>e</sup> ( mod n ) which is sent as c to Bob who has c<sup>d</sup> &equiv; m ( mod n )

The first question we must answer is how to find these large primes?

1. Given r, how do we find e and d such that d * e &equiv; 1 ( mod r )?
   - We can choose e so that gcd( r, e ) = 1, then d is guaranteed to exist
2. For any m < n, why is (m<sup>e</sup>)<sup>d</sup> &equiv; m ( mod n )?
3. Is this decryption easy?
   - if we have d, then we know the secret ( we need d )
   - we can solve d * e &equiv; 1 ( mod r ) for d ( we need r )
   - If we know p and q, then we have r ( we need to factorize n )

The theorem at hand here is called, Bézout's identity which states that

> For a, b &isin; N, if gcd( a , b ) = d, then &exist;x, y &isin; Z s.t. *ax + by = d*



## Fourth lecture(3/4) -