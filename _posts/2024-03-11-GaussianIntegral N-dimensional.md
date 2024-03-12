---
layout: post
title:  "Gaussian Integral Formula"
date:   2024-03-11 11:47:00 +0800
author: "Xuan Zhang"
categories: Mathmatics and Physics
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

# Ordinary Gaussian Integral

## One Dimensional Case

$$
\int_{-\infty}^{\infty}\mathrm{d}x\, \mathrm{e}^{-x^2}=\sqrt{\pi}
$$

There are many ways to get this. You can find some on Wiki.

By the Integration by substitution, we can get

$$
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{-\lambda x^2}=\sqrt{\frac \pi\lambda}
$$

## $N$-Dimensional Case

### No Linear Term

$$
\int_{\mathbb{R}^n}\mathrm{d}x\,\mathrm{e}^{-\frac 12 x^{\text{T}}A x}=\sqrt{\frac{(2\pi)^n}{\det A}}
$$

Here $A$ is a positive definite symmetric matrix.

> The proof is very simple. Just because $A$ is symmetric, according to the real spectrum theorem, the exist a orthogonal transformation $x\to y$ such that
> 
> $$
> x^{\mathrm{T}}Ax=\sum_{k=1}^{n}\lambda _k y_k^2
> $$
> 
> The orthogonal transformation in integral is simply change the valuable.
> 
> $$
> \int_{\mathbb{R}^n}\mathrm{d}x\,\mathrm{e}^{-\frac 12 x^{\text{T}}A x}=\int_{\mathbb{R}^n}\mathrm{d}y\,\prod_{k=1}^n\mathrm{e}^{-\frac 12 \lambda_ky_k^2}=\sqrt{\frac{(2\pi)^n}{\prod_{k=1}^{n}\lambda_k}}=\sqrt{\frac{(2\pi)^n}{\det A}}
> $$

### With Linear Term


$$
\int_{\mathbb{R}^n}\mathrm{d}x\,\mathrm{e}^{-\frac 12 x^{\text{T}}A x+b^{\mathrm{T}}x}=\sqrt{\frac {(2\pi)^n}{\det A}}\exp\left(\frac12 b^{\text T}A^{-1}b\right)
$$

> To proof this, we also use the integration by substitution. By $y=x-c$ 
> 
> $$
> \begin{align}
> -\frac 12 x^{\text{T}}A x+b^{\text{T}}x
> &=-\frac 12 \left(y^{\text T}+c^{\text T}\right)A(y+c)+b^{\text T}(y+c)
> \\&=-\frac 12 y^{\text T}Ay+\left(b^{\text T}-c^{\text T}A\right)y+\left(b^{\text T}-\frac 12 c^{\text T}A\right)c
> \end{align}
> $$
> 
> We wish the second term to vanish. Thus we can choose $c=A^{-1}b$ 
> 
> $$
> -\frac12 x^{\text{T}}A x+b^{\text{T}}x=-\frac 12 y^{\text{T}}A y+\frac12 b^{\text T}A^{-1}b
> $$
> 
> So
> 
> $$
> \begin{align}
> \int_{\mathbb{R}^n}\mathrm{d}x\,\mathrm{e}^{-\frac 12 x^{\text{T}}A x+b^{\mathrm{T}}x}
> &=\int_{\mathbb{R}^n}\mathrm{d}y\,\mathrm{e}^{-\frac 12 y^{\text{T}}A x}\mathrm{e}^{\frac12 b^{\text T}A^{-1}b}
> \\&=\sqrt{\frac {(2\pi)^n}{\det A}}\exp\left(\frac12 b^{\text T}A^{-1}b\right)
> \end{align}
> $$

# Fresnel Integral

## One-Dimension Integral

$$
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{\mathrm{i}x^2}=\sqrt{\frac \pi 2}(1+\mathrm{i})=\sqrt{\mathrm{i}\pi}
\\
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{-\mathrm{i}x^2}=\sqrt{\frac \pi 2}(1-\mathrm{i})=\sqrt{-\mathrm{i}\pi}
$$

Note: The $\sqrt z$ is a multivalued function, here we choose

