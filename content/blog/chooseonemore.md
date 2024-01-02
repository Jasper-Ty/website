+++
title = "Choosing one more by double counting"
date = 2024-01-02
updated = 2024-01-02
+++

By manipulating the factorials involved in the formula for binomial coefficients, one gets the identity

\\[{n \choose k+1} = \frac{n-k}{k+1}{n \choose k}\\]

I stumbled on a *really simple* combinatorial proof: Consider strings (of length \\(n\\)) consisting of \\(1\\) ★, \\(k\\) 1's, and \\(n-k-1\\) 0's. e.g

<center>011001★00011110</center>

We can count these in two ways:

---

Choose a binary string with \\(n-k\\) 0's \\(k\\) 1's. Replace a 0 in the string with ★.  

<center>011001 0 00011110 -> 011001 ★ 00011110</center>

There are \\(n-k\\) zeros, so there are \\((n-k){n \choose k}\\) ways to do this

---

Choose a binary string with \\(n-k-1\\) 0's \\(k+1\\) 1's. Replace a 1 in the string with ★. 

<center>011001 1 00011110 -> 011001 ★ 00011110</center>

There are \\(k+1\\) ones, so there are \\((k+1){n \choose k+1}\\) ways to do this

---

Then we have

\\[(k+1){n \choose k+1} = (n-k){n \choose k}\\]

and so

\\[{n \choose k+1} = \frac{n-k}{k+1}{n \choose k}\\]
