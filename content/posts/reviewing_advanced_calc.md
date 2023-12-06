---
title: "Reviewing Advanced Calculus"
date: 2023-12-04T16:57:53-07:00
draft: false
math: true
---

This semester(Fall 2023) I took a class called Advanced Calculus(MAT 371), which is ASU's equivalent of an introductory real analysis class. I thought I'd write a bit about what I learned, as part of my review for the final exam. The textbook we used is **Abbott's Understanding Analysis**, which I actually quite like.

## Chapter 1: Introducing the Reals
To start off with Real Analysis, it makes sense that the first thing we covered is how to construct the Reals i.e. *what makes the reals the reals*? In this textbook, we started off with the rationals, and then constructed the reals on top of the rationals.

To review, the rationals(denoted as $\mathbf{Q}$) is the set of all numbers that can be expressed as a ratio between 2 integers i.e. 
{{< raw >}}
$$\mathbf{Q} = \{ \frac{a}{b} | a, b \in \mathbf{Z} \}$$
{{< /raw >}}

To introduce the reals, we'll start by introducing a couple other ideas first, which let us define the reals.

### Maximums and Minimums
Just going off the names, these ideas are likely pretty intuitive. The maximum of a set of numbers is the largest number in the set, and the minimum is the smallest number in the set. Here are some quick examples:

{{< raw >}}Let $S = \{1, 2, 3, 4, 5\}$.{{< /raw >}} It folows that

$$ \max(S) = 5 $$
$$ \min(S) = 1 $$

Formally, we define the maximum and mimimum as follows:

**Definition**: A number $M$ is the **maximum** of a set $S$ $\iff$(**if and only if**) for any value $x$ in the set $S$, $x \leq M$, **and** $M$ is in $S$.

**Definition**: A number $m$ is the **minimum** of a set $S$ $\iff$ for any value $x$ in the set $S$, $x \geq m$, **and** $m$ is in $S$.

In both cases, the inequality makes sense, by the intuitive, everyday use of the words. The main, **important note** is that the maximum and minimum are **in** the set $S$. This also makes sense, but has some interesting consequences, which we'll see now.

### Supremums and Infimums

#### Sets with no minimums or maximums
Let's construct a new set $A$, with $A$ being defined as the set of all rational numbers **strictly less than 2** and **strictly greater than 0**. We can write this as follows:

{{< raw >}}

$$ A = \{ x | 0 < x < 2 \land x \in \mathbf{Q} \} $$

{{< /raw >}}

Now, let's try and find the maximum and minimum. Intuitively, we'd say that

$$ \max(A) = 2 $$
$$ \min(A) = 0 $$

However, **this is incorrect**, since the neither 0 nor 2 are in the set $A$. So, these 2 numbers are not the minimum nor the maximum. In fact, we can show that this set has **no maximum or minimum**, which we can show rather easily.

**Proof that $A$ has no maximum**: For $A$ to have a maximum, there must exist a number $M$, which is a candidate maximum, that satisfies the 2 properties of a maximum of a set. To show this is impossible, start by taking as $L$ any element of $A$, **ABF(arbitrary but fixed)**. We can show this element is not a maximum, since we can find a new number, $L_2$, that we define as $\frac{2 + L}{2}$, which is simply the average of 2 and $L$.

Note 3 properties of this element $L_2$:

1. It's larger than $L$, since $L$ must be less than 2 and $L_2$ is the average of $L$ and 2
2. It's less than 2, since the average of a number less than 2 and 2 must also be less than 2
3. It's in the set $A$, since it's less than 2 and is rational

As such, $L_2$ is larger than $L$, and is in the set, so $L$ cannot be a maximum. However, **since we took $L$ as ABF**, this argument holds for any candidate maximum we provide. As such, $A$ has no maximum.

The proof for the minimum is almost the same, just with the average and inequalities changed around.

#### Introducing Bounds
Intuitively, the above set $A$ does have some limit on how large its elements are, but it doesn't have a maximum or minimum. Wouldn't it be nice if we had some way of talking about the size of elements in this set? Well, we actually do.

We now introduce the notion of a set being **bounded** (Definition 1.3.1). A set $S$ is **bounded above** if there exists a number $B$ s.t. all elements of $S$ are $\leq B$. In more formal terms, the number $B$ is an upper bound of $S \iff \forall x \in S, x \leq B $.

Similarly, a set $S$ is **bounded below** by a number $b \iff \forall x \in S, b \leq x$

One important note for both of these definitions is that we **do not need the upper or lower bound to be in the set as well; they can be values outside the set**. This has important ramifications.

Going back to the set $A$ we defined above as 
{{< raw >}}
$ A = \{ x | 0 < x < 2 \land x \in \mathbf{Q} \} $
{{< /raw >}}, note that $A$ **is indeed bounded above and below**, and the maximums and minimums we defined are indeed bounds i.e. *A is bounded above by 2 and below by 0*.

#### Introducing the Supremum and Infimum
Now that we've defined the notion of an upper and lower bound, on top of our prior knowledge of maximums and minimums, there remains one more thing we'd probably like. Note that when we said that {{< raw >}}
$ A = \{ x | 0 < x < 2 \land x \in \mathbf{Q} \} $
{{< /raw >}} was upper bounded by 2 and lower bounded by 0, **those are not unique bounds**.

What I mean by this is that the set has an infinite number of both i.e. 

- Any number greater than or equal to 2 is an upper bound for A
- Any number less than or equal to 0 is a lower bound for A

While this does make sense, when we talk about the bound of a set, **we oftentimes want to talk about the narrowest bounds, since they're usually the most useful**. Real Analysis defines a term for these, and they are known as **greatest lower bounds and lowest upper bounds**, but are more commonly known as **infimums and supremums** respectively.

Here are their definitions(Definition 1.3.2):

A **supremum** of a set $S$ is a number $T$ such that $T$ is an upper bound of $S$, and $T$ is less than or equal to any other upper bound of $S$. Similarly, an **infimum** of a set $S$ is a number $t$ such that $t$ is a lower bound of $S$, and $t$ is greater than or equal to any other lower bound of $S$.

In more formal notation, we get the following:

A number $T$ is the supremum of the set $S$ if the following 2 constraints are satisfied:
1. $T$ is an upper bound of $S$ i.e. $\forall x \in S, x \leq T$
2. $T$ is less than or equal to any other upper bound of $S$ i.e. $\forall T' \in \mathbf{R}, T' \text{ is an upper bound of } S \implies T \leq T'$

A similar definition holds for the infimum, just with the inequalities flipped around.

Note that in the example given, where 
{{< raw >}}
$ A = \{ x | 0 < x < 2 \land x \in \mathbf{Q} \} $, the supremum is 2, and the infimum is 0. This makes sense, since 2 is the smallest upper bound, and 0 is the largest lower bound. This gives us the more constrained upper and lower bounds we are looking for.
{{< /raw >}}

From here on out, I will be more brief, since the range of topics widens a lot. I'll focus on what's important, and if you want more please look into the textbook mentioned at the top.

### The Axion of Completeness
The **axiom of completeness**, also known as the **least upper bound property** or the **supremum axiom**, is a very important axiom in Real Analysis. In fact, this axiom defines the reals, and is what makes the reals the reals, and is the **primary** difference between the rationals and the reals.