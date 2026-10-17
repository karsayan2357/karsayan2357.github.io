---
title: "Connecting Catalan Numbers and the Data Structure Stack"
date: 2026-10-17
layout: single
author_profile: true
katex: true
---

In this blog, we shall see a connection between the famous [Catalan Number](https://en.wikipedia.org/wiki/Catalan_number) and the abstract data structure [Stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type)).  
## Set-Up 
 We shall do the following process to obtain certain permutations of $\{1, \ldots, n\}$ using a stack. 

**Process.** $\texttt{PUSH}$ $1, \ldots, n$ in this order with $\texttt{POP}$'s allowed in any intermediate step. The final $\texttt{POP}$-ed string is a permutation of $\{1, \ldots, n\}$. 

Now the interesting thing here is that when we try to count the number of permutations obtainable from here, Catalan number pops out! 

$\textbf{Theorem.}$ The number of permutations obtainable from the above process is $C_{n} = \dfrac{1}{n+1}\dbinom{2n}{n}$.

Before actually proving the proposition of interest here, let us see a very relevant definition of Catalan numbers here that will help us obtain the former mentioned proposition. 

##### Relevant Definition of Catalan Numbers
Consider the set-up where we have $n$ many left and $n$ many right brackets and we want to arrange them in an order such that the total arrangement is $\textit{balanced}$. Formally it means that the final string of these brackets satisfy the following two properties:
1. The number of "\[" in the string is same as the number of "\]".
2. For any prefix string, the number of "\[" $\geq$ the number of "\]".
Now the number of $balanced$ parantheses using $n$ many left and right brackets is known as the $n$-th Catalan number, denoted as $C_{n}$. 

Now the obvious question is the relevance of this definition. Observe that if we can show a bijective correspondence between an instance of $balanced$ paranthese with an instance of an obtainable permutation with out set-up, we can prove the desired proposition.

##### Equivalence of $balanced$ parantheses and our Set-Up
We shall try to define a bijective map between the two following sets:
$$
A = \left\{ x \in \{ [,] \}^* \mid x \text{ is balanced} \right\}  \quad \text{and}\quad B = \left\{ \sigma\in S_{n} \mid \sigma \text{ is obtainable} \right\}.
$$
Let us first note that an obtainable $\sigma$ is induced by a sequence of $\texttt{PUSH}$'s and $\texttt{POP}$'s with the number of each call $n$. Now the following important question comes,

Question. What kind of $\texttt{PUSH-POP}$ sequences give an obtainable permutation?

The answer to it is fairly simple, of course the number of $\texttt{PUSH}$ is equal to the number of $\texttt{POP}$. But to ensure that we have valid $\texttt{PUSH-POP}$ operations, at any prefix string of this $\texttt{PUSH-POP}$ sequence, the number of $\texttt{PUSH}$ is greater than or equal to number of $\texttt{POP}$. So one can see an equivalence between $balanced$ paranthese and the set of valid $\texttt{PUSH-POP}$ operations, we define a bijection $f:A\to\{\text{valid \texttt{PUSH-POP} sequence}\}$ by just replacing "\[" with $\texttt{PUSH}$ and "\]" with $\texttt{POP}$. We shall use this to find a bijection from $A$ to $B$.

Define the bijection $\varphi:A\to B$ as follows, if $h:\{\text{valid \texttt{PUSH-POP} sequence}\}\to B$ is the trivial bijection for our setup, the $\varphi = h\circ f$.

Showing $\varphi$ is trivial, hence we have established an equivalence between $A$ and $B$. Thus we can conclude: 
$$
\# B = \# A = C_{n}.
$$