$$
\sqrt{R\mathrm{e^{\mathrm{i}\theta}}}:=\sqrt R \mathrm{e}^{\mathrm{i}\theta/2},R>0,\theta\in\left(-\pi,\pi\right]
$$

> To prove this, we need to use the residue theorem.
>
> <div align=center><img src="https://github.com/Xuanyiyiren/picx-images-hosting/raw/master/Fresnel-Integral.7awwxewzna.svg" width="300"></div>
>
> $$
> \int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{\mathrm{i}x^2}=\int_{-\infty}^{\infty}\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}=\lim_{R\to\infty}\int_{D}^{A}\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}\\
> \oint_{ABCDA}\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}=0\\
> \Rightarrow\int_D^A\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}=\int_C^B\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}-\left(\int_A^B+\int_C^D\right)\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}
> $$
>
> The first term on the right side is just Gaussian Integral
>
> $$
> \begin{align}
> \int_C^B\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}&\xrightarrow{z=x\mathrm{e}^{\mathrm{i}\pi/4}}\int_{-\infty}^{\infty}\mathrm{d}(x\mathrm{e^{\mathrm{i}\pi/4}})\,\mathrm{e}^{\mathrm{i}x^2\mathrm{e}^{\mathrm{i}\pi/2}}
> \\&=\mathrm{e^{\mathrm{i}\pi/4}}\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{-x^2}
> \\&=\sqrt{\pi}\left(\frac{1}{\sqrt2}+\frac{\mathrm{i}}{\sqrt2}\right)
> \\&=\sqrt{\frac \pi2}(1+\mathrm{i})=\sqrt{\mathrm{i}\pi}
> \end{align}
> $$
>
> The second term is zero
>
> $$
> \begin{align}
> \left(\int_A^B+\int_C^D\right)\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}&\to 2\lim_{R\to\infty}\int_A^B\,\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}
> \\&=2\lim_{R\to\infty}\int_0^{\pi/4}\mathrm{d}(R\mathrm{e}^{\mathrm{i}\theta}) \mathrm{e}^{\mathrm{i}R^2\mathrm{e}^{2\mathrm{i}\theta}}
> \\&=2\lim_{R\to\infty}\int_0^{\pi/4}\mathrm{i}\mathrm{e}^{\mathrm{i}\theta}R\mathrm{d}\theta\, \mathrm{e}^{\mathrm{i}R^2(\cos{2\theta}+\mathrm{i}\sin{2\theta})}
> \\&=2\lim_{R\to\infty}\int_0^{\pi/4}\mathrm{d}\theta\, R\mathrm{e}^{-R^2\sin{2\theta}}\,\mathrm{i}\mathrm{e}^{\mathrm{i}\left(\theta+R^2\cos{2\theta}\right)}
> \end{align}
> $$
>
> So
> 
> $$
> \begin{align}
> \left|\int_0^{\pi/4}\mathrm{d}\theta\, R\mathrm{e}^{-R^2\sin{2\theta}}\,\mathrm{i}\mathrm{e}^{\mathrm{i\left(\theta+R^2\cos{2\theta}\right)}}\right|&\leq \int_0^{\pi/4}\mathrm{d}\theta\, R\exp\left(-R^2\sin 2\theta\right)
> \\&=\left(\int_{0}^{\delta/R}+\int_{\delta/R}^{\pi/4}\right)\mathrm{d}\theta\,R\exp\left(-R^2\sin 2\theta\right)
> \\&\leq\frac{\delta}{R}R+\frac{\pi}{4} \exp(-R^2\sin(\delta/R))
> \\&= \delta+\frac{\pi}{4} \exp(-R^2\sin(\delta/R))
> \end{align}
> $$
>
> Now take $R\to\infty$ on both sides 
>
> $$
> \lim_{R\to \infty}\left|\int_0^{\pi/4}\mathrm{d}\theta\, R\mathrm{e}^{-R^2\sin{2\theta}}\,\mathrm{i}\mathrm{e}^{\mathrm{i\left(\theta+R^2\cos{2\theta}\right)}}\right|\leq \delta
> \\
> \lim_{R\to \infty}\left(\int_A^B+\int_C^D\right)\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}\leq 2\delta
> $$
> 
> Here $\delta$ can be any positive number small enough(no need to be infinitesimal), this means 
> 
> $$
> \lim_{R\to \infty}\left(\int_A^B+\int_C^D\right)\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}=0
> $$
> 
> So the second term is zero. The conclusion has been proved.

