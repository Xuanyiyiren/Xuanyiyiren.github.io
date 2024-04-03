---
layout: post
title:  "All about Linear Regression"
date:   2024-03-30 15:42:00 +0800
author: "Xuan Zhang"
categories: Mathematics
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

# All about Linear Regression

[TOC]

## Simple Linear Regression

### Motivation

There is a linear model between $y$ and $x$ with unknown parameter:

$$
y=\beta_0+\beta_1x.
$$

You did same experiment and got some data

$$
(x_1,y_1),(x_2,y_2),\ldots,(x_N,y_N).
$$

How to use these data to estimate the parameter $\beta_0,\beta_1$?

### By Least Square

The least squares method is to minimize the following function

$$
L(\beta_0,\beta_1)=\sum_{i=1}^N (y_i-\hat y_i)^2\\
\hat y_i = \beta_0+\beta_1x_i
$$

We get the result by

$$
\frac{\partial L}{\partial \beta_i}=0~,~i=0,1
$$

$$
\frac{\partial L}{\partial \beta_0}=2\sum_{i=1}^N (\hat y_i-y_i)=0\\
\frac{\partial L}{\partial \beta_1}=2\sum_{i=1}^N (\hat y_i-y_i)x_i=0
$$

By simplifying the equation, one can derive

$$
\begin{gather*}
\begin{cases}
\beta _{0} +\beta _{1}\overline{x} =\overline{y}\\
\beta _{0}\overline{x} +\beta _{1}\overline{x^{2}} =\overline{xy}
\end{cases}\\
\overline{x} =\frac{1}{N}\sum _{i=1}^{N} x_{i} ,\overline{y} =\frac{1}{N}\sum _{i=1}^{N} y_{i} ,\overline{x^{2}} =\frac{1}{N}\sum _{i=1}^{N} x_{i}^{2} ,\overline{xy} =\frac{1}{N}\sum _{i=1}^{N} x_{i} y_{i}
\end{gather*}
$$

Thus the result is

$$
\begin{cases}
\beta _{0} =\frac{\begin{vmatrix}
\overline{y} & \overline{x}\\
\overline{xy} & \overline{x^{2}}
\end{vmatrix}}{\begin{vmatrix}
1 & \overline{x}\\
\overline{x} & \overline{x^{2}}
\end{vmatrix}} =\frac{\overline{x}^{2}\overline{y} -\overline{x}\overline{xy}}{\overline{x^{2}} -\overline{x}^{2}}\\
\beta _{1} =\frac{\begin{vmatrix}
1 & \overline{y}\\
\overline{x} & \overline{xy}
\end{vmatrix}}{\begin{vmatrix}
1 & \overline{x}\\
\overline{x} & \overline{x^{2}}
\end{vmatrix}} =\frac{\overline{xy} -\overline{x}\overline{y}}{\overline{x^{2}} -\overline{x}^{2}}
\end{cases}
$$


### By Maximum Likelihood.

Consider $y_i$ to have a Gaussian noise around the truth value

$$
y=\beta_0+\beta_1x+\eta
$$

All the $\eta$ is independent and obey the gaussian distribution $\mathcal{N}(0,\sigma^2)$, thus $y$ obey the distribution $\mathcal{N}(\beta_0+\beta_1x,\sigma^2)$.

The data is just a sample of $\eta$,

$$
\eta_i=y_i-\beta_0-\beta_1x_i,i=1,\ldots,N
$$

The Likelihood function of $\{\eta_i\}_{i=1}^N$ is

$$
\mathcal{L}(\beta_0,\beta_1;x_1,\ldots,x_N,y_1,\ldots,y_N)=\prod_{i=1}^N \frac{1}{\sigma \sqrt{2\pi}}\exp\left(-\frac{(y_i-\hat y_i)^2}{2\sigma^2}\right)
\\
\hat y_i = \beta_0-\beta_1x_i
$$

Thus the log-likelihood function is

