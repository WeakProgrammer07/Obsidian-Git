## Propositional Logic Notes
- Deals with propositions (Statements)
- Propositions can only be true or false
- Simplest are primitive propositions
	- use $p, q, r, etc$
- Combine primitive propositions to become compound propositions or formulas
	- use $\phi, \psi$
- Logic connectives

| Connective                       | Description     | Example                                                                    |
| -------------------------------- | --------------- | -------------------------------------------------------------------------- |
| Negation ($\neg$)                | NOT             | It is not true that at least one political is honest                       |
| Conjunction ($\wedge$)           | AND             | In this room there is a tiger and in the other room there is a tiger       |
| Disjunction ($\vee$)             | OR              | There is a tiger or a lady in this room (Can be both)                      |
| Implication ($\to$)              | If... then...   | if there is a tiger then there is no lady in there                         |
| Equivalence ($\leftrightarrow$)  | If and only if  | There is a lady in this room if and only if the tiger is in the other room |
| Exclusive Or ($\oplus$)${ \ \ }$ | Either... or... | There is either a tiger or a lady in the room                              |
- Truth Tables
- Implication (only false if the first is true and second is false)
	- False when, $p \to q$, p is true and q is false
- $p \to q$ 
	- Converse: $q \to p$
	- Contrapositive: $\neg q \to \neg p$
	- Inverse: $\neg p \to \neg q$
- Tautology
	- Compound proposition that is true for all combinations
- Contradiction
	- Compound proposition that is false for all combinations
- Logic Equivalences
	- Logically equivalent if the proposition $\phi$ is true if and only if $\psi$ is true (or both are false)
	- Truth tables are equal
## Laws of Logic
- Double Negation ($\neg \neg p \iff p$)
- DeMorgan's Laws
	- $\neg (p \wedge q) \iff \neg p \vee \neg q$
	- $\neg (p \vee q) \iff \neg p \wedge \neg q$
- Commutative Laws
	- $p \wedge q \iff q \wedge p$
	- $p \vee q \iff q \vee p$
- Associative Laws
	- $p \wedge (q \wedge r) \iff (p \wedge q) \wedge r$
	- $p \vee (q \vee r) \iff (p \vee q) \vee r$
- Distributive Laws
	- $p \wedge (q \vee r) \iff (p \wedge q) \vee (p \wedge r)$
	- $p \vee (q \wedge r) \iff (p \vee q) \wedge (p \vee r)$
- Idempotent Laws
	- $p \wedge p \iff p$
	- $p \vee p \iff p$
- Identity Laws
	- $p \wedge T \iff p$
	- $p \vee F \iff p$
- Inverse Laws
	- $p \wedge \neg p \iff F$
	- $p \vee \neg p \iff T$
- Domination Laws
	- $p \wedge F \iff F$
	- $p \vee T \iff T$
- Absorption Laws
	- $p \wedge (p \vee q) \iff p$
	- $p \vee (p \wedge q) \iff p$
##### Expressing Connectives
- $p \oplus q \iff \neg (p \leftrightarrow q )$
- $p \leftrightarrow q \iff (p \to q) \wedge (q \to p)$
- $p \to q \iff \neg p \vee q$
## Rules of Inference
- One of the main goals of logic is to distinguish valid and invalid arguments
- List of rules used
	- Modus Ponens
		- $\begin{array}{l} p \to q \\ p \\ \hline \therefore q \end{array}$ 
	- Modus Tollens
		- $\begin{array}{l} p \to q \\ \neg q \\ \hline \therefore \neg p \end{array}$
	- Rule of Syllogism
		- $\begin{array}{l} p \to q \\ q \to r \\ \hline \therefore p \to r \end{array}$
	- Rule of Disjunctive Syllogism
		- $\begin{array}{l} p \vee q \\ \neg p \\ \hline \therefore q \end{array}$
	- Rule of Proof By Cases
		- $\begin{array}{l} p \to r \\ q \to r \\ \hline \therefore (p \vee q) \to r \end{array}$
	- Rule of Contradiction
		- $\begin{array}{l} \neg p \to F \\ \hline \therefore p \end{array}$
	- Rule of Simplification
		-  $\begin{array}{l} \neg p \wedge q \\ \hline \therefore p \end{array}$
	- Rule of Amplification
		- $\begin{array}{l} \neg p \\ \hline \therefore p \vee q \end{array}$