Thus we have

$$
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{\mathrm{i}\lambda x^2}=\sqrt{\frac{\mathrm{i}\pi}{\lambda}},\lambda\in\mathbb{R}
$$

## $N$-Dimensional Integral

By the same way before, we can get the following formulas.

In the following formulas, $A$ is a real symmetric invertible matrix

$$
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{\frac{\mathrm{i}}{2}x^{\text T}Ax}=\sqrt{\frac{(2\pi\mathrm{i})^n}{\det A}}\\
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{\mathrm{i}\left(\frac 12 x^{\text T}Ax+b^{\text T}x\right)}=\sqrt{\frac{(2\pi\mathrm{i})^n}{\det A}}\exp\left(\frac{\mathrm{i}}{2} b^{\text T}A^{-1}b\right)
$$

# Can we combine them together?

Can we just bring the complex $A$ in the ordinary formula?

$$
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{-{\frac12}x^{\text T}Ax}=\sqrt{\frac{(2\pi)^n}{\det A}}\\

\int_{\mathbb{R}^n}\mathrm{d}x\,\mathrm{e}^{-\frac 12 x^{\text{T}}A x+b^{\mathrm{T}}x}
=\sqrt{\frac {(2\pi)^n}{\det A}}\exp\left(\frac12 b^{\text T}A^{-1}b\right)
$$

If we shift $A$ to $A/\mathrm{i}$, then we get the $N$-dimensional Fresnel Integral directly.

## One-Dimensional Case

We can choose a loop for $\mathrm{e}^{-z^2}$ like in the Fresnel Integral case but without an fixed angle at $45\degree$.

<div align=center><img src="https://github.com/Xuanyiyiren/picx-images-hosting/raw/master/Fresnel-Integral-general.7p1jwa6a2.svg" width="300"></div>

$$
\int_C^B\mathrm{d}z\,\mathrm{e}^{-z^2}=\int_D^A\mathrm{d}z\,\mathrm{e}^{-z^2}+\left(\int_A^B+\int_C^D\right)\mathrm{d}z\,\mathrm{e}^{-z^2}
$$

On the left hand side,

$$
\text{LHS}=\int_{-\infty}^{\infty}\mathrm{d}(x\mathrm{e}^{\mathrm{i}\alpha})\,\mathrm{e}^{-\mathrm{e}^{2\mathrm{i}\alpha}x^2}=\mathrm{e}^{\mathrm{i}\alpha}\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{-\mathrm{e}^{2\mathrm{i}\alpha}x^2}
$$

The first term on the right hand side is the Gaussian Integral, whose value is $\sqrt{\pi}$. And the second term on the right hand side is zero due to some condition.

$$
\begin{align}
\text{RHS-2} & =2\int _{0}^{\alpha }\mathrm{d} (R\mathrm{e}^{\mathrm{i} \theta } )\ \mathrm{e}^{-R^{2}\mathrm{e}^{\mathrm{2i\theta }}}\\
 & =2R\int _{0}^{\alpha }\mathbf{i}\mathrm{e}^{\mathbf{i} \theta }\mathrm{d} \theta \ \mathrm{e}^{-R^{2}(\cos 2\theta +\mathbf{i}\sin 2\theta )}\\
 & =2R\int _{0}^{\alpha }\mathrm{d} \theta \ \mathrm{e}^{-R^{2}\cos 2\theta }\mathrm{ie}^{\mathbf{i}\left( \theta -R^{2}\sin 2\theta \right)}
\end{align}
$$

If $-\frac \pi 4\leq\alpha\leq\frac \pi 4$, then this term is zero. You can use the same trick before. Only when $\lvert\alpha\rvert=\frac \pi 4$ the product function will touch 0, and that's when you need to divide the integral into two estimates. If $\lvert\alpha\rvert>\frac \pi 4$, the exponential decay term becomes an exponential explosion term and the integral does not converge.

So we get our result

$$
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{-\mathrm{e}^{2\mathrm{i}\alpha}x^2}=\mathrm{e}^{-\mathrm{i}\alpha}\sqrt{\pi}=\sqrt{\frac{\pi}{\mathrm{e}^{2\mathrm{i}\alpha}}},\lvert\alpha \rvert\leq\frac \pi 4.
$$

