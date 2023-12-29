+++
title = "A nonempty perfect set in the reals that avoids rationals"
date = 2023-12-21
updated = 2023-12-29
+++

One of the notoriously hard questions in Rudin's *Principles of Mathematical Analysis* asks you to construct a nonempty perfect set in \\(\mathbb{R}\\) that contains no points of \\(\mathbb{Q}\\).

Well, it's hard because it's just so *awkward* to do with just the tools Rudin himself furnishes up until that point in the book.

There's [a solution](https://math.stackexchange.com/questions/178631/perfect-set-in-mathbbr-which-contains-no-rational-number) that shows up as the first or maybe the second result when you search this question: 

It asks you to enumerate the rationals \\(q_1, q_2, q_3, \ldots \\), and, for each \\(n\\), you delete from \\(\mathbb{R}\\) an open interval of width \\(2^{-n}\\) that contains \\(q_n\\). We end up with a closed subset \\(E\\) of \\(\mathbb{R}\\) that has positive (namely infinite) Lebesgue measure, which tells us that it is uncountable.

Then, once you utter the magic words *Cantor-Bendixson Theorem*, you know that this closed uncountable subset of \\(\mathbb{R}\\) has a decomposition as the disjoint union of a countable set and a perfect set, and voilà! This perfect subset of \\(E\\) must avoid \\(\mathbb{Q}\\) since \\(E\\) avoids \\(\mathbb{Q}\\) already, by construction.

The invocation of Cantor-Bendixson is "honest"-- it appears as another exercise in the same chapter, but the measure-theoretic argument? Not quite. And having this "dishonest" part of an answer tends to be the case. A lot of arguments you look up need sophistication that just isn't there yet in the book.


I was having a conversation with James Pascoe (prof at my uni-- AWESOME PERSON!) about this question, and he told me I could maybe do something clever with the decimal expansions of real numbers, perhaps maybe changing the digits at the \\((n^2)\\)-th places, moving numbers by "very little".

And so I ran with it! Here is my answer. It's going to be pretty long since I want to put down every detail.

We start by making "decimal expansions" very precise, at least as much as we're going to need for this problem.

---

### Lemma (base-\\(p\\) existence)

Let \\(p\\) be an integer such that \\(p \geq 2\\). Every \\(x \in [0, 1]\\) admits a *base-\\(p\\) expansion*, which is a sequence of integers \\(a_1, a_2, a_3, \ldots\\) such that \\(0 \leq a_k < p \\) for all \\(k\\) and
$$x = \sum_{k=1}^\infty \frac{a_k}{p^k}$$

and we will denote this infinite sum as 

$$0.a_1a_2a_3\ldots$$

### Proof

For all \\(k\\), let \\(M_k\\) be the largest integer such that \\(M_k \leq x \cdot p^k\\), which exists by \\(\mathbb{R}\\)'s Archimedean property (take the smallest integer greater, and let \\(M_k\\) be that minus one). Then \\(M_k\\) is the largest integer such that

$$\frac{M_k}{p^k} \leq x$$

We note that 

$$\frac{pM_k}{p^{k+1}} \leq x$$

so \\(pM_k \leq M_{k+1}\\), and we have that \\(M_{k+1}-pM_k \geq 0 \\).

Also, \\(M_{k+1} - pM_k < p\\). Suppose otherwise, then

$$M_{k+1} - pM_k \geq p$$
$$M_{k+1} \geq p(M_k+1)$$
$$p(M_k+1) \leq M_{k+1}$$
$$\frac{p(M_k+1)}{p^{k+1}} \leq \frac{M_{k+1}}{p^{k+1}}$$
$$\frac{pM_k}{p^{k+1}} \leq \frac{p(M_k+1)}{p^{k+1}} \leq \frac{M_{k+1}}{p^{k+1}} \leq x$$

So we have that 

$$\frac{M_k}{p^k} \leq \frac{M_{k}+1}{p^k} \leq x$$

Which contradicts \\(M_k\\)'s maximality. Then we define \\(a_1 := M_1\\), \\(a_k := M_{k+1} - pM_k\\) for \\(k \geq 2 \\), and we have that \\(0 \leq a_k < p\\) for all \\(k\\).

We claim that, as promised,

$$x = \sum_{k=1}^\infty \frac{a_k}{p^k}$$

First, we derive an easy formula for the partial sums \\(A_N := \sum_{k=1}^N a_k/p^{k}\\)

$$A_N = \frac{M_N}{p^N}$$

Which we prove by induction on \\(k\\). By definition, \\(A_1 = a_1/p^1 = M_1/p^1 \\). Suppose \\(A_N = M_N/p^N\\), then

\\[\begin{align}
A_{N+1} &= A_N + \frac{a_{N+1}}{p^{N+1}} \\\\
&= \frac{M_N}{p^N} + \frac{M_{N+1} - pM_N}{p^{N+1}} \\\\
&= \frac{pM_N}{p^{N+1}} + \frac{M_{N+1} - pM_N}{p^{N+1}} \\\\
&= \frac{M_{N+1}}{p^{N+1}} \\\\
\end{align}
\\]