$$
\begin{align*}
\mathscr{l} (\beta _{0} ,\beta _{1} ;x_{1} ,\dotsc ,y_{N} ) & =\ln\mathcal{L}\\
 & =\sum _{i}^{N}\left[\left( -\frac{( y_{i} -\hat{y}_{i})^{2}}{2\sigma ^{2}}\right) -\ln \sigma -\frac{1}{2}\ln( 2\pi )\right]\\
 & =-\frac{1}{2\sigma ^{2}}\sum _{i}^{N}( y_{i} -\hat{y}_{i})^{2} -N\ln \sigma -\frac{N}{2}\ln( 2\pi )
\end{align*}
$$

So to maximize the log-likelihood function $\mathscr{l}$, it is equivalent to minimize the least squares function $L$ for

$$
\mathscr{l} =-\frac{1}{2\sigma ^{2}} L-N\ln \sigma -\frac{N}{2}\ln( 2\pi )
$$

### The relationship between Maximum Likelihood and Least Square

This part may be a little objective.

In my opinion, the great likelihood estimation method provides the idea, telling us why we can do regression analysis by taking the maximal value, which in turn leads to minimizing the least squaress function, the starting point of least squaress. Whereas the least squaress method is more concerned with how to get the result, how to go about finding the extremes step by step given the least squaress function.

## Weighted Linear Regression

### Motivation

Some times the observed value $y_i$ is not exact, and you can get a estimate it's variance $\sigma_i^2$ in the you experiment. 

This time we begin with maximum likelihood method.

This means the variance of $\eta_i$ has a estimated value $\sigma_i^2$, the likelihood function is

$$
\mathcal{L}(\beta_0,\beta_1;x_1,\ldots,x_N,y_1,\ldots,y_N)=\prod_{i=1}^N \frac{1}{\sigma_i \sqrt{2\pi}}\exp\left(-\frac{(y_i-\hat y_i)^2}{2\sigma_i^2}\right)
\\
\hat y_i = \beta_0-\beta_1x_i.
$$

So the log-likelihood function is

$$
\begin{align*}
\mathscr{l} (\beta _{0} ,\beta _{1} ;x_{1} ,\dotsc ,y_{N} ) & =\ln\mathcal{L}\\
 & =\sum _{i}^{N}\left[\left( -\frac{( y_{i} -\hat{y}_{i})^{2}}{2\sigma _{i}^{2}}\right) -\ln \sigma _{i} -\frac{1}{2}\ln( 2\pi )\right]\\
 & =-\frac{1}{2}\sum _{i}^{N}\frac{( y_{i} -\hat{y}_{i})^{2}}{\sigma _{i}^{2}} -\sum _{i=1}^{N}\ln \sigma _{i} -N\frac{1}{2}\ln( 2\pi )\\
 & =:-\frac{1}{2} L-\sum _{i=1}^{N}\ln \sigma _{i} -N\frac{1}{2}\ln( 2\pi )
\end{align*}
$$

$$
L=\sum _{i}^{N}\frac{( y_{i} -\hat{y}_{i})^{2}}{\sigma _{i}^{2}}
$$

To maximize $\mathscr{l}$ is equivalent to minimize $L$. Here $L$ is the weighted least squares function. It is the ordinary least squares function 

One can easily see that the simple linear regression is just replacing the summation in the original least squaress function with a weighted summation, with the weight $w_i=\frac{1}{\sigma_i^2}$.

This weight means we should pay more attention on those observed values with higher accuracy, i.e. the smaller $\sigma_i^2$.

In fact, we do not have to know the $\sigma_i^2$'s values totally, just the ratio is enough. That is $1/\sigma_i^2=w_i/\sigma^2$, which is $w_i=\frac{\sigma^2}{\sigma_i^2}$. The parameter $\sigma^2$ is called **variance of unit weight**, meaning the variance with weight $1$.

Now the maximum likelihood function and the least squares function is

