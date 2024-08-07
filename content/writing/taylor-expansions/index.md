---
title: "Taylor expansions: An easy derivation"
subtitle: Repeatedly use the fundamental theorem of calculus to get Taylor expansions.
date: 2021-01-10
lastmod: 2021-07-02
draft: false
tags:
  - math
---

# Introduction

Recently I had to bound the error in a Taylor expansion.
However, I forgot the form of the error term and had to look it up.
This was not the first time I've had to look it up.
In fact, though I first learned about Taylor expansions in 2014{{< sidenote >}}
    Shoutout to Ms. Dartnell!
{{< /sidenote >}},
up till 2021 I struggled to remember their remainder formula.

This post is my attempt to
re-derive Taylor expansions and their error term
in a way I can finally remember.

# Approach

To remember Taylor expansions, all you need to remember is the **fundamental theorem of calculus (FTC)**. If you repeatedly apply the FTC, the Taylor expansion will emerge.

The FTC says that for a function{{< sidenote >}}
    To be precise,
    for the FTC to hold $f$ needs to have a derivative $f'$
    that is sufficiently well behaved.
    For example,
    it suffices for $f'$ to be continuous.
{{< /sidenote >}}
$f: \mathbb{R} \to \mathbb{R}$
and a base point $c \in \mathbb{R}$,
the value of $f$ at a point $x \in \mathbb{R}$
is given by

$$f(x) = f(c) + \int_{c}^x f'(t)\\, dt.$$

This is "fundamental" because it relates the two key ideas of calculus, derivatives and integrals, and says they are inverses of each other.

# Taylor expansions from the FTC

How do we get Taylor expansions from the FTC? It goes like this.

0. To begin, assume $f' = 0$. Then apply the FTC and simplify:

    $$
    \begin{align*}
    f(x)
    &= f(c) + \int_{c}^x f'(t)\\, dt \\\\
    &= f(c) + \int_{c}^x 0\\, dt \\\\
    &= f(c).
    \end{align*}
    $$

    This yields a **zeroth order Taylor expansion**, which approximates $f$ with a constant function based at $c$.

1. Now assume $f'' = 0$. Then apply the FTC twice and simplify:

    $$
    \begin{align*}
    f(x)
    &= f(c) + \int_c^x f'(t_1)\\, dt_1 \\\\
    &= f(c) + \int_c^x \left[ \\, f'(c) + \int_c^{t_1}  f''(t_2)\\, dt_2 \right] dt_1 \\\\
    &= f(c) + f'(c) (x - c) + \int_c^x \int_c^{t_1} f'' (t_2) \\, dt_2 \\, dt_1 \\\\
    &= f(c) + f'(c) (x - c) + \int_c^x \int_c^{t_1} 0   \\, dt_2 \\, dt_1 \\\\
    &= f(c) + f'(c) (x - c).
    \end{align*}
    $$

    We first applied the FTC to $f$ in the first line, then to $f'$ in the second line.

    This yields a **first order Taylor expansion**, which approximates $f$ with a linear function based at $c$.

2. One more. Assume $f''' = 0$ and apply the FTC three times:

    $$\begin{align*}
    f(x)
    &= f(c) + \int_c^x f'(t_1)\\, dt_1 \\\\
    &= f(c) + \int_c^x \left[ \\, f'(c) + \int_c^{t_1} f''(t_2)\\, dt_2\right] dt_1 \\\\
    &= f(c) + f'(c) (x - c) + \int_c^x \int_c^{t_1} f''(t_2) \\, dt_2 \\, dt_1 \\\\
    &= f(c) + f'(c) (x - c) + \int_c^x \int_c^{t_1} \left[ \\, f''(c) + \int_c^{t_2} f'''(t_3) \\, dt_3 \right] dt_2 \\, dt_1 \\\\
    &= f(c) + f'(c) (x - c) + f''(c) \frac{(x - c)^2}{2} + \int_c^x \int_c^{t_1} \int_c^{t_2} f'''(t_3) \\, dt_3 \\, dt_2 \\, dt_1 \\\\
    &= f(c) + f'(c) (x - c) + f''(c) \frac{(x - c)^2}{2} + \int_c^x \int_c^{t_1} \int_c^{t_2} 0 \\, dt_3 \\, dt_2 \\, dt_1 \\\\
    &= f(c) + f'(c) (x - c) + f''(c) \frac{(x - c)^2}{2}.
    \end{align*}
    $$

    This yields a ______ order Taylor expansion, which approximates $f$ with a quadratic function based at $c$.

    I'll let you fill in the blank.

