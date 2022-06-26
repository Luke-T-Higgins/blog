---
layout: post
title: "The Euler Characteristic"
---

To show that two topological spaces are not homeomorphic we make use of _topological invariants_: a number or an attribute of a space which remains constant under continuous deformation. If the two spaces disagree on this invariant, they cannot be homeomorphic.

This post aims at introducing the Euler characteristic, a topological invariant, in a few different contexts. The first section of this post will introduce the Euler characteristic for graphs, the second for [simplicial complexes](https://lukethiggins.com/2022/02/16/surfaces-and-simplicial-complexes), and the third for [closed surfaces](https://lukethiggins.com/2022/02/16/surfaces-and-simplicial-complexes).

## 1
A **graph** is a collection of vertices and edges which connect some of those vertices, graphs are called **finite** when the number of vertices and edges is finite. A **connected graph** is a graph in which all vertices are conneced to at least one other vertex via an edge. (All graphs in this post will be finite and connected so these distinctions are not made going forward.) If you can travel around some of the edges of a graph and get back to where you started, without back-tracking on any edge, we call the path you took a **loop/cycle**. Graphs which have no loops are known as **trees**.

img
(A graph with one of its cycles in red, and a tree)

The **Euler characteristic** of a graph $G$ is

$$\chi (G) :=\#\{\text{vertices of}\ G \}-\#\{ \text{edges of}\ G \}$$

The Euler characteristics of the graphs above are $-4, 1$, respectively.

>**Lemma:** If $T$ is a tree, then $\chi(T)=1$

**Proof:** We use an inductive argument on the number of vertices of the tree. Let $T_n$ denote any tree with $n$ vertices, which is not unique for $n \geq 4$.

It is easy to see that $\chi(T_1)=1$. Assume that $\chi(T_n)=1$, for all $n \leq N$. Note that we get a tree with $N+1$ vertices by adding an extra vertex and an extra edge to some tree with $N$ vertices, making sure to not create a loop. This means that

$$\chi(T_{N+1}) = \chi(T_N) +1 -1 = \chi(T_N) =1$$

$\square$

Given any graph $G$, we can find a subgraph which is a tree by removing edges, making sure it remains connected when we do so, iteratively until we find a tree. The Euler characteristic of each iteration is one larger than the last. We then have the following.

> **Lemma:** If $G$ is a connected graph, then $\chi(G) \leq 1$, with equality if and only if $G$ is a tree_

All of the above graphs have been on the plane. What if we drew a graph of the surface of the sphere?

img

If we chopped up the surface of the sphere along the graph, how many chunks would we get? That is, how many regions of $S^2-G$ are there?

> **Theorem:** If $G$ is a finite connected graph drawn on the surface of $S^2$, then $S^2-G$ consists of $2-\chi(G)$ **faces**: connected regions homeomorphic to open discs.

**Proof:** If $G$ has loops, pick an edge of a loop which seperates two connected regions of $S^2-G$. If we removed this edge, the number of connected regions would go down by one, and the Euler characteristic of the graph would go up by one. Thus the following sum remains the same when we remove edges of $G$.

$$\chi(G) + \#\{\text{connected regions in} \ S^2-G \}$$

Keep on going until we get a tree $T_G$. The complement of a tree on $S^2$ is one connected region, and we know that $\chi(T_G)$. Hence

$$\chi(G) + \#\{\text{connected regions in} \ S^2-G \} = \chi(T_G) + \#\{\text{connected regions in} \ S^2-T_G \} =2$$
$\square$

Let $P$ be a polyhedron with $v$ vertices, $e$ edges, and $f$ faces. Note that $P \cong S^2$ so we can use the previous theorem, considering the vertices and edges of $P$ as a graph drawn on $S^2 \cong P$, to get the following.

> **Corollary:** If $P$ is a polyhedron which has $v$ vertices, $e$ edges, and $f$ faces, then $v-e+f=2$

This is the famous Euler's formula (for polyhedra).

## 2

img

An **$n$-simplex**  $\sigma^n \subset \mathbb{R}^N$ where $N \geq n$ is the convex hull of $n+1$ points, called vertices, in general position. The above image shows the first four simplices in $\mathbb{R}^3$.

A **(finite) simplicial complex** $K \subset \mathbb{R}^N$ is a finite union of simplices $\sigma^n \subset \mathbb{R}^N$, $n< N$, such that if $\sigma^n, \tau^m$ are two simplices in $K$, with one of them not being a face of the other, then $\sigma^n \cap \tau^m$ must be empty or a _single_ common face of both $\sigma^n, \tau^m$.

img

The **Euler Characteristic** of a simplicial complex $K$ is

$$\chi(K) := \sum_{i=1}^n a_i(K)$$

where $a_i(K)$ is the number of $i$-simplices in $K$.

> **Lemma:** Let $K =A \cup B$ be a simplicial complex. Then we have $\chi(K) = \chi(A)+ \chi(B) - \chi(A \cap B)$

**Proof:** Note that $a_i(K)=a_i(A)+a_i(B) - a_i(A\cap B)$. Hence

$$\chi(K) = \sum_{i=1}^n a_i(K) = \sum_{i=1}^n [a_i(A)+a_i(B) - a_i(A\cap B)]$$

$$= \sum_{i=1}^n a_i(A) + \sum_{i=1}^n a_i(B) - \sum_{i=1}^n a_i(A \cap B)$$

$$= \chi(A)+ \chi(B) - \chi(A \cap B)$$

$\square$

## 3
A **closed surface** is a compact, connected, Hausdorff topological space which locally Eucidean of dimension two. Draw a graph $G$ on some closed surface $S$. As before, the complement $S-G$ is a set of connected regions, each homeomorphic to open discs.

img

If we define the **Euler characteristic** of $S$ as

$$\chi_G(S)= \chi (G) + \#\{ \text{components of} \ S-G \}$$

we need to check that $\chi_G(S)$ does not depend on $G$. One can show that if our graph is enlarged to another graph $G' \subset S$ whose complement also comprises faces, then $\chi_{G}(S) = \chi_{G'}(S)$. Given two graphs $G_1, G_2 \subset S$, we can position them in such a way that $G_1 \cup G_2$ is also a graph and a common enlargement of both $G_1$ and $G_2$. Hence