$$
\begin{gather*}
\sigma _{i} =\frac{\sigma }{\sqrt{w_{i}}}\\
\mathcal{L} =\prod _{i=1}^{N}\frac{1}{\sigma }\sqrt{\frac{w_{i}}{2\pi }}\exp\left( -\frac{w_{i}( y_{i} -\hat{y}_{i})^{2}}{2\sigma ^{2}}\right)\\
\begin{aligned}
\mathscr{l} & =\ln\mathcal{L}\\
 & =-\frac{1}{2\sigma ^{2}}\sum _{i=1}^{N} w_{i}\left( y_{i}^{2} -\hat{y}_{i}^{2}\right)^{2} +N\left(\frac{1}{2}\ln w_{i} -\ln \sigma -\frac{1}{2}\ln 2\pi \right)\\
 & =-\frac{L}{2\sigma ^{2}} +N\left(\frac{1}{2}\ln w_{i} -\ln \sigma -\frac{1}{2}\ln 2\pi \right)
\end{aligned}\\
L=\sum _{i=1}^{N} w_{i}( y_{i} -\hat{y}_{i})^{2}
\end{gather*}
$$

If we choose $w_i\equiv 1$, it degrade to the simple linear regression.

### Formula

We can get the result by minimize the least squares function

$$
L=\sum _{i=1}^{N} w_{i}( y_{i} -\hat{y}_{i})^{2}\\
\frac{\partial L}{\partial \beta _{0}} =\sum _{i=1}^{N} 2w_{i}(\hat{y}_{i} -y_{i}) =0\\
\frac{\partial L}{\partial \beta _{1}} =\sum _{i=1}^{N} 2w_{i}(\hat{y}_{i} -y_{i}) x_{i} =0
$$

One can easily derive that the formula is very similar to the previous one.

$$
\begin{gather*}
\begin{cases}
\beta _{0} +\beta _{1}\overline{x} =\overline{y}\\
\beta _{0}\overline{x} +\beta _{1}\overline{x^{2}} =\overline{xy}
\end{cases}\\
\overline{x} =\frac{\sum _{i=1}^{N} w_{i} x_{i}}{\sum _{i=1}^{N} w_{i}} ,\overline{y} =\frac{\sum _{i=1}^{N} w_{i} y_{i}}{\sum _{i=1}^{N} w_{i}} ,\dots;w_{i} =\frac{\sigma ^{2}}{\sigma _{i}^{2}}\\
\begin{cases}
\beta _{0} =\frac{\overline{x}^{2}\overline{y} -\overline{x}\overline{xy}}{\overline{x^{2}} -\overline{x}^{2}}\\
\beta _{1} =\frac{\overline{xy} -\overline{x}\overline{y}}{\overline{x^{2}} -\overline{x}^{2}}
\end{cases}
\end{gather*}
$$

The formula is exactly the same as before, only the summation is replaced by the weighted summation.

## Non Linear Regression

There is a non-linear model $y=f(x;\beta),x\in\mathbb{R}^n,\beta\in \mathbb{R}^p$, you did same experiment and got some data

$$
(x_1,y_1),(x_2,y_2),\ldots,(x_N,y_N).
$$

How to use these data to estimate the parameters ?

Both least squares method and the maximum likelihood method are to minimize the following function

$$
L(\beta)=\sum_{i=1}^N w_i(y_i-\hat y_i)^2\\
\hat y_i = f(x_i;\beta)
$$

By $\frac{\partial L}{\partial \beta}=0$, we get

$$
\sum _{i=1}^{N} 2w_i( f( x_{i} ;\beta ) -y_{i})\frac{\partial f}{\partial \beta }( x_{i} ;\beta ) =0
$$

Now we cannot do more calculation. In fact, for a non-linear model, we often use the numeral optimizer to do least squares.

## General Linear Regression and General Least Squares Question

We specialize our model to **general linear model**

$$
f=\beta_0 + \beta_1f_1(x)+\beta_2f_2(x)+\cdots+\beta_pf_p(x)\\
L=\sum _{i=1}^{N} w_{i}( y_{i} -\hat{y}_{i})^{2} =\sum _{i=1}^{N} w_{i}\left(\sum _{j=0}^{p} \beta _{p} f_{p}( x_{i}) -y_{i}\right)^{2}
$$

### An analytical way to least squares

Of cause, you can directly get the result by $\frac{\partial L}{\partial \beta}=0$,

