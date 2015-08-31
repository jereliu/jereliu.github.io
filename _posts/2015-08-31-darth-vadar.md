---
title: Darth Vadar's Mean Survival Time
layout: post
external: [latex]
---


<center><img src="/download/posts/darth_cookie.jpg" alt="I find your lack of cookie disturbing" style="width: 400px;" vspace="30"/></center>




In this post we are interested in proving the [Darth Vadar Rule](https://www.sav.sk/journals/uploads/1030150905-M-O-W.pdf):

$$E(X) = \int_{\mathbb{R}_+}S(x)dx 
\qquad x\in \mathbb{R}_+$$

where $S(x) = 1 - F(x)$ is the survival function. We also want to  illustrate its usage in showing the closed form expression of mean survival time 
$E(t-t_0|t>t_0)$.


---


#### First, a Calculus proof of **Darth Vadar Rule**:

$$
\begin{align}
E(X) &= \int_{\mathbb{R}_+} x*f(x) dx \\
& =  
\lim_{t \rightarrow \infty} \int_0^t x*f(x) dx 
\qquad \mbox{(note } \frac{\partial}{\partial x}S(x) = -f(x) )
\\
&= \lim_{t \rightarrow \infty}
\Big[
-t*S(t) + \int_0^t S(x) dx
\Big]
\quad \mbox{(integration by parts)} \\
&= 
\underline{- \lim_{t \rightarrow \infty} t*S(t)} +  \int_{\mathbb{R}_+} S(x) dx \qquad \mbox{(claim } \lim_{t \rightarrow \infty} t*S(t) = 0) \\
& =  \int_{\mathbb{R}_+} S(x) dx 
\end{align}
$$

Now only need to show the claim $\lim_{x \rightarrow \infty} x*S(x) = 0$. We can show this by showing $0 \leq \lim_{x \rightarrow \infty} x*S(x)  \leq 0$:

$$
\begin{align}
\lim_{x \rightarrow \infty} x*S(x) &\geq 0 \\
\lim_{x \rightarrow \infty} x*S(x) &=
 \lim_{x \rightarrow \infty} x*\int_x^\infty f(t) dt \\
&= \lim_{x \rightarrow \infty} \int_x^\infty x*f(t) dt
\qquad \mbox{(note x is constant w.r.p. t)} \\
&\leq  \lim_{x \rightarrow \infty} \int_x^\infty t*f(t) dt
= 0
\end{align}
$$

and conclude $\lim_{x \rightarrow \infty} x*S(x) = 0$  by [the squeeze theorem](https://en.wikipedia.org/wiki/Squeeze_theorem).

---

#### Now, **Mean Survival Time**:
Want to show:

$E(T-t_0|T>t_0) = \int_{t_0}^\infty \frac{S_T(t)}{S_T(t_0)}dt \qquad 
T > t_0
$

Note if we define $R = T-t_0$ above formula is just a straightforward application of the Darth Vadar rule, i.e. 

$$E(T-t_0|T>t_0) = E(R|R>0) = E(R) = \int_{\mathbb{R}_+} S_R(r) dr$$

we only need to express $S_R(r)$ in terms of $S_T(t)$:

$$
\begin{align}
S_R(r) &= P(R\geq r|R \geq 0) \\
&= P(T-t_0 \geq r|T-t_0 \geq 0) = P(T \geq r+t_0|T \geq t_0) \\
& = \frac{P(T \geq r+t_0)}{P(T \geq t_0)}\\
& = \frac{S_T(t_0+r)}{S_T(t_0)}
\end{align}
$$

and plug this expression into 
$\int_{\mathbb{R}_+} S_R(r) dr$:

$$
\begin{align}
E(T-t_0|T>t_0) &=  \int_{\mathbb{R}_+} S_R(r) dr\\
&= \int _0^\infty \frac{S_T(t_0+r)}{S_T(t_0)} dr\\
& (\mbox{now define } t = r + t_0, \mbox{do change of variable} )\\
& =  \int _{t_0}^\infty \frac{S_T(t)}{S_T(t_0)} dt\\
\end{align}
$$

Easy breezy~