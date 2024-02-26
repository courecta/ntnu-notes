# Discrete Mathematics [Spring 2024]

<details>
<summary>First lecture (23/2) - Logic & Proofs pt. 1</summary>
<h3>Propositional logic and proofs</h3>
We have symbols pertaining to propositions<br>
<br>Let's assume we have 2 propositions, P and Q.
<ul>
    <li>AND (^) will be TRUE if both P and Q are true</li>
    <li>OR (V) will evaluate to TRUE if either P or Q are true</li>
    <li>NOT (~) will take proposition P to be TRUE if it is false</li>
</ul>
    
<h3>Implication</h3>
    
Implication is the relation of two propositions, that is P --> Q. Here are it's evaluations.
<ul>
    <li>If P is true, then Q is true, thus the evauluation is TRUE</li>
    <li>If P is false, then the evaluation does not break the initial condition, because it was not fulfilled in the first place. Thus, it evauluates to TRUE</li>
</ul>
Therefore, we can see here, that P is the sufficient condition of Q, while Q is the necessary condition of P.<br>

<blockquote>
Here we can see the difference
<ul>
    <li>A necessary condition is one where if the necessary condition is not met, the event cannot occur</li>
    <li>A sufficient condition is one where if the condition is met, the event must occur</li>
</ul>
</blockquote>

<h3>Equivalence</h3>

P <--> Q is true if both (P --> Q) and (Q --> P) is true

<ul>
    <li>P if and only if Q (P iff Q)</li>
    <li>P is equivalent to Q</li>
    <li>Q is the necessary and sufficient condition of P</li>
</ul>

<h3>Predicate logic</h3>
    
A predicate is a sentence with a variable. A quantifier is a symbol that allows us to make statements about the scope of quantity of a variable

<dl>
    <dt>The universal quantifier ( ∀ )</dt>
        <dd>~for all</dd>
</dl>
<dl>
    <dt>The existential quantifier ( ∃ )</dt>
        <dd>~there exists</dd>
</dl>

Here is an example, for a proposition, in which we will evaluate

*Let n be an integer. If n is an odd number, then n<sup>2</sup> is also odd*<br>

We can first extract our P and Q statements.

<ul>
    <li>P: If n is an odd number</li>
    <li>Q: then n<sup>2</sup> is also odd</li>
</ul>

We know the definition of an odd number, n = 2k + 1 , k ∈ Z<br>

Thus, n<sup>2</sup> is equal to (2k + 1)<sup>2</sup> which is equal to 4k<sup>2</sup> + 4k + 1, which for any n, will evaluate to be odd.

Now what if we were to reverse the P and Q statements, in which,

<ul>
    <li>P: if n<sup>2</sup> is an odd number</li>
    <li>Q: then n is also odd</li>
</ul>

∀n∈Z , Q(n) --> P(n)<br>

thus we can prove by, ~P(n) --> ~Q(n), meaning "if n is even, then n<sup>2</sup> is even"
    
|P|Q|P --> Q|~Q --> ~P|~P --> ~Q|~P V Q|
|-|-|-------|---------|---------|------|
|T|T|   T   |    T    |    T    |   T  |
|T|F|   F   |    F    |    T    |   F  |
|F|T|   T   |    T    |    F    |   T  |
|F|F|   T   |    T    |    T    |   T  |

We can then prove by using the contrapositive (~Q --> ~P)

<ul>
    <li>Contrapositive statement: "If n is even, then n<sup>2</sup> is even"</li>
    <li>Since n is even, there exists an integer k, s.t. n = 2k (even number formula)</li>
    <li>Thus, n<sup>2</sup> = (2k)<sup>2</sup> = 4k<sup>2</sup>, which is even, which evaluates to even</li>
    </ul>

Here, we can see that there are many different types of proofs

<ul>
        <li>Direct proof</li>
        <li>Proof by contraposition</li>
        <li>Proof by contradiction</li>
        <li>To prove that statement R is true, we can show that if ~R --> ~F, where F is a known fact, F</li>
        <li>This implies that the premise R, was in fact false</li>