$$
\sum _{i=1}^{N}w_i\left(\sum _{j=0}^{p} \beta _{j} f_{j}( x_{i}) -y_{i}\right) f_{j}( x) =0,j=0,\dotsc ,p
\\
\begin{pmatrix}
1 & \overline{f_{1}( x)} & \cdots  & \overline{f_{p}( x)}\\
\overline{f_{1}( x)} & \overline{f_{1}( x) f_{1}( x)} &  & \overline{f_{p}( x) f_{1}( x)}\\
\vdots  &  &  & \vdots \\
\overline{f_{p}( x)} & \overline{f_{1}( x) f_{p}( x)} & \cdots  & \overline{f_{p}( x) f_{p}( x)}
\end{pmatrix}\begin{pmatrix}
\beta _{0}\\
\beta _{1}\\
\vdots \\
\beta _{p}
\end{pmatrix} =\begin{pmatrix}
\overline{xy}\\
\overline{f_{1}( x) y}\\
\vdots \\
\overline{f_{p}( x) y}
\end{pmatrix}
$$

Note that the $\bar{z}$ is weighted sum $\bar{z}=\frac{\sum_{i=1}^N w_iz_i}{\sum_{i=1}^N w_i}$.

Now, how do you ensure that this equation exists a solution?

A better way is to modify the form of the original function.

$$
W=\begin{pmatrix}
w_{1} &  &  & \\
 & w_{2} &  & \\
 &  & \ddots  & \\
 &  &  & w_{n}
\end{pmatrix} ,A=\begin{pmatrix}
1 & f_{1}( x_{1}) & \cdots  & f_{p}( x_{1})\\
1 & f_{1}( x_{2}) & \cdots  & f_{p}( x_{2})\\
\vdots  & \vdots  &  & \vdots \\
1 & f_{1}( x_{N}) & \cdots  & f_{p}( x_{N})
\end{pmatrix}\\
\beta =\begin{pmatrix}
\beta _{0}\\
\beta _{1}\\
\vdots \\
\beta _{p}
\end{pmatrix} ,y=\begin{pmatrix}
y_{1}\\
y_{2}\\
\vdots \\
y_{N}
\end{pmatrix}
$$

Therefore

$$
\hat{y} =A\beta\\
L=( A\beta -y)^{\mathrm{T}} W( A\beta -y)
$$

(If you feel the elegant algebraic perspective behind the equation, you can skip this little part to the next one.)

Now we can use the calculus,

$$
\begin{gather*}
L=( A\beta -y)^{\mathrm{T}} W( A\beta -y)\\
L=\beta ^{\mathrm{T}}\left( A^{\mathrm{T}} WA\right) \beta -2y^{\mathrm{T}} WA\beta +y^{\mathrm{T}} y\\
\frac{\partial L}{\partial \beta } =2\beta ^{\mathrm{T}} A^{\mathrm{T}} WA-y^{\mathrm{T}} WA=0\\
\Rightarrow A^{\mathrm{T}} WA\beta =A^{\mathrm{T}} Wy\\
\beta =\left( A^{\mathrm{T}} WA\right)^{-1} A^{\mathrm{T}} Wy
\end{gather*}
$$

Now, we get the general linear regression formula

$$
\beta =\left( A^{\mathrm{T}} WA\right)^{-1} A^{\mathrm{T}} Wy \tag{GLRE}
$$

However, we still do not prove why $A^{\mathrm{T}} WA$ is invertible here. Because it is an algebraic problem.

### An algebraic perspective of Least Squares

#### Restating the problem in algebraic perspective

Maybe some of you have find that the least squares problem is just the minimize problem in linear algebra.

Consider a linear space $V=\mathbb{R}^{\{x_1,\ldots,x_N\}}\simeq \mathbb{R}^N$. ($A^B$ means functions from $B$ to $A$, $A^B:=\{f:A\to B\}$)

We have two ways to denote the vectors in the linear space:

- Abstractly denote by a function $f\in\mathbb{R}^{\{x_1,\ldots,x_N\}}$;
- Denote by a list $f=\begin{pmatrix}f( x_{1})\\ \vdots \\ f( x_{N}) \end{pmatrix} \in \mathbb{R}^{N}$ 

Both notion will be used in the lecture note. In fact the second notion is the representation of a vector in $V$ by discrete delta function $\delta_i(x_j)=\delta_{ij}$.