## Predicates and Quantifiers
- Types of Predicates
	- Unary Predicates: Contain only one variable: P(x)
		- x is greater than 3
		- x is my brother
		- x is a human being
	- Binary Predicates: Contain 2 variables: Q(x,y)
		- x is greater than y
		- x is the mother of y
		- car x has colour y
	- Ternary Predicates: Contain 3 variables R(x,y,z)
		- x divides y + z
		- x sits between y and z
		- x is a son of y and z
- Assigning a value
	- When a value is assigned to a predicate it becomes a statement
		- P(x) = x is greater than 3
			- x = 2: False
			- x = 4: True
		- Q(x,y) = car x has colour y
			- x = my car, y = red: True
			- x = my car, y = Blue: False
	- Universe
		- Cannot assign a variable of a predicate to any value, need to make it a meaningful statement
- Universal Quantifiers
	- $\forall$: Asserts that a predicate is true for all values
		- $\forall x \ P(x)$: means that if every value of $a$ from the universe is true for $P(a)$ then $P(x)$ is true
		- To make if False find at least one counterexample (where $P(x)$ is False)
	- $\exists$: Assets a predicate is true for at least one value from universe
		- $\exists \ P(x)$: means that there is a value a from the universe such that $P(a)$ is true
		- $\exists \ P(x)$: is false if and only if for all $a$ from the universe $P(a)$ is false
			- Quite difficult to prove
## Logic Equivalence
- 2 quantified propositions are said to be logically equivalent if they are equivalent for **any given** universe
	- to prove they are not find a counterexample
## Theorems and Proofs
- Two cases for theorems
	- Mathematical statement of certain importance
	- A theorem is any proposition inferred within an **axiomatic theory**
- To infer a theorem we need to start with something: called a collection of **axioms**
- Two understandings of axioms 
	- Self Evident Truth (usually not quite truths)
		- two non-parallel lines intersect
		- there is something outside me
	- Propositions we assume as true
		- facts from experiment or observation
		- something we suggest and want to see implications
- Proving theorems
	- Simplest method is the method of exhaustion:
		- To prove that $\forall x \ P(x)$, just verify that $P(a)$ is true or all values $a$ from the universe
		- To prove that $\exists x \ P(x)$, by checking all the values in the universe to find a value $a$ such that $P(a)$ is true
- Rule of Universal Specification
	- If a proposition becomes true for all values of the universe then it is true for a specific individual value from that universe
		- $\begin{array}{l} \forall x \ P(x) \\ \hline \therefore P(c) \end{array}$
	- Example$$
\begin{array}{|l|l|}
\hline
\textbf{Step} & \textbf{Reason} \\
\hline
1. \  \forall x(P(x) \to Q(x)) & \text{Premise} \\
\hline
2. \  P(Socrates) \to Q(Socrates) & \text{Rule of Universal Specification} \\
\hline
3. \ P(Socrates) & \text{Premise} \\
\hline
4. \ Q(Socrates) & \text{Modus Ponens} \\
\hline
\end{array}
$$
- Rule of Universal Generalization
	- If a proposition $P(x)$ is proved to be true when $x$ is assigned to any arbitrary number (generic) value from the universe, then the proposition $\forall x \ P(x)$ is also true.
	- Example: If $2x - 6 = 0$ then $x = 3$
	- Notation: $P(x): 2x - 6 = 0, Q(x): 2x = 6, R(x): x = 3$
	- Premises: $\forall x \ (P(x) \to Q(x)), \ \forall x \ (Q(x) \to R(x))$
	- Conclusion: $\forall x \ (P(x) \to R(x))$$$
