---
layout: post
title:  "Irreducible representation of SU(2)"
date:   2024-03-30 15:42:00 +0800
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

# irreps of $\mathrm{SU}(2)$

I will just give a brief introduction. For more details, you can see *GTM267 Quantum Theory for Mathematicians*.

$\tilde J_i$ is the basis of $\mathfrak{su}(2)$, we define

$$
\tilde{J}_{+} =\tilde{J}_{1} +\mathbf{i}\tilde{J}_{2} =\mathbf{i} \pi ( F_{1}) -\pi ( F_{2})\\
\tilde{J}_{-} =\tilde{J}_{1} -\mathbf{i}\tilde{J}_{2} =\mathbf{i} \pi ( F_{1}) +\pi ( F_{2})
$$

Here $\tilde{J_i}:=\frac{J_i}{\hbar}$ is to make it dimensionless. If you use the natural unit system, than $\tilde{J}_i=J_i$. 

You can use the relationship $[\tilde{J}_i,\tilde{J}_j]=\mathrm{i}\epsilon_{jkl}\tilde{J}_k\tilde{J}_l$ to prove the following equations

$$
\begin{align*}
[\tilde{J}_{3} ,\tilde{J}_{+}] & =[\tilde{J}_{3} ,\tilde{J}_{1} +\mathbf{i}\tilde{J}_{2}]\\
 & =\mathbf{i}\tilde{J}_{2} -\mathbf{i} \cdot \mathbf{i}\tilde{J}_{1}\\
 & =\tilde{J}_{1} +\mathbf{i}\tilde{J}_{2} =\tilde{J}_{+}\\
[\tilde{J}_{3} ,\tilde{J}_{-}] & =[\tilde{J}_{3} ,\tilde{J}_{1} -\mathbf{i}\tilde{J}_{2}]\\
 & =\mathbf{i}\tilde{J}_{2} +\mathbf{i} \cdot \mathbf{i}\tilde{J}_{1}\\
 & =-\tilde{J}_{1} +\mathbf{i}\tilde{J}_{2}\\
 & =-\tilde{J}_{-}\\
[\tilde{J}_{+} ,\tilde{J}_{-}] & =[\tilde{J}_{1} +\mathbf{i}\tilde{J}_{2} ,\tilde{J}_{1} -\mathbf{i}\tilde{J}_{2}]\\
 & =-\mathbf{i}[\tilde{J}_{1} ,J_{2}] +\mathbf{i}[\tilde{J}_{2} ,\tilde{J}_{1}]\\
 & =2\tilde{J}_{3}
\end{align*}
$$

Thus for $\tilde{J}_+$ , consider $\psi$ is the eigenstate of $\tilde{J}_3$ with eigenvalue $\lambda$

$$
\tilde{J}_{3}\tilde{J}_{+} \psi=\tilde{J}_{+}\tilde{J}_{3} \psi+[\tilde{J}_{3} ,\tilde{J}_{+}] \psi=\tilde{J}_{+}( \lambda \psi) +\tilde{J}_{+} \psi=( \lambda +1)\tilde{J}_{+} \psi
$$

So $\tilde{J}_+$ can increase the eigenvalue by one. The similar conclusion can be derived for $\tilde{J}_-$. 

So consider the finite-dimensional representation of $\mathrm{su}(2)$ . By the Schur's Theorem in [Linear Algebra Done Right(Theo 6.38)](https://linear.axler.net/) , a complex operator in finite-dimensional space has at least one eigenstate. 

You can apply $\tilde{J}_+$ on it to get the maximal eigenvalue $l$ and the eigenstate $\psi_l$, there must exist maximal eigenvalue because it is a finite-dimension space. And the maximal means that $\tilde{J}_+\ket{\psi_l}=0$

Then you can apply $\tilde{J}_-$ on $\psi_l$ and define

$$
\ket{ \psi _{l-k}}=(\tilde{J}_-)^k\ket{\psi_l}
$$

By this way the eigenvalue of $\ket{\psi_k}$ is $k$.

So by some induction, you can find

$$
\tilde{J}_+\ket{\psi_k} = (l-k)(l+1+k)\ket{\psi_{k+1}}
$$

Again, there must be finitely many eigenstates. So there must exists $m$ such that $\psi_m\neq0$ and $\psi_{m-1}=0$. Thus $\tilde{J_+}\ket{\psi_{m-1}}=0$ 

$$
\tilde{J}_+{\ket{\psi_{m-1}}} =(l-m+1)(l+m)\ket{\psi_{m}}
$$

This means $l=-m$ or $l-m=-1$. For $m\leq l$ the second solution is wrong. The whole space is expanded by $\psi_{-l},\cdots,\psi_l$ because the space is $\mathrm{su}(2)$ irreducible representation space. There are totally $2l+1$ eigenstates thus the dimension of the space is $2l+1$.

So $2l+1$ must be an integer, and $l\geq m=-l$ means $l$ must be zero or positive. That is why $l=0,\frac 12,1,\ldots$

For an infinite representation space, the *GTM267* do not give a discussion.