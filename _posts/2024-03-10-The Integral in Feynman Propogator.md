---
layout: post
title:  "The Integral in Feynman Propogator"
date:   2024-03-10 02:47:00 +0800
author: "Xuan Zhang"
categories: Physics
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


In QM and QFT course, we need to use the Residue theorem to get do a integral in the calculation in propagator

$$
\int_{-\infty}^{+\infty} \frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}\omega
$$

To calculate this integral, we need to use the Residue theorem. And another important things is the sign of $t$.

Choose $\omega$ as the point in the complex plane. The integral is from $-\infty \in \mathbb{R}$ to $+\infty \in \mathbb{R}$. There are two ways to construct the closed curve (the red curve and the blue curve in the figure below). And the function to be integrated is 

$$
\frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}
$$

This function have only one singularity which is $\omega=\omega_0-\mathrm{i}\varepsilon$.

<div align=center><img src="https://github.com/Xuanyiyiren/picx-images-hosting/raw/master/feynmanporpagator.7i04qxon6o.svg" width="50%"></div>

Note only if the close curve is clockwise, there should be a negative value sign ''$-$'' before residue in Residue Formula.

### If $t>0$

We will choose the blue way

$$
\begin{align}
\int_{-\infty}^{+\infty} \frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}\omega
&=-\lim_{R\to\infty}\int_0^\pi \frac{\mathrm{e}^{\mathrm{i}R\mathrm{e}^{\mathrm{i}\theta} t}}{R\mathrm{e}^{\mathrm{i}\theta} - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}(R\mathrm{e}^{\mathrm{i}\theta})
\\ &=-\lim_{R\to\infty}\int_0^\pi \frac{\mathrm{e}^{\mathrm{i}Rt(\cos \theta+\mathrm{i\sin\theta})}(R\mathrm{i\mathrm{e}^{\mathrm{i}\theta}})}{R\mathrm{e}^{\mathrm{i}\theta} - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}\theta
\\ &=-\lim_{R\to\infty}\int_0^\pi \mathrm{e}^{-Rt\sin\theta}\frac{\mathrm{i}\mathrm{e}^{\mathrm{i}(Rt\cos\theta+\theta)}}{\mathrm{e}^{\mathrm{i}\theta} -\frac{\omega_0 - \mathrm{i}\varepsilon}{R}}\mathrm{d}\theta
\end{align}
$$

The integrant 

$$
\left|\mathrm{e}^{-Rt\sin\theta}\frac{\mathrm{i}\mathrm{e}^{\mathrm{i}(Rt\cos\theta+\theta)}}{\mathrm{e}^{\mathrm{i}\theta} -\frac{\omega_0 - \mathrm{i}\varepsilon}{R}}\right|\leq 2\mathrm{e}^{-Rt\sin\theta}
$$

For a great enough $R$.

Thus 

$$
\left|\int_{-\infty}^{+\infty} \frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}\omega \right|\leq 2\lim_{R\to\infty}\int_0^\pi \mathrm{e}^{-Rt\sin\theta}\mathrm{d}\theta
$$

For any $\delta>0$ which is small enough(no need to be infinitesimal)

$$
\begin{align}
\int_0^\pi \mathrm{e}^{-Rt\sin\theta}\mathrm{d}\theta
&\leq\left(\int_0^{\delta}+\int_{\pi-\delta}^\pi \right)\mathrm{e}^{-Rt\sin\theta}\mathrm{d}\theta+\int_\delta^{\pi-\delta}\mathrm{e}^{-Rt\sin\theta}\mathrm{d}\theta
\\ &\leq 2\delta+\pi \cdot \mathrm{e}^{-Rt\sin\delta}
\end{align}
$$

If take $\lim_{R\to\infty}$ on both side

$$
\lim_{R\to\infty}\int_0^\pi \mathrm{e}^{-Rt\sin\theta}\mathrm{d}\theta \leq 2\delta
$$

This means that $\lim_{R\to\infty}\int_0^\pi \mathrm{e}^{-Rt\sin\theta}\mathrm{d}\theta$ can be infinitesimal(smaller than any positive number)

$$
\lim_{R\to\infty}\int_0^\pi \mathrm{e}^{-Rt\sin\theta}\mathrm{d}\theta=0
$$

So when $t>0$

$$
\int_{-\infty}^{+\infty} \frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}\omega=0
$$

### If $t<0$

We will choose the red way

$$
\begin{align}
\int_{-\infty}^{+\infty} \frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}\omega
&=-2\pi\mathrm{i}\,\mathrm{Res}(\omega_0-\mathrm{i\varepsilon})-\\ &\lim_{R\to\infty}\int_0^{-\pi} \frac{\mathrm{e}^{\mathrm{i}R\mathrm{e}^{\mathrm{i}\theta} t}}{R\mathrm{e}^{\mathrm{i}\theta} - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}(R\mathrm{e}^{\mathrm{i}\theta})

\\ &=-2\pi\mathrm{i}\mathrm{e}^{\mathrm{i}\omega_0 t}-0
\end{align}
$$

The first term $\mathrm{e}^{\mathrm{i}\omega_0 t}$ is the residue of $\frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}$ at $\omega_0-\mathrm{i}\varepsilon$.

$$
\omega':=\omega_0-\mathrm{i}\varepsilon
\\
\frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}
=\frac{\mathrm{e}^{\mathrm{i}(\omega-\omega') t}}{\omega -\omega'}\cdot \mathrm{e}^{\mathrm{i}\omega't}
=\frac{\mathrm{e}^{\mathrm{i}\omega't}}{\omega-\omega'} + \cdots
$$

Thus the residue is $\mathrm{e}^{\mathrm{i}\omega't}=\mathrm{e}^{\mathrm{i}\omega_0t}$. 

The second term is zero due to the same reason before. The only difference is this time $t<0$ and $\theta$ is form $0$ to $-\pi$.

### The total result

$$
\int_{-\infty}^{+\infty} \frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}\omega=
-2\pi\mathrm{i}\mathrm{e}^{\mathrm{i}\omega_0t}\Theta(-t) \tag{1}
$$

If $\omega$ is shifted to $-\omega$ on the numerator. We can just shift $t$ to $-t$

$$
\int_{-\infty}^{+\infty} \frac{\mathrm{e}^{-\mathrm{i}\omega t}}{\omega - \omega_0 + \mathrm{i}\varepsilon}\mathrm{d}\omega
=-2\pi\mathrm{i}\mathrm{e}^{-\mathrm{i}\omega_0t}\Theta(t) \tag{1'}
$$

If $\varepsilon$ is shifted to $-\varepsilon$, keeping $\varepsilon>0$. Of cause you can just repeat the above process. But you can play a trick by applying complex conjugate on both side of equation (1').

$$
\int_{-\infty}^{+\infty} \frac{\mathrm{e}^{\mathrm{i}\omega t}}{\omega - \omega_0 - \mathrm{i}\varepsilon}\mathrm{d}\omega
=2\pi\mathrm{i}\mathrm{e}^{\mathrm{i}\omega_0t}\Theta(t) \tag{2}
$$