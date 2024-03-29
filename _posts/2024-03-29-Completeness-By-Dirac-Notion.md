---
layout: post
title:  "Dirac's Notion and Completeness in Function Space"
date:   2024-03-29 17:44:00 +0800
author: "Xuan Zhang"
categories: Mathematics and Physics
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>
$\require{braket}$



In a function space $X$, the completeness of a set of functions $\{\psi_k\}$ means $\mathrm{span}\{\psi_k:k\}=X$. If we add the orthonormality, we can write a beautiful equation as a equivalent condition (The inner product here treats the second element linearly $\langle a,\lambda b\rangle=\lambda\langle a,b\rangle$)

$$
\psi=\sum_k \langle \psi_k,\psi\rangle \psi_k
$$

For a proof you can see the 18th chapter of *Mathematical Analysis by Zorich*.

However, as a student major in physics, by using Dirac's notion, the equation can be written more beautifully:

$$
\ket{\psi}=\sum_k \ket{k}\bra{k}\ket{\psi},\forall\psi\in X
$$

This means an operator $\sum_k \ket{k}\bra{k}=\mathrm{id}_X=I$, this is the completeness introduced by your Quantum Mechanics teacher. To emphasize how beautiful it is, let me write it again

$$
\sum_k \ket{k}\bra{k}=\mathrm{id}_X=I
$$

However, this notion is more than just beautiful looking. By insert this identity map to your formula, you can see it's power.

###### Parseval Equation:

Just insert the identity map in a self inner product, 

$$
\lVert\psi\rVert^2=\braket{\psi}=\mel**{\psi}{I}{\psi}=\sum_k \bra{\psi}\ket{\psi_k}\bra{\psi_k}\ket{\psi}
=\sum_k \lvert\bra{\psi_k}\ket{\psi}\rvert^2
$$

###### To construct Dirac delta function:

Just insert the identity map in $\bra{x}\ket{y}=\delta(x-y)$

$$
\sum_k \psi_k^*(x)\psi_k(y)=\sum_k\bra{x}\ket{\psi}\bra{\psi}\ket{y}=\bra{x}\ket{y}=\delta(x-y) \tag{1}
$$

The property $\sum_k \psi_k^*(x)\psi_k(y)=\delta(x-y)$ for a orthonormal complete basis of function space is not easy to proof. **However the Dirac's notion help us to neglect those analytical parts and pay more attention on algebraic parts.**

### To prove eq(1) without Dirac's notion

Note: in fact the proof is extract from Dirac notion's one-step proof.

$$
\begin{align*}
\sum _{k} \psi _{k}^{*}( a) \psi _{k}( b) & =\sum _{k}\int \mathrm{d} x\ \delta ( x-a) \psi _{k}^{*}( x) \ \int \mathrm{d} y\ \delta ( y-b) \psi _{k}( y)\\
 & =\int \mathrm{d} y\ \delta ( y-b)\sum _{k}\int \mathrm{d} x\ \delta ( x-a) \psi _{k}^{*}( x) \psi _{k}( y)\\
 & \xlongequal{F( x) :=\delta ( x-a)}\int \mathrm{d} y\ \delta ( y-b)\sum _{k}\int \mathrm{d} x\ F( x) \psi _{k}^{*}( x) \psi _{k}( y)\\
 & =\int \mathrm{d} y\ \delta ( y-b)\sum _{k}\bra{\psi _{k}}\ket{F} \psi _{k}( y)\\
 & =\int \mathrm{d} y\ \delta ( y-b)\left[\sum _{k}\bra{\psi _{k}}\ket{F} \psi _{k}\right]( y)\\
 & =\int \mathrm{d} y\ \delta ( y-b) F( y)\\
 & =F( b)\\
 & =\delta ( a-b)
\end{align*}
$$
