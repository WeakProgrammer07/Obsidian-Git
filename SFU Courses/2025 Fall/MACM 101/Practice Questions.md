# MACM 101: Targeted Practice Final Exam

**Instructions:** This practice set focuses on the specific "danger zones" identified from your Midterm 1 & 2 results, combined with the new topics appearing on the sample final.

---

## Part 1: Definitions & Concepts (The "danger zones")

**1. The Well-Ordering Trap**
(a) Define the **Well-Ordering Principle**.
- The well ordering principle states that for any non-empty subset of the natural numbers there is a least element.
(b) Is the set of Integers ($\mathbb{Z}$) well-ordered? Explain why or why not.
- No it cannot, this is because it has the negative numbers, so there is no floor for it to stop at.
(c) Is the set of Positive Rational Numbers ($\mathbb{Q}^+$) well-ordered? Explain why or why not.
- Yes, there is a floor so that means there can only be numbers above 0. So we can apply well ordering

**2. Functions on Real Numbers**
Let $f: \mathbb{R} \to \mathbb{R}$ be defined by $f(x) = 2x + 1$.
(a) Is $f$ **surjective** (onto)? Prove it by showing that for any $y$, there exists an $x$.
- This is onto, because it is for real numbers there will always be a corresponding output, and every output is covered. 
- Example
	- if we want f(x) to be 3 then we can have a x value that maps to an output of 3
(b) Is $f$ **injective** (one-to-one)? Prove it.
- Yes it is injective, becuase it is imposible for two x values to have the same value, and there is no step that makes it equal to another (ie squaring)

**3. Orders (Greatest vs. Maximal)**
Consider the relation of **divisibility** ($a \mid b$) on the set $A = \{2, 3, 4, 6, 12, 18\}$
(a) Draw the **Hasse Diagram** for this relation.
- Generate Image for this please
(b) Identify all **Maximal** elements.
- The maximal elements is 2,3,4,6
(c) Identify the **Greatest** element (if it exists).
- 2
(d) Identify all **Minimal** elements.
- 12 and 18

---

## Part 2: Proofs & Logic

**4. Logical Equivalence**
Without using a truth table (use logical laws), show that:
$$p \to (q \to r) \iff (p \wedge q) \to r$$
$\neg p \vee (\neg q \vee r) \iff \neg(p \wedge q) \vee r$ 
$\neg p \vee \neg q \vee r \iff \neg p \vee \neg q \vee r$ 
**5. Induction**
Prove by mathematical induction that for all integers $n \ge 1$:
$$1 + 3 + 5 + \dots + (2n - 1) = n^2$$
show that P(k) is true for base case (n = 1)
$(2n - 1) = n^2$ 
$(2(1) - 1) = 1^2$
$(2 - 1) = 1$
$1 = 1$


**6. Sets**
Prove that if $A \subseteq B$, then $P(A) \subseteq P(B)$. (Where $P(A)$ is the power set of A).
Let A = {0,2}
let B = {0,1,2}
since all elements of A are in B then A is a subset of B. 
P(A) = {{},{0},{2},{0,2}}
P(B) = {{},{0},{1},{2},{0,1},{0,2},{1,2},{0,1,2}}
Because when you take the power set of a set you get all of the possible subsets this means that since A is a subset of B then the set of A will be in the set of B, and when the power set of B is taken then that subset (set A) is also taken and is some of the sets, this means that P(A) will be in the P(B)

---

## Part 3: New Topics (Number Theory & Graphs)

**7. Chinese Remainder Theorem**
Solve the following system of congruences for $x$:
$$x \equiv 2 \pmod 3$$
$$x \equiv 3 \pmod 5$$
*(Show your steps using the substitution or construction method).*
$x = 3k +2$
$3k + 2 \equiv 3 \pmod 5$ 
$3k \equiv 1 \pmod 5$ 
test k = 1 (nope)
test k = 2 (yep)

$x = 3(2) + 2$ 
$x = 8$ 


**8. Graph Theory**
(a) Define what it means for a graph to be a **Tree**.
- A tree is a connected graph, where one element is pendant, and there are no cycles
(b) A graph $G$ has 10 vertices and 9 edges. Is $G$ automatically a tree? Explain.
- No, because it might not be connected
(c) Determine the **GCD(270, 192)** using the Euclidean Algorithm.
$270 = 192 + 78$
$192 = 2(78) + 36$ 
$78 = 2(36) + 6$
$36 = 6(6) + 0$
$GCD(270,192) = 6$
# Answer Key