$$\chi_{G_1}(S) = \chi_{G_1 \cup G_2}(S) = \chi_{G_2}(S)$$

> **Theorem:** $\chi_G(S)$ does not depend on $G$

Suppose $f: S_1 \to S_2$ is a homeomorphism between two closed surfaces, and that $G \subset S_1$ is a graph whose complement is homeomorphic to a disjoint union of open $2$-discs. Then $f(G)$ must also be a graph whose complement is homeomorphic to a disjoint union of open $2$-discs, the same number components in fact. Similarly $\chi(G_1) = \chi(f(G))$ and so

$$\chi(S_1)=\chi_G(S_1) = \chi_{f(G)}(S_2)=\chi(S_2)$$

> **Theorem:** The Euler characteristic is a topological invariant.

The **connected sum** of two closed surfaces, denoted $\cdot \# \cdot$, is achieved by ripping off an open disc from both surfaces and then joining the surfaces ath the boundaries of those open discs. Removing an open disc from a surface decreases the Euler characteristic of the surface by one.

img

> **Lemma:** $\chi(A\#B)=\chi(A)+\chi(B)-2$

We can add a **handle** to a closed surface $S$ by removing two open discs from the surface and then glueing the two ends of a cylinder to the boundaries of those discs.

> **Lemma:** $\chi(S \cup \{\text{handle} \}) = \chi(S) - 2$

img

We can add a **cross-cap** to a surface $S$ by removing an open disc from $S$ and glueing the resulting boundary circle to the boundary circle of the Möbius strip.

> **Lemma:** $\chi(S \cup \{\text{cross-cap} \}) = \chi(S) - 1$

img