\begin{array}{|l|l|}
\hline
\textbf{Step} & \textbf{Reason} \\
\hline
1. \  \forall x(P(x) \to Q(x)), \ \forall x \ (Q(x) \to R(x)) & \text{Premises} \\
\hline
2. \  P(c) \to Q(c), \ Q(c) \to R(c)) & \text{Rule of Universal Specification} \\
\hline
3. \ P(c) \to R(c) & \text{Rule of Syllogism} \\
\hline
4. \ \forall x \ (P(x) \to R(x))  & \text{Rule of Universal Generalization} \\
\hline
\end{array}
$$
## Sets
- A set is an unordered collection of objects
- The objects in a set are called **elements** or **members** of the set
	- $a \in A$: a is an element of A, a belongs to A
	- $a \notin A$: a is not an element of A, a does not belong to A
- Describing a set
	- Listing
		- {0,1,2,3,4,5,6,7,8,9} - the set of digits
		- {a, b ,c,...x ,y ,z} - set of Latin letters, alphabet
	- Set Builder
		- Big sets can be described using **set builder**
		- {$x \ |\ P(x)$}, the set of all $x$ such that $P(x)$
- A set can be an element of another set
	- {{a, b ,c,...},{$\alpha, \beta, \gamma, ...$},...}
- Sets to know/memorize
	- $\mathbb{N} = \{0,1,2,3,...\}$: the set of natural numbers
	- $\mathbb{Z} = \{..., -2, -1, 0,1,2,3,...\}$: the set of integers
	- $\mathbb{R}$: the set of real numbers
- ##### Equality of Sets, Subsets
	- Two sets are **equal** if they have the same elements
		- $A = B$ if and only if $\forall x \ (x \in A \leftrightarrow x \in B)$ 
		- $\{1,3,5\} = \{5,3,1\}$
		- $\{1,3,5\} = \{5,5,5,5,3,3,3,1,3,1\}$
		- $\{1,3,5\} \neq \{1,3,\{5\}\}$
	- Set B is a subset of set A if every element of B is also an element of A
		- $B \subseteq A$ if and only if $\forall x \ (x \in B \to x \in A)$ 
		- $\{1,3\} \subseteq \{1,3,5\}$
	- Set B **is not** a subset of set A if
		- $\exists x \ (x \in B \wedge x \notin A)$ 
	- Another way to say two sets are equal are if they are subsets of each other
- A **proper subset** of set A, if it is a subset of A and is not equal to A
- An empty set is $\emptyset$ 
- **Power Set**
	- the power set of A is the set of all subsets of the set A
	- if A is a finite set, then $|P(A)| = 2^{|A|}$
### Relations Between Sets
- Venn Diagrams to represent sets
- ![[Pasted image 20251206105024.png|300]]
- The **intersection** of sets A and B, denoted by $A \cap B$, is the set that contains those elements that belong to both A and B
- ![[Pasted image 20251206105612.png|300]]
	- Example
		- $\{1,3,5,7\} \cap \{2,3,4,5,6\} = \{3,5\}$ 
- The **union** of sets A and B, denoted by $A \cup B$, is the set that contains those elements that are in A or in B
- ![[Pasted image 20251206105858.png|300]]
	- Example
		- $\{1,3,5,7\} \cup \{2,3,4,5,6,7\} = \{1,2,3,4,5,6,7\}$
- Sets A and B are said to be **disjoint** if $A \cap B = \emptyset$
	- Example: Sets $\{1,3,5\}$ and $\{2,4,6\}$ are disjoint
- Principle of inclusion exclusion: for any *finite* sets A and B
- ![[Pasted image 20251206110402.png|300]]
	- To count elements in $A \cup B$ we first count the elements of A, then B. Elements of $A \cap B$ are counted twice so we subtract the number of such elements
	- If A and B are disjoint then $|A \cup B| = |A| + |B|$ 
- Symmetric Difference
- ![[Pasted image 20251206111013.png|300]]
	- The symmetric difference of sets A and B, denoted by $A \ \Delta \ B$ 
	- Is the set that contains elements that are in either A or B, but not in both
- Disjoint sets and symmetric difference
	- Sets A and B are disjoint if and only if: $A \cup B = A \ \Delta \ B$