If we equip this linear space with a inner product by

$$
\langle f\vert g\rangle = \sum_{i=1}^N w_if(x_i)g(x_i) = f^{\mathrm{T}}Wg\\
W=\begin{pmatrix}
w_{1} &  &  & \\
 & w_{2} &  & \\
 &  & \ddots  & \\
 &  &  & w_{n}
\end{pmatrix}
$$

Then problem becomes to find the minimal distance between vectors in $U=\mathrm{span}\{f_0,\ldots,f_p\}$ and $y$ and which vector in $U$ reach it. 

> **The statement of Our Problem in Linear Algebra**
>
> The linear space $V=\mathbb{R}^{\{x_1,\ldots,x_N\}}\simeq \mathbb{R}^N$ is equipped with the inner product
> 
> 
> 
> 
> 
> $$
> \langle f\vert g\rangle = \sum_{i=1}^N w_if(x_i)g(x_i) = f^{\mathrm{T}}Wg
> $$
> 
> 
> 
> 
> 
> $y$ is a vector in $V$ and $U=\mathrm{span}\{f_0,\ldots,f_p\}$ is a subspace of $V$. 
>
> We need to find the vector $u$ in $U$ which reaches the minimal distance between $y$, i.e.
> 
> 
> 
> 
> 
> $$
> \Vert u-y\rVert=\min_{\hat u\in U}\lVert \hat u-y\rVert.
> $$
> 
> 
> 
> 
> 
> And to get the coefficients $\{\beta_i\}_{i=1}^N$ of this $u$ expanded by $\{f_0,\ldots,f_p\}$, i.e. 
> 
> 
> 
> 
> 
> $$
> u=\sum_{i=0}^N \beta_if_i
> $$
> 
> 
> 
> 
> 

Because is a inner product space, the solution is very simple, it is just the minimization theorem. 

#### A concise review of linear algebra

Consider $V$ is a inner product space. If $U$ is a subset of $V$, the **orthogonal complement** is the set of all vectors that are orthogonal to every vector in $U$, denoted by $U^{\perp}:=\{v\in V:\langle u\vert v\rangle=0,\forall u\in U\}$. It is not hard to see that $U^{\perp}$ is a linear subspace of $V$.

For example, ${V}^\perp=\{0\},\{0\}^\perp=V$.

>  The whole space $V$ can be decompose by $U$ and it's orthogonal complement if **$\boldsymbol{U}$ is finite-dimensional**.
> 
> 
> 
> 
> 
> 
> $$
> V=U\oplus U^{\perp}
> $$
> 
> 
> 
> 
> 

> Proof:
>
> Frist we can show that $V=U+U^\perp$. Let $e_1,\ldots,e_m$ be an orthonormal basis of $U$
> 
> 
> 
> 
> 
> $$
> v=\sum_{i=1}^m \vert e_i\rangle\langle e_i\vert v\rangle+\left(v-\sum_{i=1}^m \vert e_i\rangle\langle e_i\vert v\rangle\right).
> $$
> 
> 
> 
> 
> 
> One can easily check that 
> 
> 
> 
> 
> 
> $$
> \sum_{i=1}^m \vert e_i\rangle\langle e_i\vert v\rangle \in U,v-\sum_{i=1}^m \vert e_i\rangle\langle e_i\vert v\rangle\in U^\perp.
> $$
> 
> 
> 
> 
> 
> And one can easily find that
> 
> 
> 
> 
> 
> $$
> U\cap U^\perp=\{0\}
> $$
> 
> 
> 
> 
> 
> QED.

So we can define the **orthogonal projection** $P_U:V\to U$ by the decomposition $V=U\oplus U^\perp$,

$$
\forall v\in V,\exists !u\in U,\exists !w\in U^{\perp } ,v=u+w,u\in U,w\in U^{\perp }\\
P_{U} :v\mapsto u
$$

One can easily find these properties of orthogonal projection