# Taylor expansions: general form

If we continue to above procedure, we get the general form of a $n$-th order Taylor expansion:

$$
\begin{align*}
f(x) &=  f(c) + f'(c) (x-c) + f''(c) \frac{(x - c)^2}{2} + \cdots + \frac{f^{(n)}(c)}{n!}\\, (x-c)^n + R_{f,c,n}(x) \\\\
&= \sum_{k=0}^n \frac{f^{(k)}(c)}{k!}\\,(x-c)^k + R_{f,c,n}(x), \\\\
R_{f,c,n}(x) &\triangleq \int_{c}^x \int_c^{t_1} \int_c^{t_2} \cdots \int_c^{t_{n}}  f^{(n+1)}(t_{n+1}) \\, dt_{n+1} \cdots dt_2\\,dt_1.
\end{align*}
$$

Some comments on this identity:

- $f^{(n)}$ denotes the $n$-th derivative of $f$. So $f^{(0)} = f$, $f^{(1)} = f'$, $f^{(2)} = f''$, and so on.
- $R_{f,c,n}$ is the remainder you get when you approximate $f$ about a base point $c$ with a $n$-th order Taylor expansion. If $f^{(n + 1)} = 0$, then $R_{f,c,n} = 0$.
- This identity is known as **Taylor's theorem**.
{{% expand "A proof of the identity (click to expand)." %}}
---

First, a technical note. In order for Taylor's theorem to hold, we must be able to take enough derivatives of $f$. For Taylor's theorem to hold up to $n$-th order, one sufficient condition is for $f^{(n + 1)}$ to exist and be continuous.

Now onto the proof.

We've already proven Taylor's theorem for $n = 0, 1, 2$.

To prove the theorem for arbitrary $n$, we use induction. Assume Taylor's theorem holds up to $n$-th order, and let $f: \mathbb{R} \to \mathbb{R}$ be $(n+2)$-times continuously differentiable. This means $f^{(n+1)}$ is continuously differentiable, so

$$
\begin{align*}
& f(x) - \sum_{k=0}^n \frac{f^{(k)}(c)}{k!}\\,(x-c)^k \\\\
&= \int_{0}^x \int_0^{t_1} \cdots \int_0^{t_n}  f^{(n+1)}(t_{n+1}) \\, dt_{n+1} \cdots \\,dt_1 \\\\
&= \int_{c}^x \int_c^{t_1} \cdots \int_c^{t_n} \left[ \\, f^{(n+1)}(c) + \int_{c}^{t_{n+1}} f^{(n+2)}(t_{n+2})\\, dt_{n+2} \right] \\, dt_{n+1} \cdots \\,dt_1 \\\\
&= \frac{f^{(n+1)}(c)}{(n+1)!}\\,(x-c)^{(n+1)}\\,\\, +\\, \int_{c}^x \int_c^{t_1} \cdots \int_c^{t_{n+1}}  f^{(n+2)}(t_{n+2}) \\, dt_{n+2} \cdots \\,dt_1.
\end{align*}
$$

To get the last line,
we used the identity{{< sidenote >}}This is the formula for the volume of a $(n + 1)$-dimensional simplex with side length $(x - c)$.{{< /sidenote >}}

$$\int_c^x \int_c^{t_1} \cdots \int_c^{t_n}  1 \\, dt_{n+1} \cdots \\,dt_1
= \frac{(x-c)^{(n+1)}}{(n+1)!}.$$

We have shown that