</ul>

<h3>Proposition: &#8730;2 is irrational</h3>

<i>how do we prove this one?</i>

<ol>
    <li>We can tackle this elementary proof by using the aforementioned <i>proof by contradiction</i></li>
    <li>This means that we must first <i>assume that &#8730;2 is rational</i></li>
    <li>Now, the definition of a rational number is that the number can be represented by <sup>a</sup>/<sub>b</sub>, in which a and b are positive integers, and b &NotEqual; 0</li>
    <li>Next, we must also assume that the gcd of a and b is, and only can be 1 (if there is any other number that both are divisible by, then the fraction is not in simplest form, in which, you can just simplify the expression until <b>gcd(a, b) = 1</b>)</li>
    <li>We can then re-arrange the equation &#8730;2 = <sup>a</sup>/<sub>b</sub>, to become a<sup>2</sup> = 2b<sup>2</sup></li>
    <li>Thus, by definition, a will always be an even number (it is equal to b<sup>2</sup> multiplied by 2)</li>
    <li>If this is the case, then we can define c, an integer which a = 2c. This is valid because we already know a is an even number integer</li>
    <li>And since a<sup>2</sup> = 2b<sup>2</sup>, we will then have 4c<sup>2</sup> = 2b<sup>2</sup>, which proves that b is also even!</li>
    <li>Since both a and b are even, they still share some gcd, s.t. <b>gcd(a, b) &ge; 2</b> which CONTRADICTS the statement made in step 4, <b>gcd(a, b) = 1</b></li>
</ol>
</details>

<br>

<details>
<summary>Second lecture(26/2) - Logic & Proofs pt. 2</summary>
<h3>Here we have another proposition: Show that there exists irrational numbers x and y such that x<sup>y</sup> is rational</h3>
<ol>
    <li>First, we must state any known facts that can help us that we can write as a statement</li>
    <li>Known fact: The real power of a positive real number is real</li>
    <li>Then, we can let x = y = &radic;2. As seen, we use the square root of 2 as our irrational number</li>
    <li>thus, if &radic;2<sup>&radic;2</sup> is rational, then we have the requested numbers by the proposition</li>
    <li>Finally, let x = &radic;2<sup>&radic;2</sup> and y = &radic;2. Then (&radic;2<sup>&radic;2</sup>)<sup>&radic;2</sup> = &radic;2<sup>2</sup> = 2</li>
</ol>

<h3>Sets</h3>
<ul>
    <li>The beginning of set theory started with Cantor in 1874 in a paper he wrote</li>
    <li>Here is how sets are represented:</li>
    <li>roster method (listing out all elements in the set): e.g. {a, b, c, d, e}</li>
    <li>set comprehension: S = {x | x has property P}</li>
        <li>S is the set of all elements x such that x has property P</li>
        <li>e.g. S = {x &isin; N | 0 < x < 5}</li>
</ul>
Sets serve as the primitive concept of most fields in mathematics<br>
An example is Gottlob Frege in the 1900s, used set theory to define the natural numbers<br>
One of the famous set problems/paradoxes is as such, Let S = {X | X is a set and X &notin; X}<br>
    In other words, is S &isin; S or is S &notin; S?<br>
<br>This is known as <i>Russell's Paradox</i><br>
<br>
<h2>Modular Arithmetics</h2>
<br>Definition: Given two integers a and b, and a positive integer m, we say that a is congruent to b modulo m if m | (a - b)<br>
Notation: a &equiv; b (mod m)<br>

Proposition: Let a, b, c, d &isin; Z and m &isin; N. The following two congruences hold,
<ul>
    <li>a &equiv; b (mod m), c &equiv; d (mod m) ==> (a + c) &equiv; (b + d) (mod m)</li>
    <li>a &equiv; b (mod m), c &equiv; d (mod m) ==> ac &equiv; bd (mod m)</li>
</ul>

</details>

<br>

<details>
<summary>Third lecture(1/3) - Modular Arithmetics pt. 1</summary>

</details>