- $P_U u=u$ for every $u\in U$
- $P_U w=0$ for every $w\in U^\perp$
- $P_U^2=P_U$, thus $P_U$ is indeed a projection operator.
- $\mathrm{range}\,P_U=U,\mathrm{ker}\,P_U=U^\perp$
- $v-P_Uv\in U^\perp$ for every $v\in V$
- $\lVert P_Uv\rVert\leq\lVert v\rVert$ for every $v\in V$

By the proof before we can find that a way to construct $P_U$ by $U$'s orthogonal basis $\{e_i\}_{i=1}^m$.

$$
U=\sum_{i=1}^m \vert e_i\rangle\langle e_i\vert
$$

Finally we can state the **minimization theorem** in linear algebra:

>  **Minimization Theorem**:
>
>  Suppose $U$ is a finite-dimensional subspace of $V$, for any $v\in V$. Then
>  $$
>  \lVert v-P_Uv\rVert\leq\lVert v-u\rVert,\forall u\in U
>  $$

> Proof:
> 
> 
> 
> 
> 
> $$
> \begin{aligned}
> \left\|v-P_U v\right\|^2 & \leq\left\|v-P_U v\right\|^2+\left\|P_U v-u\right\|^2 \\
> & =\left\|\left(v-P_U v\right)+\left(P_U v-u\right)\right\|^2 \\
> & =\|v-u\|^2
> \end{aligned}
> $$
> 
> 
> 
> 
> 
>
> The first line hold because $0\leq\lVert P_Uv-u\rVert$. The second line hold because the Pythagorean theorem, which state that if $\langle u\vert v\rangle=0$, 
> 
> 
> 
> 
> 
> $$
> \lVert u+v\rVert^2 = \lVert u\rVert^2+\lVert v\rVert^2
> $$
> 
> 
> 
> 
> 

#### How to Really Solve the Problem and Represent The Result in Matrices Form

Now return to our original problem. Let's state our problem again:

> The linear space $V=\mathbb{R}^{\{x_1,\ldots,x_N\}}\simeq \mathbb{R}^N$ is equipped with the inner product
> 
> 
> 
> 
> 
> $$
> \langle f\vert g\rangle = \sum_{i=1}^N w_if(x_i)g(x_i) = f^{\mathrm{T}}Wg
> $$
> 
> 
> 
> 
> 
> $y$ is a vector in $V$ and $U=\mathrm{span}\{f_0,\ldots,f_p\}$ is a subspace of $V$, we need to find the coefficients $\beta_i$ of $u=\sum_{i=0}^N\beta_i f_i$ which reaches the minimal distance  
> 
> 
> 
> 
> 
> $$
> \Vert u-y\rVert=\min_{\hat u\in U}\lVert \hat u-y\rVert
> $$
> 
> 
> 
> 
> 

The minimization theorem tells us that the vector reaches the minimal distance is $u=P_Uv$. However, to really solve the least squares problem, we have to expand $P_Uv$ in to $f_0,\cdots,f_p$. This seems to be trivial, but it is hard to get the result.

So we construct the linear space $\mathbb{R}^p$ equipped with the standard inner product to represent the coefficients $\beta =( \beta _{0} ,\dotsc ,\beta _{p})^{\mathrm{T}}$. And construct a map $A:\mathbb{R}^p\to V$ by

$$
A\beta = \sum_{j=0}^p \beta_jf_j.
$$

So $\mathrm{range}\,A=U$, we need to solve the equation

$$
A\beta=P_Uy
$$

We can apply $A^\dagger$ on both side and using the property of adjoint[^1]

[^1]: $T^{\dagger } v=0\Leftrightarrow \langle w,T^{\dagger } v\rangle =0,\forall w\Leftrightarrow \langle v,Tw\rangle =0,\forall w\Leftrightarrow v\in (\mathrm{range} \ T)^{\perp }$

$$
\ker (T^\dagger) = (\mathrm{range}\,T)^\perp
$$

We get

$$
\ker A^\dagger=U^\perp, y-P_Uy\in U^\perp \\
\Rightarrow A^{\dagger } A\beta =A^{\dagger } P_{U} y=A^{\dagger }[ P_{U} y+( y-P_{U} y)] =A^{\dagger } y
$$

Here $A^\dagger A$ is invertible if $f_0,\ldots,f_p$ is linearly independent. Because