- **Complement**
- ![[Pasted image 20251206111521.png|450]]
	- Let A be a set and U a universe, $A \subseteq U$. The complement of A, denoted by **$\overline{\mbox{A}}$** 
	- $\overline{\mbox{A}}$ is the set that comprises all elements of U that do not belong to A
- **Difference**
- ![[Pasted image 20251206111748.png | 300]]
	- The difference of sets A and B, or the relative complement of B in A, denoted A - B
	- A - B is the set containing those elements that are in A but not in B
	- Example
		- $\overline{\mbox{A}} = U - A$ 
- **Laws of Set Theory**
	- Similar to logic connectives and formulas, expressions build from set operations and sets also satisfy some laws
	- ![[Pasted image 20251206112106.png|400]]
	- ![[Pasted image 20251206112128.png|400]]
## Relations Between Sets
- Relation is the connection between things or people
	- to be brothers
	- to be greater than
	- to be an owner
- **Cartesian Product**
	- Denoted by $A \times B$ 
	- Set of all ordered pairs of elements from $A$ and $B$ 
	- $A \times B = \{(a,b) | a \in A, b \in B\}$ 
	- If sets are one dimensional objects then cartesian products are two dimensional, can be more
	- ![[Pasted image 20251206112639.png|400]]
## **Binary Relation** 
- A binary relation from set A to set B is any subset of $A \times B$ 
- If A = B then we say that the relation is **on** the set A
- Example
	- $x$ is a brother of $y$ $\subseteq People \times People$ 
- Matrix of a relation
	- Rows are labeled with elements of A
	- Columns are labeled with elements of B
	- We write 1 in the intersection of row a and column b if and only if $(a,b) \in R$ otherwise write 0
	- ![[Pasted image 20251206113336.png|400]]
- Graph of a relation
	- Consists of two sets of vertices labeled by the elements of A and B. A vertex a is connected to vertex b with an edge if and only if $(a,b) \in R$ 
	- ![[Pasted image 20251206113514.png|300]]
## Properties of Binary Relations
- **Reflexivity** 
	- A binary relation $R \subseteq A \times A$ is said to be reflexive if $(a,a) \in R$ for all $a \in R$ 
	- ![[Pasted image 20251206113855.png|400]]
- **Symmetricity**
	- A binary relation $R \subseteq A \times A$ is said to by symmetric if, for any $a,b \in A$, if $(a,b) \in R$
	- ![[Pasted image 20251206114125.png|400]]
- **Transitivity**
	- A binary relation $R \subseteq A \times A$ is said to be transitive if, for any $a,b,c \in A$, if $(a,b) \in R$ and $(b,c) \in R$ then $(a,c) \in R$
	- ![[Pasted image 20251206114339.png|300]]
- **Anti-Symmetricity** 
	-  A binary relation $R \subseteq A \times A$ is said to be anti-symmetric if, for any $a,b \in A$, if $(a,b) \in R$ and $(b,a) \in R$ then $a = b$ 
	- ![[Pasted image 20251206115421.png|400]]
## Orders and Equivalences
- A binary relation R on set A is an **equivalence relations** if it is reflexive, symmetric, and transitive
- A relation R on a set A is called a **(partial) order** if it is reflexive, transitive and anti-symmetric
- Example
	- $a \leq b$ on the set of real numbers 
- Due to being anti-symmetric, all the elements of A are ranked with respect to the order R, that is b is ranked higher than a if $(a,b) \in R$
- ![[Pasted image 20251206115918.png|350]]
- **Minimal and Maximal**
	- ![[Pasted image 20251206120022.png|400]]
	- ![[Pasted image 20251206120043.png|400]]
	- There can be any amount of maximal or minimal elements
	- Can only be 1 least or greatest element
		- If there are two which are equal then there is no least/greatest
## Functions
- A relation R from A to B is called a **function** from A to B
- If for every $a \in A$ there is exactly one $b \in B$ such that $(a,b) \in R$ 
	- This is known as the vertical line test in math
- We use f, g, h to denote functions
	- $f:A \to B$
	- $f(a) = b$
	- $f(Rodriguez) = A$