## 1. Well-Ordering
* **(a)** Every **non-empty** subset of the set contains a **least** (smallest) element.
* **(b) No.** The set of negative integers $\{-1, -2, -3, \dots\}$ has no smallest element; it goes down to $-\infty$.
* **(c) No.** The set $\{ x \in \mathbb{Q}^+ \mid x > 2 \}$ has no smallest element. For any fraction $2 + \epsilon$ you pick, I can pick a smaller one $2 + \epsilon/2$.

## 2. Functions
* **(a) Surjective:** Yes. Let $y \in \mathbb{R}$. We need $2x + 1 = y$. Solving for $x$ gives $x = (y-1)/2$. Since $(y-1)/2$ is a valid real number for any $y$, the function is onto.
* **(b) Injective:** Yes. Assume $f(a) = f(b)$. Then $2a + 1 = 2b + 1 \implies 2a = 2b \implies a = b$.

## 3. Orders (Divisibility on $\{2, 3, 4, 6, 12, 18\}$)
* **(a) Diagram:**
    * 12 is above 4 and 6.
    * 18 is above 6 (and 9 if it were in the set, but 9 isn't). 18 is above 3 (via 6) and 2 (via 6).
    * 4 is above 2.
    * 6 is above 2 and 3.
* **(b) Maximal:** 12, 18 (Nothing divides them in this set).
* **(c) Greatest:** **None.** (There is no single number that is divisible by *everything* else. 12 is not divisible by 18, and 18 is not divisible by 12).
* **(d) Minimal:** 2, 3 (Nothing in the set divides them).

## 4. Logic
* $p \to (q \to r)$
* $\equiv \neg p \vee (\neg q \vee r)$ (Implication law)
* $\equiv (\neg p \vee \neg q) \vee r$ (Associative law)
* $\equiv \neg (p \wedge q) \vee r$ (De Morgan's law)
* $\equiv (p \wedge q) \to r$ (Implication law)

## 5. Induction
* **Base case ($n=1$):** $2(1)-1 = 1^2 \implies 1 = 1$. True.
* **Hypothesis:** Assume $\sum_{i=1}^k (2i-1) = k^2$.
* **Step:** Show for $k+1$.
    * Sum $= k^2 + (2(k+1) - 1)$
    * $= k^2 + 2k + 2 - 1$
    * $= k^2 + 2k + 1$
    * $= (k+1)^2$. True.

## 6. Sets
* Let $X$ be an arbitrary element of $P(A)$. By definition, $X \subseteq A$.
* Since $A \subseteq B$ (premise), and $X \subseteq A$, it follows that $X \subseteq B$.
* Since $X \subseteq B$, then by definition $X \in P(B)$.
* Therefore, $P(A) \subseteq P(B)$.

## 7. Chinese Remainder Theorem
* Eq 1: $x = 3k + 2$.
* Sub into Eq 2: $3k + 2 \equiv 3 \pmod 5$.
* $3k \equiv 1 \pmod 5$.
* Find inverse of 3 mod 5 (it is 2, because $3 \times 2 = 6 \equiv 1$).
* Multiply by 2: $k \equiv 2(1) \pmod 5 \implies k \equiv 2 \pmod 5$.
* So $k = 5j + 2$.
* Sub back into Eq 1: $x = 3(5j + 2) + 2 = 15j + 6 + 2 = 15j + 8$.
* **Solution:** $x \equiv 8 \pmod{15}$.

## 8. Graphs
* **(a)** A connected graph with no cycles.
* **(b) No.** It implies it has a cycle. A Tree with $n$ vertices must have exactly $n-1$ edges. If it has $n$ edges (10 vertices, 10 edges), it contains exactly one cycle (if connected). With 9 edges, it *could* be a tree if connected, but if strictly $n$ edges, no.
    * *Correction for the specific question asked (10 vertices, 9 edges):* The condition for a tree is $n$ vertices and $n-1$ edges **AND** connected. Just having 9 edges isn't enough (it could be disconnected).
* **(c) GCD(270, 192):**
    * $270 = 1(192) + 78$
    * $192 = 2(78) + 36$
    * $78 = 2(36) + 6$
    * $36 = 6(6) + 0$
    * **GCD is 6.**