$$f(x) = \sum_{k=0}^{n+1} \frac{f^{(k)}(c)}{k!}\\,(x-c)^k\\,\\,+\\, \int_c^x \int_c^{t_1} \cdots \int_c^{t_{n+1}}  f^{(n+2)}(t_{n+2}) \\, dt_{n+2} \cdots \\,dt_1,$$

so by induction, Taylor's theorem holds for all $n$. $\square$

---

{{% /expand %}}

# Application: approximating sine

The general form of Taylor's theorem is useful for bounding the error of a Taylor expansion. In particular, if we can bound $f^{(n + 1)}$, then we can bound $R_{f,c,n}(x)$. A coarse bound is the following:

$$
\begin{align*}
\left| R_{f,c,n}(x) \right|
&= \left| \int_c^x \int_c^{t_1} \cdots \int_c^{t_n}  f^{(n+1)}(t_{n+1}) \\, dt_{n+1} \cdots \\,dt_1 \right| \\\\
&\leq \int_c^x \int_c^{t_1} \cdots \int_c^{t_n} \left[ \max_{t \\,\in\\, [c, x]} \left| \\, f^{(n+1)}(t)\right| \right] \\, dt_{n+1} \cdots \\,dt_1 \\\\
&= \frac{(x-c)^{n+1}}{(n+1)!} \cdot\\,\max_{t \\,\in\\, [c, x]} \left| \\, f^{(n+1)}(t) \right|.
\end{align*}
$$

As a concrete example, consider the the sine function. Its infinite-order Taylor expansion (centered at zero) is given by

$$\sin(x) = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \cdots$$

How accurate is the Taylor expansion of sine up to 8th order
in the region{{< sidenote >}}
    We could extend our expansion to
    the entirety of $\mathbb{R}$
    by using the symmetries of the sine function.
{{< /sidenote >}}
$[-\frac{\pi}{2}, \frac{\pi}{2}]$?
Well the 9th derivative of sine is cosine, which over $[-\frac{\pi}{2}, \frac{\pi}{2}]$ has a maximum value of $1$. Thus our 8th order expansion has error at most $(\frac{\pi}{2})^9 / 9! \approx 1.60 \times 10^{-4}$ over $[-\frac{\pi}{2}, \frac{\pi}{2}]$.

How tight is this bound?
Well the actual maximum of
$R_{\sin, 0, 8}$
over $[-\frac{\pi}{2}, \frac{\pi}{2}]$
is approximately
[$\underline{1.57 \times 10^{-4}}$](https://www.wolframalpha.com/input/?i=maximize+|sin(x)+-+(x+-+x^3%2F3!+%2B+x^5%2F5!+-+x^7%2F7!)|+over+[-pi%2F2%2C+pi%2F2]),
so our bound is pretty tight!

Here is a plot of sine and our 8th order expansion:

{{<
    figure
    src="taylor-sine.svg"
    width="400px"
    caption="Sine and its 8th order Taylor expansion about zero. The expansion is very good close to zero, and very bad far away from zero. Image is [from the Wikimedia Commons](https://commons.wikimedia.org/w/index.php?curid=825819)."
>}}

# Final thoughts

I like this derivation of Taylor expansions because it is very easy to remember.
All you have to do is repeatedly apply the fundamental theorem of calculus.

The differentiability conditions presented in this post
are stronger than necessary (see expandable proof).
For example, it suffices for $f^{(n)}$ to be
[absolutely continuous](https://en.wikipedia.org/wiki/Absolute_continuity)
instead of continuously differentiable.
Additionally, differentiability conditions only need to hold
in the region over which we use our expansion,
not the entirety of $\mathbb{R}$.

Finally, here are some links to similar derivations I came across
while working on this post:
- [math.stackexchange.com/a/492165/85418](https://math.stackexchange.com/a/492165/85418)
  is very similar in nature,
  and derives the Lagrange form of Taylor's theorem via the multivariate integral form.
- [youtu.be/y87iKV5PU24](https://youtu.be/y87iKV5PU24) is a nice video
  derivation that uses the same idea as described here.

Thank you for reading and I hope you can better remember
Taylor expansions and remainders in the future!

## Acknowledgements

Thanks to Elton Lin and Horace He for reading drafts of this post.