Then we prove convergence, as, since 
\\[\frac{M_n}{p^n} \leq x < \frac{M_n + 1}{p^n}\\]
we have that
\\[x  - \frac{M_n}{p^n} < \frac{1}{p^n}\\]
so
\\[|x-A_n| = \left|x - \frac{M_n}{p^n}\right| = x - \frac{M_n}{p^n} \leq \frac{1}{p^n}\\]
and now for all \\(\varepsilon\\) we just choose \\(N\\) such that \\(p^{-N} < \varepsilon\\). Then, we get the result
\\[x = \lim_{n \to \infty} A_n = \sum_{k=1}^\infty \frac{a_k}{p^k}\\]
where \\(0 \leq a_k < p \\) for all \\(k\\). \\(\Box\\)

---

### Lemma (base-\\(p\\) uniqueness)

The base-\\(p\\) expansion of a real number \\(x \in [0,1]\\) is unique, except possibly for the case that it has a tail consisting entirely of \\(0\\)s or \\((p-1)\\)s, i.e, there exists \\(N\\) such that \\(a_n = 0\\) for all \\(n > N\\), and similarly for the \\(p-1\\) case.

### Proof 

Let \\(x = 0.a_1a_2a_3\ldots\\) and \\(y = 0.b_1b_2b_3\ldots\\). We will show that if \\(a_k\\) and \\(b_k\\) differ then in general \\(x \neq y\\). Let \\(N\\) be the smallest integer for which \\(a_N \neq b_N\\). Then

\\[
\begin{align}
x - y &= \sum_{k=1}^\infty \frac{a_k}{p^k} - \sum_{k=1}^\infty \frac{b_k}{p^k}\\\\
&= \sum_{k=1}^\infty \left[\frac{a_k}{p^k} - \frac{b_k}{p^k}\right] \\\\
&= \sum_{k=1}^\infty \frac{a_k-b_k}{p^k} \\\\
&= \sum_{k=N}^\infty \frac{a_k-b_k}{p^k} \\\\
&= \frac{a_N-b_N}{p^N} + \sum_{k=N+1}^\infty \frac{a_k-b_k}{p^k} \\\\
&= \frac{a_N-b_N}{p^N} - \sum_{k=N+1}^\infty \frac{b_k-a_k}{p^k}
\end{align}\\]

And we invoke the reverse triangle inequality

\\[|x-y| \geq \left|\left|\frac{a_N-b_N}{p^N}\right| - \left|\sum_{k=N+1}^\infty \frac{b_k-a_k}{p^k}\right|\right|\\]

Since \\(b_k < p\\) and \\(a_k \geq 0\\), \\(b_k - a_k \leq p-1\\). By comparison, the largest possible value for \\(\sum_{k=N+1}^\infty \frac{a_k-b_k}{p^k}\\) is 

\\[\begin{align}
\sum_{k=N+1}^\infty \frac{p-1}{p^k} &= (p-1)\sum_{k=N+1}^\infty p^{-k}\\\\
&= (p-1)(p^{-(N+1)})\sum_{k=0}^\infty p^{-k} \\\\
&= p^{-(N+1)}\frac{p-1}{1-p^{-1}} \\\\
&= p^{-(N+1)}\frac{p-1}{\frac{p-1}{p}} \\\\
&= \frac{1}{p^N} 
\end{align}\\]

Which is only attainable if \\(b_k = p-1\\) and \\(a_k = 0\\) for all \\(k > N \\). 
\\[x-y \leq \frac{a_N-b_N}{p^N} + \frac{1}{p^N}\\]

Similarly, we get a lower bound \\(-1/p^N\\) if \\(b_k = 0\\) and \\(a_k = p-1\\) for all \\(k > N\\), so 

\\[\left|\sum_{k=N+1}^\infty \frac{b_k-a_k}{p^k} \right| \leq \frac{1}{p^N}\\]

Then with the exception of these two cases, we have in general

\\[\left|\sum_{k=N+1}^\infty \frac{b_k-a_k}{p^k} \right| < \frac{1}{p^N}\\]

Then, since \\(|a_N-b_N| \geq 1\\), being two unequal integers,

\\[\left|\frac{a_N-b_N}{p^N}\right| - \left|\sum_{k=N+1}^\infty \frac{b_k-a_k}{p^k}\right| > \frac{1}{p^N} - \frac{1}{p^N} = 0\\]

Then 

\\[|x-y| \geq \left|\left|\frac{a_N-b_N}{p^N}\right| - \left|\sum_{k=N+1}^\infty \frac{b_k-a_k}{p^k}\right|\right| > 0 \\]

so \\(x \neq y \\). \\(\Box\\)

---

Then we note a basic but important fact about expansions and rational numbers

---

### Lemma

A number \\(x = 0.a_1a_2a_3\ldots\\) is rational if and only if its base-\\(p\\) expansion is *eventually periodic*, which means there exist positive integers \\(N\\) and \\(P\\) such that

\\[a_n = a_{n+P}\\]