- **Domain and Codomain** 
	- Let $f:A \to B$, be a function from A to B.
		- A is the **domain** of f
		- B is the **codomain**
	- If $f(a) = b$
		- b is called the image of a
		- a is called the preimage of b
	- Also we say that f maps A to B
	- The **range** of f is that set of all images of elements a
		- all of the possible outputs of a function
- Numerical Functions
	- Can be computed using a formula
		- $f(x) = x^2$
- **One-to-One Functions**
	- Also known as injective functions
	- A function is one to one (injective) if and only if $f(a) = f(b)$ implies $a = b$
	- No two elements are mapped to the same output (image)
- **Onto Functions**
	- Also known as surjective
	- A function is onto (surjective) if and only if for every element $b \in B$ there is an element $a \in A$ with $f(a) = b$ 
	- Every output has some input that obtains it
- **Bijection**
	- Also a one to one correspondence
	- If a function is both one to one and onto then it is a bijection
	- Have to have sets of equal size
		- A set with 6 elements cannot map perfectly to a set with 10 elements
- Composition of Functions
	- Let g be a function from A to B and let f be a function from B to C.
	- Composition of functions
		- $(f \circ g)(a) = f(g(a))$
- Inverse functions
	- Let f be a one to one correspondence from set A to B
		- Required or the inverse function will not map the same as the function
		- If the bijection does not exist then the inverse cannot exist
	- The inverse function of f is the function that assigns to a $b \in B$ the unique element $a \in A$ such that $f(a) = b$
	- Denoted by $f^{-1}(b) = a$ if and only if $f(a) = b$
## Cardinality
- Sets A and B (finite or infinite) have the same cardinality if and only if there is a bijection from A to B
	- $|\mathbb{N}| = |2\mathbb{N}|$ 
	- ![[Pasted image 20251206141325.png|200]]
- A set $A$ is said to be **countable** if $|A| \leq |\mathbb{N}|$ 
	- This is because an injective function from A to $\mathbb{N}$ can be viewed as assigning numbers to the elements of A, thus counting them
- Sets that are not countable are called **uncountable**
- Examples
	- Countable
		- Finite sets: $\{a,b,c\}$
		- Any subset of $\mathbb{N}$
		- $\mathbb{I}$ (integers)
	- Uncountable
		- Real Numbers
		- Irrational Numbers
		- Power Set of Natural Numbers
- **Cantor's Theorem**
	- Theorem: For any set $|P(A)| \gt |A|$
		- The power set of A has more elements then the set A
		- Saying that some infinities are greater than others
	- Proof
		- Imagine you have listed all of the subsets of natural numbers
			- Item 1 pairs with Subset A (e.g. evens)
			- Item 2 pairs with Subset A (e.g. primes)
			- Item 3 pairs with Subset A (e.g. multiples of 10)
			- so on forever
		- Diagonalization: To prove that the list is incomplete we construct a new subset D
			- We build D by looking on the diagonal of the list and doing the opposite
				- Look at item 1, is it inside subset A
					- If YES, we leave it out of D
					- If NO, we add it to D
				- Repeat for all items
		- Contradiction
			- Is this set D on the list
				- Cannot be subset A as it disagrees with the first term
				- Cannot be subset B as it disagrees with the second term 
				- Cannot be the 1000th subset as it disagrees with the 1000th term
		- Conclusion
			- This new set is completely different, therefore the list was incomplete
			- Impossible to list as the infinity of the power set is greater than the infinity of the initial set
## Mathematical Induction
- **Principle of Mathematical Induction** 
	- To prove that a statement that asserts some property $P(n)$ is true for all positive integers n, we complete two steps
	- **Basis Step**: We verify that P(1) is true
		- The base case
	- **Inductive Step**: We show that the conditional statement $P(k) \to P(k + 1)$ is true for all positive integers k
	- To prove the conditional statement we assume that $P(k)$ is true (called the inductive hypothesis) and show that under this assumption $P(k+1)$ is also true
	- The domino effect
		- Base Case
			- The first domino falls
		- Inductive step
			- Whenever a domino falls, its next neighbour will fall