$$
A^{\dagger } A\gamma =0\\
\Rightarrow A\gamma \in \ker A^{\dagger } =\left(\operatorname{range} A\right)^{\perp }\\
\Rightarrow A\gamma \in \left(\operatorname{range} A\right)^{\perp } \cap \operatorname{range} A=\{0\}\\
\Rightarrow A\gamma =0\\
\Rightarrow \sum _{i=0}^{p} \gamma _{i} f_{i} =0\\
\Rightarrow \gamma _{i} \equiv 0\\
\Rightarrow \gamma = 0
$$

So the result is

$$
\beta = (A^\dagger A)^{-1}A^\dagger y.
$$

Now, does it end? Remember that we are solving a practical problem. We need to offer the result by matrices rather than abstract operators.

Consider to use the standard basis of $\mathbb{R}^p$ and the discrete delta functions $\{\delta_i:\delta_i(x_k)=\delta_{ik}\}$ as the basis of $V=\mathbb{R}^{\{x_1,\ldots,x_N\}}$. The matrices form is

$$
\begin{gather*}
A=\begin{pmatrix}
1 & f_{1}( x_{1}) & \cdots  & f_{p}( x_{1})\\
1 & f_{1}( x_{2}) & \cdots  & f_{p}( x_{2})\\
\vdots  & \vdots  &  & \vdots \\
1 & f_{1}( x_{N}) & \cdots  & f_{p}( x_{N})
\end{pmatrix} ,\beta =\begin{pmatrix}
\beta _{0}\\
\beta _{1}\\
\vdots \\
\beta _{p}
\end{pmatrix} ,y=\begin{pmatrix}
y_{1}\\
y_{2}\\
\vdots \\
y_{N}
\end{pmatrix}\\
W=\begin{pmatrix}
w_{1} &  & \\
 & \ddots  & \\
 &  & w_{N}
\end{pmatrix} ,\langle u,v\rangle _{V} =u^{\mathrm{T}} Wv,A^{\dagger } =A^{\mathrm{T}} W
\end{gather*}
$$

One can easily check those matrices representations. For the last one

$$
\langle v,Aw\rangle _{V} =u^{\mathrm{T}} WAw=\left( A^{\mathrm{T}} Wu\right)^{\mathrm{T}} w=\langle A^{\dagger } u,w\rangle _{\mathbb{R}^{p}}
$$

So the result is

$$
( \beta _{0} ,\dotsc ,\beta _{N})^{\mathrm{T}} =\beta =\left( A^{\mathrm{T}} WA\right)^{-1} AWy,
$$

which is the same with the analytical one.




> **Exercise**
>
> 1. Get the least squares formula of 1D-polynomial regression formula.
> 2. Get the least squares formula of ND-linear regression formula.



## The Confidence Interval of Parameters

To get the confidence interval of parameters, we should treat the relationship between data $\{x_i,y_i,w_i\}_{i=1}^N$ and regression result $\beta$ as a estimator.

$$
\hat \beta = \hat \beta\left(\{x_i,y_i,w_i\}_{i=1}^N\right)
$$

Now the $\hat \beta$ is a statistic of sample data. The interval is just the standard error of $\hat \beta$

## Reference

1. [STAT 224 Lecture 14 Chapter 7 Weighted Least Squares, University of Chichago Department of Statistics](https://www.stat.uchicago.edu/~yibi/teaching/stat224/L14.pdf)
2. [Tutorial 2: Linear regression with MLE, Neuromatch computational neuroscience course](https://compneuro.neuromatch.io/tutorials/W1D2_ModelFitting/student/W1D2_Tutorial2.html)
3. [Interactive Linear Algebra, Section 6.3 Theorem](https://textbooks.math.gatech.edu/ila/projections.html)
4. [Linear Algebra Down Right, Minimization Problems](https://textbooks.math.gatech.edu/ila/projections.html)
5. [Prof Xilin Xie's online class, Examples of Mathematical Analysis Zorich: Least Squares Problem](https://www.bilibili.com/video/BV1oN411c7ze/?spm_id_from=333.999.0.0&vd_source=e83f6243963f730d4d2994d23f588a9d)