The condition $\lvert\alpha \rvert\leq\frac \pi 4$ means $\mathrm{Re}\{\mathrm{e}^{2\mathrm{i}\alpha}\}\geq0$, so by the Integration by substitution, we can rewrite our result by

$$
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{-\zeta x^2}=\sqrt{\frac \pi\zeta},\mathrm{Re}\,\zeta\geq0.
$$

## $N$-Dimensional Case

The big problem is how to treat a complex matrix with the real valuables. Decompose the matrix into real and imaginary parts and decompose the matrix into real and imaginary parts and diagonalize them simultaneously. This is the general eigenvalue problem. The general eigenvalue decomposition can not finished by an orthogonal transformation, but don't worry, we will just use the ideal behind it.

Consider $A=B+\mathrm{i}C$ is a symmetric complex matrix and $B$ is a real symmetric positive definite matrix and $C$ is a symmetric invertible real matrix.

So $B=R^2$ and $R$ is also real symmetric positive definite matrix(Refer to *Linear Algebra Done Right*). Thus

$$
x^{\text T}Ax\xrightarrow{y=Rx}y^{\text T}R^{-1}AR^{-1}y=y^{\text T}(I+\mathrm{i}R^{-1}CR^{-1})y
$$

Then we can diagonalize $R^{-1}CR^{-1}$.

$$
x^{\text T}Ax\xrightarrow[y'=Py]{y=Rx}y'^{\text T}y'+\mathrm{i}y'^{\text T}\Lambda y'
$$

So in the integral

$$
\begin{align}
\int \mathrm{d} x\ \mathrm{e}^{-\frac{1}{2} x^{\mathrm{T}} Ax} & \xrightarrow[y'=Py]{y=Rx}\int \mathrm{d} x\ \mathrm{e}^{-\frac{1}{2} x^{\mathrm{T}} Ax}\\
 & =\int | \det R| \mathrm{d} y'\ \exp\left( -\frac{1}{2} y^{\prime \mathrm{T}} y-\frac{\mathbf{i}}{2} y^{\prime \mathrm{T}} \Lambda y'\right)\\
 & =| \det R| \prod\limits _{k=1}^{n}\int \mathrm{d} y'_{k} \ \exp\left( -\frac{1}{2}( 1+\mathbf{i} \lambda _{k}) y^{\prime 2}_{k}\right)\\
 & =| \det R| \prod\limits _{k=1}^{n}\sqrt{\frac{2\pi }{( 1+\mathbf{i} \lambda _{k})}}\\
 & =\sqrt{\frac{2\pi }{\det B}\frac{1}{\prod _{k=1}^{n}( 1+\mathbf{i} \lambda _{k})}}
\end{align}
$$

Here $\lambda_k$ is the eigenvalues of $R^{-1}CR^{-1}$. So $1+\mathrm{i}\lambda_k$ is the eigenvalues of $I+\mathrm{i}R^{-1}CR^{-1}$, therefore

$$
\prod _{k=1}^{n}( 1+\mathbf{i} \lambda _{k}) =\det\left( 1+\mathbf{i} R^{-1} CR^{-1}\right)
$$

$$
\begin{align*}
\det B\cdot \det\left( 1+\mathbf{i} R^{-1} CR^{-1}\right) & =\det R\cdot \det\left( 1+\mathbf{i} R^{-1} CR^{-1}\right) \cdot \det R\\
 & =\det A
\end{align*}
$$

Thus we get one of our ideal result:

If $A$ is matrix whose real part is positive definite symmetric matrix and imaginary part is invertible symmetric matrix, then

$$
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{-{\frac12}x^{\text T}Ax}=\sqrt{\frac{(2\pi)^n}{\det A}}
$$

By the same way we can add the linear term

$$
\int_{\mathbb{R}^n}\mathrm{d}x\,\mathrm{e}^{-\frac 12 x^{\text{T}}A x+b^{\mathrm{T}}x}
=\sqrt{\frac {(2\pi)^n}{\det A}}\exp\left(\frac12 b^{\text T}A^{-1}b\right)
$$