- **Strong Induction** 
	- To prove that $P(n)$ is true for all positive integers n, we complete two steps
	- **Basis Step**: Verify that P(1) is true
		- Same as mathematical induction
	- **Inductive Step**: 
		- Show that $[P(1) \wedge P(2) \wedge \ ... \ \wedge P(k)] \to P(k + 1)$ is true for all positive integers k
- **Well Ordering Principle** 
	- Every non-empty subset of $\mathbb{N}$ contains at least one element
	- Note that the sets of integers, rational numbers, and real numbers do not have this property
- **Structural Induction**
	- To prove properties or design algorithms working with recursively defined structures we need structural induction
	- Two steps
		- Basis Step
			- Prove that the property is true for the simplest structure
		- Inductive Step
			- Assuming that the property is true fir all simpler structures, prove it for a more complex structure
## Integers
- If a and b are integers with $a \neq 0$, we say that a divides $b$ if there is an integer $c$ such that $b = ac$
- When $a$ divides $b$ we say that $a$ is a **divisor (factor)** of $b$, and $b$ is a **multiple** of $a$
- **Properties of Divisibility**
	- if $a \ | \ b$ and $a \ | \ c$ then $a \ | \ (b + c)$
	- if $a \ | \ b$ then $a \ | \ b \times c$ for all integers $c$
	- if $a \ | \ b$ and $b \ | \ c$ then $a \ | \ c$
- **The Division Algorithm**
	- **Theorem**: Let $a$ be an integer and $d$ a positive integer. Then there are unique integers $q$ and $r$ with $0 \leq r \lt d$ , such that $a = dq + r$
	- $d$ is called the divisor, $a$ is the dividend, $q$ is called the quotient, and $r$ is called the remainder
	- Example
		- Let $a = 101$ and $d = 11$
		- Then $101 = 11 \times 9 + 2$ 
- **Composite Numbers**
	- Positive number that is not prime
	- Has a prime divisor
### Common Divisors 
- For integers $a$ and $b$, a positive integer $c$ is said to be a common divisor of $a$ and $b$ if $c \ | \ a$ and $c \ | \ b$
- Let $a, b$ be integers such that $a \ne 0, b \ne 0$, then a positive integer $c$ is called the greatest common divisor (GCD) of $a,b$ 
	- $c \ | \ a$ and $c \ | \ b$ 
	- for any common divisor $d$ of $a$ and $b$, we have $d \ | \ c$
- Euclidian Algorithm
	- To find the $\gcd(a,b)$
	1. Divide $a$ by $b$ to find $r$
	2. Shift
		- The old $b$ becomes the new $a$
		- The old $r$ becomes the new $b$
	3. Repeat until the remainder is 0
	4. Last non-zero divisor is the gcd
- Fundamental Theorem of Arithmetic
	- Every integer n > 1 can be represented as a product of primes uniquely
### Least Common Multiple
- A positive integer $c$ is called a common multiple of integers $a$ and $b$ if $a \ | \ c$ and $b \ | \ c$
- Formula: $\frac{|a \times b|}{gcd(a,b)}$ 
## Congruences
- If $a$ and $b$ are integers and $m$ is a positive integer, then $a$ is congruent to $b$ modulo $m$ if $m$ divides $a - b$ 
- Notation: $a \equiv b (mod \ m)$ 
- Can do addition, subtraction, multiplication, and still be equivalent but not division
### Chinese Remainder Theorem
- Method to find a mystery number if you only know what the remainder is when you divide that number by different divisors
- Condition: Divisors have to be co-prime (not share any factors)
	- 1. Write equation of congruences
	- 2. Substitute: Plug the first equation into the second
	- 3. Solve: Find the var that makes it true
	- 4. Repeat: Repeat for all equations


$x \equiv 3 \pmod 5$ 
$x \equiv 2 \pmod 7$ 
$x \equiv 2 \pmod 9$ 

$x = 7k + 2$ 
$7k + 2 \equiv 3 \pmod 5$
k = 3

1 = 9
2 = 16 (inverse)
3 = ****23****
x = 23
$x = 9k + 2$ 
$9k + 2 \equiv 3 \pmod 5$
11
20
29
38 * 23 = 


x = 5 x 7