for all \\(n \geq N \\)

### Proof

Suppose \\(x \in [0, 1]\\) is rational, and let \\(x = a/b\\), where \\(a\\) and \\(b\\) are two coprime integers.

For all  \\(k > 0\\). We have that
\\[\frac{M_k}{p^k} \leq \frac{a}{b}\\]
\\[M_k \leq \frac{ap^k}{b} \\]
We note that, in this restriction, the definition of \\(M_k\\) coincides with the Euclidean division of \\(ap^k\\) by \\(b\\), i.e it is the unique number such that
\\[ap^k = bM_k + r_k\\]
where \\(0 \leq r_k < b\\). Define \\(r_k\\) this way for all \\(k\\). Then
\\[\frac{ap^k}{b} = \frac{bM_k+r_k}{b} = M_k + \frac{r_k}{b} \\]
Then
\\[\frac{ap^{k+1}}{b} = p\frac{ap^k}{b} = pM_k + \frac{pr_k}{b}\\]
and, if we further define with another application of Euclidean division, integers \\(m_k\\) and \\(r'\_k\\) 
\\[pr_k = bm_k + r'\_k\\]
such that \\(0 \leq r'\_k \leq b \\), we get that
\\[\frac{ap^{k+1}}{b} = (pM_k + m_k) + \frac{r'\_k}{b}\\]
By uniqueness of Euclidean division, we have that
\\[M_{k+1} = pM_k + m_k\\]
\\[r_{k+1} = r'\_k\\]
Since the \\(k\\)th digit of \\(x\\) is given by \\(M_{k+1} - pM_k\\),
\\[a_k = M_{k+1} - pM_k = (pM_k + m_k) - pM_k = m_k\\]
And so we have shown that computing the digits of a rational number's expansion can be done purely by
repeating Euclidean division recursively, giving us
\\[pr_k = ba_k + r_{k+1}\\]
Then the value of \\(a_k\\) is completely determined by \\(r_k\\). But any function from a finite set to itself is eventually periodic when iterated! Then we have that the digits \\(a_k\\) are eventually periodic. [under construction]

For the reverse, suppose the expansion is eventually periodic. Then we may split it into a periodic part and a finite non-periodic part. The former is rational, as it it can be written as a geometric series with a rational ratio, and the latter is also rational, as it is just a finite sum of rational numbers. \\(\Box\\)

[under construction]

---

And so we're ready! I'm getting a little tired as I write this, so the following won't be as detailed as the lemmas. I'll edit this later, I promise...

---

### Theorem

There exists a nonempty perfect subset of \\(\mathbb{R}\\) that contains no points of \\(\mathbb{Q}\\).

### Proof

Let \\(E\\) be the subset of \\([0, 1]\\) consisting of numbers whose base-\\(5\\) expansions consist of only the numbers \\(1\\) and \\(3\\).

This set is perfect. We will construct, for each point \\(x \in E\\), an infinite sequence \\(x_n\\) of *distinct* numbers of \\(E\\) such that \\(x_n \to x\\) as \\(n \to \infty\\). This suffices to prove that \\(E\\) is perfect.

Let \\(x \in E\\). Let \\(x = 0.a_1a_2a_3\ldots\\). Define \\(x_n\\) to be

\\[
x_n := 0.a^{(n)}_1 a^{(n)}_2 a^{(n)}_3\ldots
\\]

where

\\[
a^{(n)}_k = \begin{cases}
a_k & \text{ if } k \leq n \\\\
1 & \text{ if } k \geq n \text{ and } a_k = 3 \\\\
3 & \text{ if } k \leq n \text{ and } a_k = 1 \\\\
\end{cases}
\\]

So, each \\(x_n\\) agrees with \\(x\\)'s base-\\(5\\) expansion up until the \\(n\\)-th digit, from which point it simply 'flips' each digit. Clearly \\(x_n \neq x\\) for all \\(n\\), and we also find that

\\[|x_n - x| \leq \frac{1}{5^n}\\]

which shows that \\(x_n \to x\\) as \\(n \to \infty\\).

For any real number \\(\alpha\\) and any set \\(G\\), define the set 

\\[\alpha + G := \\{ \alpha + x : x \in E\\}\\]

Its easy to show that if \\(G\\) is perfect, then \\(G + \alpha\\) remains perfect for any \\(\alpha\\). [under construction]

Then, we choose \\(\alpha\\) to be equal to 

\\[0.10100100010000100001\ldots\\]

We note that \\(\alpha\\) is irrational, as it cannot be eventually periodic. [under construction]

Then we consider the set \\(\alpha + E\\), which is still perfect as \\(E\\) is perfect. Consider \\(x \in E\\). If \\(x\\) is rational, then clearly \\(x + \alpha\\) is irrational as \\(\alpha\\) is irrational.

If \\(x\\) is irrational, then \\(x + \alpha\\) is irrational, for the same reason \\(\alpha\\) itself is irrational-- it cannot be eventually periodic. [under construction]

Then \\(\alpha + E\\) is exactly the set desired. \\(\Box\\)
