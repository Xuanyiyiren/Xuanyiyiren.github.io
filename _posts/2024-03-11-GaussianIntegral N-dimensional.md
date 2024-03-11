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

# Gaussian Integral

## One Dimensional Case

$$
\int_{-\infty}^{\infty}\mathrm{d}x\, \mathrm{e}^{-x^2}=\sqrt{\pi}
$$

There are many ways to get this.

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
> \Rightarrow\int_A^B\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}=\int_C^B\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}-\left(\int_A^B+\int_C^D\right)\mathrm{d}z\,\mathrm{e}^{\mathrm{i}z^2}
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
> \\&=2\lim_{R\to\infty}\int_0^{\pi/4}\mathrm{d}\theta\, R\mathrm{e}^{-R^2\sin{2\theta}}\,\mathrm{i}\mathrm{e}^{\mathrm{i\left(\theta+R^2\cos{2\theta}\right)}}
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
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{\frac{\mathrm{i}}{2}x^{\text T}Ax}=\sqrt{\frac{(\mathrm{i}\pi)^n}{\det A}}\\
\int_{-\infty}^{\infty}\mathrm{d}x\,\mathrm{e}^{\mathrm{i}\left(\frax^{\text T}Ax+b^{\text T}x\right)}=\sqrt{\frac{(\mathrm{i}\pi)^n}{\det A}}\exp\left(\frac{\mathrm{i}}{2} b^{\text T}A^{-1}b\right)
$$


#### Can we combine them together?
