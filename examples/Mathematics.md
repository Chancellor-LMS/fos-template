---
name: "Mathematics (MathJax)"
---

# Mathematics

Chancellor supports rendering mathematics expressions using [MathJax](https://www.mathjax.org/).

## Inline Math

Use `$` to wrap the math expression. For example, `$\sqrt{3x-1}+(1+x)^2$` will be rendered as $\sqrt{3x-1}+(1+x)^2$.

## Block Math

Use `$$` to wrap the math expression. For example:

```markdown
$$
\begin{aligned}
f(x) &= x^2 + 2x + 1 \\
&= (x + 1)^2 \\
&= (x + 1)(x + 1) \\
\end{aligned}
$$
```

Is rendered as:

$$
\begin{aligned}
f(x) &= x^2 + 2x + 1 \\
&= (x + 1)^2 \\
&= (x + 1)(x + 1) \\
\end{aligned}
$$

## Math Symbols

You can find a list of supported symbols and functions in the [MathJax documentation](http://docs.mathjax.org/en/latest/input/tex/macros/index.html).

For example:

| Syntax | Result |
| ------ | ------ |
| `$\alpha$` | $\alpha$ |
| `$\beta$` | $\beta$ |
| `$\gamma$` | $\gamma$ |
| `\frac{a}{b}` | $\frac{a}{b}$ |
| `\int_{a}^{b}` | $\int_{a}^{b}$ |
| `\sum_{n=1}^{10}` | $\sum_{n=1}^{10}$ |

## Showcase: Explicit Euler Method

First-order ordinary differential equations are equations that contain a function and its first derivative, such as:

$$
y'(t) = f(t,y)
$$

Where $y$ is a real-valued function of the real variable $t$, $y'(t) \equiv \frac{dy}{dt}$, and $f$ is a real-valued function of two real variables.

Approximate the derivative by **Explicit Euler Method**:

$$
\begin{aligned}
\frac{y(t_n + 1) - y(t_n)}{h} &\approx y'(t_n) \\
\frac{y_{n + 1} - y_{n}}{h} &\approx f(t_n, y(t_n)) \\
\frac{y_{n + 1} - y_{n}}{h} &\approx f(t_n, y_n) \\
y_{n + 1} &\approx y_n + h f(t_n, y_n)
\end{aligned}
$$

Alternatively, derive by integration using left-rectangle rule:

$$
\begin{aligned}
\int_{t_n}^{t_{n+1}} y'(t) dt &\approx \int_{t_n}^{t_{n+1}} f(t, y(t)) dt \\
y(t_{n+1}) - y(t_n) &\approx (t_{n+1} - t_n) f(t_n, y(t_n)) \\
y_{n+1} &\approx y_n + h f(t_n, y_n)
\end{aligned}
$$

The **global error** can be measured by summing the local error across the $m-1$ time-steps:

$$
\begin{aligned}
e_m &= \sum_{n=0}^{m-1} \max_{\xi \in [t_n, t_{n+1}]} \frac{h^2f''(\xi)}{2} \\
 &\leq \frac{mh^2}{2T} \max_{\xi \in [t_0, T_M]} f''(\xi) \\
  &\leq \frac{h}{2}\max_{\xi \in [t_0, T_M]} f''(\xi)
\end{aligned}
$$

::: details | Source (click to expand)

```markdown
First-order ordinary differential equations are equations that contain a function and its first derivative, such as:

$$
y'(t) = f(t,y)
$$

Where $y$ is a real-valued function of the real variable $t$, $y'(t) \equiv \frac{dy}{dt}$, and $f$ is a real-valued function of two real variables.

Approximate the derivative by **Explicit Euler Method**:

$$
\begin{aligned}
\frac{y(t_n + 1) - y(t_n)}{h} &\approx y'(t_n) \\
\frac{y_{n + 1} - y_{n}}{h} &\approx f(t_n, y(t_n)) \\
\frac{y_{n + 1} - y_{n}}{h} &\approx f(t_n, y_n) \\
y_{n + 1} &\approx y_n + h f(t_n, y_n)
\end{aligned}
$$

Alternatively, derive by integration using left-rectangle rule:

$$
\begin{aligned}
\int_{t_n}^{t_{n+1}} y'(t) dt &\approx \int_{t_n}^{t_{n+1}} f(t, y(t)) dt \\
y(t_{n+1}) - y(t_n) &\approx (t_{n+1} - t_n) f(t_n, y(t_n)) \\
y_{n+1} &\approx y_n + h f(t_n, y_n)
\end{aligned}
$$

The **global error** can be measured by summing the local error across the $m-1$ time-steps:

$$
\begin{aligned}
e_m &= \sum_{n=0}^{m-1} \max_{\xi \in [t_n, t_{n+1}]} \frac{h^2f''(\xi)}{2} \\
 &\leq \frac{mh^2}{2T} \max_{\xi \in [t_0, T_M]} f''(\xi) \\
  &\leq \frac{h}{2}\max_{\xi \in [t_0, T_M]} f''(\xi)
\end{aligned}
$$
```

Now that we're in a custom block, let's hope that maths still works:

$$
\begin{aligned}
f(x) &= x^2 + 2x + 1 \\
&= (x + 1)^2 \\
&= (x + 1)(x + 1) \\
\end{aligned}
$$

:::