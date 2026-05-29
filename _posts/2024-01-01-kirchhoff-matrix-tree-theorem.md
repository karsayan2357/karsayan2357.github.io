---
title: "Kirchhoff Matrix-Tree Theorem"
date: 2024-01-01
layout: single
author_profile: true
katex: true
---

A spanning subgraph of a graph $X = (V, E)$ is a subgraph whose vertex set is exactly $V$, obtained by deleting some (possibly none) edges. A spanning tree of $X$ is a spanning subgraph that is also a tree, i.e., connected and acyclic. We denote by $\tau(X)$ the number of spanning trees of $X$; in particular, $X$ is connected if and only if $\tau(X) > 0$. The problem of counting spanning trees is central in graph theory, and in this article we study the Kirchhoff Matrix Tree Theorem, which gives a matrix-based method to compute $\tau(X)$.

Our goal is to compute $\tau(X)$, the number of spanning trees of a connected graph $X$. Rather than enumerating all possible trees directly, which quickly becomes infeasible, we seek a systematic and efficient method to determine this quantity.

The *contraction* of a graph $X$ by an edge $e$ with endpoints $x$ and $y$ is the graph obtained by merging $x$ and $y$ into a single vertex. All edges that were incident to $x$ or $y$, except $e$ itself, remain incident to the new vertex. The resulting multigraph, denoted $X/e$, has one fewer edge than $X$.

<div class="theorem">
Let $X$ be a graph. If $e$ is an edge of $X$ that is not a loop, then
$$\tau(X) = \tau(X - e) + \tau(X / e).$$
</div>

<div class="proof">
The number of spanning trees $\tau(X)$ of $X$ equals the sum of the number of spanning trees that do not contain $e$ and the number of spanning trees that do contain $e$. The spanning trees of $X$ that omit $e$ are counted by $\tau(X - e)$. The family of spanning trees that contain $e$ is in bijective correspondence with the set of spanning trees of $X / e$. When we contract $e$ in a spanning tree that contains $e$, we obtain a spanning tree of $X / e$ because the resulting subgraph is spanning, connected, and has the correct number of edges. Since other edges maintain their identity under contraction, no two trees map to the same spanning tree of $X / e$, and each spanning tree of $X$ arises this way.
</div>

Now that we have seen the recursive relation for counting spanning trees, we shall move on to the main theorem, which provides a closed-form formula to compute $\tau(X)$ directly using matrices associated with the graph.

For a matrix $M$, we denote by $M[i]$ the matrix obtained by removing the $i$-th row and $i$-th column, and by $M[i,j]$ the matrix obtained by removing the $i$-th row and $j$-th column.

<div class="theorem">
<strong>Kirchhoff's Matrix-Tree Theorem.</strong> Let $X$ be a graph with vertex set $[n]$ for some $n \ge 1$ and Laplacian matrix $L$. Then:
<ol>
<li>For any $i \in [n]$, $\tau(X) = \det L[i]$.</li>
<li>For any $i,j \in [n]$, $\tau(X) = (-1)^{i+j} \det L[i,j]$.</li>
<li>$\mathrm{adj}(L) = \tau(X) J_n$.</li>
<li>$\tau(X) = n^{-2} \det(J_n + L)$.</li>
<li>If $0 = \mu_1 \le \mu_2 \le \dots \le \mu_n$ are the eigenvalues of $L$, then $\tau(X) = \dfrac{\mu_2 \cdots \mu_n}{n}$.</li>
</ol>
</div>

<div class="proof">
Clearly, part (2) is a generalization of part (1), but we prove (1) first and use it to establish (2). We proceed by strong induction on the number of edges, leaving the base case to the reader. Let $e = ij$ be an edge of $X$, and denote by $E$ the $([n] \setminus \{i\}) \times ([n] \setminus \{i\})$ matrix with all entries zero except $E[j,j] = 1$. Note that

$$L[i] = L(X-e)[i] + E$$

This implies

$$\det L[i] = \det L(X-e)[i] + \det L(X-e)[i,j] = \det L(X-e)[i] + \det L[i,j]$$

since $L(X-e)[i,j] = L[i,j]$. When contracting the edge $e = ij$ and forming $X/e$, assume the vertex set of $X/e$ is $[n] \setminus \{i\}$. Then $L(X/e)[j] = L[i,j]$. By the induction hypothesis,

$$\det L(X-e)[i] = \tau(X-e), \quad \det L(X/e)[i] = \tau(X/e)$$

Thus, by the above theorem,

$$\det L[i] = \tau(X-e) + \tau(X/e) = \tau(X)$$

which proves part (1). For parts (2) and (3), note that $\mathrm{adj}(L)L = L\,\mathrm{adj}(L) = \det(L) I_n = 0$ since $L$ has $0$ as an eigenvalue. This implies that each column of $\mathrm{adj}(L)$ lies in the eigenspace corresponding to the eigenvalue $0$ of $L$. By properties of Laplacian matrices, all entries of any column of $\mathrm{adj}(L)$ are equal, and the diagonal entries equal $\tau(X)$. Hence $\mathrm{adj}(L) = \tau(X) J_n$.

For part (4), note that $J_n^2 = n J_n$ and $J_n L = L J_n = O_n$. Then $(n I_n - J_n)(J_n + L) = n L$, so

$$\mathrm{adj}(nL) = \mathrm{adj}((n I_n - J_n)(J_n + L)) = \mathrm{adj}(J_n + L)\, \mathrm{adj}(n I_n - J_n)$$

Using Cayley's formula, $\mathrm{adj}(n I_n - J_n) = n^{n-2} J_n$ and $\mathrm{adj}(n L) = n^{n-1} \mathrm{adj}(L)$, giving

$$n\, \mathrm{adj}(L) = [\mathrm{adj}(J_n + L)] J_n \implies n \tau(X) J_n = [\mathrm{adj}(J_n + L)] J_n$$

Multiplying both sides by $J_n + L$ on the left yields the desired result. Finally, for part (5), the eigenvalues of $J_n + L$ are $n, \mu_2, \dots, \mu_n$, so $\det(J_n + L) = n \prod_{j=2}^{n} \mu_j$, and part (4) gives

$$\tau(X) = \frac{\mu_2 \cdots \mu_n}{n}$$
</div>