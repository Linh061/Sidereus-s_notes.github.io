---
layout: post
title: "Differential Equations – Study Notes"
categories: math
math: true
---

## 1. Basic Definitions

- **Differential equation (DE)**: An equation that relates an unknown function with one or more of its derivatives.
- **Ordinary differential equation (ODE)**: Contains derivatives with respect to a **single** independent variable.
- **Partial differential equation (PDE)**: Contains partial derivatives with respect to **multiple** independent variables.
- **Order**: The highest derivative appearing in the equation.
- **Degree**: The power of the highest derivative (when the DE is expressed as a polynomial in derivatives).
- **Linear DE**:
  - The dependent variable and its derivatives appear linearly (no products, no nonlinear functions).
  - General form for ODE of order $n$:
    $$ a_n(x) y^{(n)} + a_{n-1}(x) y^{(n-1)} + \dots + a_1(x) y' + a_0(x) y = g(x). $$
- **Nonlinear DE**: Any DE that is not linear (e.g., $y y' + y = 0$, $(y'')^2 + y = 0$, $\sin(y') = y$).

## 2. Classification of ODEs

| Type                | Example                                    | Characteristics                       |
|---------------------|--------------------------------------------|---------------------------------------|
| Separable           | $\frac{dy}{dx} = \frac{x}{y}$              | $f(x)dx = g(y)dy$                     |
| First-order linear  | $y' + p(x)y = q(x)$                        | Integrating factor $\mu = e^{\int p dx}$|
| Exact               | $M(x,y)dx + N(x,y)dy = 0$ with $M_y = N_x$| Potential function $\psi(x,y)=C$      |
| Homogeneous (order 0)| $y' = F(y/x)$                             | Substitution $v = y/x$                |
| Bernoulli           | $y' + p(x)y = q(x) y^n$                    | Set $v = y^{1-n}$                     |
| Second-order linear | $y'' + p(x)y' + q(x)y = r(x)$              | Superposition principle, Wronskian    |

## 3. First‑Order ODEs – Solution Methods

### 3.1 Separable equations
$$\frac{dy}{dx} = g(x)h(y) \quad \Rightarrow \quad \int \frac{dy}{h(y)} = \int g(x) dx + C.$$

### 3.2 Linear equations
$$y' + p(x)y = q(x)$$
1. Compute integrating factor $\mu(x) = e^{\int p(x) dx}$.
2. Multiply both sides: $\frac{d}{dx}(\mu y) = \mu q$.
3. Integrate: $y = \frac{1}{\mu}\left( \int \mu q \, dx + C \right)$.

### 3.3 Exact equations
$M(x,y)\,dx + N(x,y)\,dy = 0$ is exact iff $\frac{\partial M}{\partial y} = \frac{\partial N}{\partial x}$.
Find $\psi(x,y)$ such that $\psi_x = M$, $\psi_y = N$; then $\psi(x,y) = C$.

### 3.4 Substitution methods
- **Homogeneous** $y' = F(y/x)$: let $v = y/x$.
- **Bernoulli** $y' + p(x)y = q(x)y^n$: let $v = y^{1-n}$ (reduces to linear).

## 4. Second‑Order Linear ODEs

### 4.1 Homogeneous with constant coefficients
$$a y'' + b y' + c y = 0$$
Characteristic equation: $a r^2 + b r + c = 0$.

| Discriminant | Roots $r_1, r_2$ | General solution                          |
|--------------|------------------|-------------------------------------------|
| $>0$         | real, distinct   | $y = C_1 e^{r_1 x} + C_2 e^{r_2 x}$       |
| $=0$         | real, double $r$ | $y = (C_1 + C_2 x) e^{r x}$               |
| $<0$         | complex $\alpha \pm i\beta$ | $y = e^{\alpha x}(C_1 \cos\beta x + C_2 \sin\beta x)$ |

### 4.2 Non‑homogeneous – method of undetermined coefficients
$$a y'' + b y' + c y = g(x)$$
General solution: $y = y_h + y_p$ (homogeneous + particular).

Choose $y_p$ based on $g(x)$:

| $g(x)$               | Trial $y_p$                                         |
|----------------------|-----------------------------------------------------|
| $P_n(x)$ (polynomial) | $x^s Q_n(x)$                                        |
| $e^{\alpha x}$        | $x^s A e^{\alpha x}$                                |
| $\sin(\beta x)$ or $\cos(\beta x)$ | $x^s (A\sin\beta x + B\cos\beta x)$ |
| $e^{\alpha x}\sin(\beta x)$ | $x^s e^{\alpha x}(A\sin\beta x + B\cos\beta x)$ |

The factor $x^s$ ($s=0,1,2$) is chosen so that no term in $y_p$ duplicates a solution of the homogeneous equation.

### 4.3 Variation of parameters (general method)
For $y'' + p(x)y' + q(x)y = g(x)$:
$$y_p = y_1\int \frac{-y_2 g}{W} dx + y_2\int \frac{y_1 g}{W} dx,$$
where $y_1, y_2$ are fundamental solutions of the homogeneous equation and $W = y_1 y_2' - y_2 y_1'$ is the Wronskian.

## 5. Applications

### 5.1 Population growth (Malthusian)
$$\frac{dP}{dt} = kP \quad \Rightarrow \quad P(t) = P_0 e^{kt}.$$

### 5.2 Logistic growth
$$\frac{dP}{dt} = rP\left(1 - \frac{P}{K}\right) \quad \Rightarrow \quad P(t) = \frac{K}{1 + \left(\frac{K}{P_0} - 1\right)e^{-rt}}.$$

### 5.3 Newton’s law of cooling
$$\frac{dT}{dt} = -k(T - T_{\text{amb}}) \quad \Rightarrow \quad T(t) = T_{\text{amb}} + (T_0 - T_{\text{amb}})e^{-kt}.$$

### 5.4 RLC circuit (second order)
$$L\frac{d^2q}{dt^2} + R\frac{dq}{dt} + \frac{1}{C}q = E(t) \quad \text{or} \quad L\frac{di}{dt} + Ri + \frac{1}{C}\int i\,dt = E(t).$$

### 5.5 Harmonic oscillators
- **Undamped**: $m x'' + kx = 0$ → simple harmonic motion.
- **Damped**: $m x'' + c x' + kx = 0$ (over‑, critical‑, under‑damped).
- **Forced**: $m x'' + c x' + kx = F_0 \cos(\omega t)$ → resonance when $\omega \approx \sqrt{k/m}$.

## 6. Laplace Transforms (for IVPs)

Definition:
$$\mathcal{L}\{f(t)\} = F(s) = \int_0^{\infty} e^{-st} f(t) dt.$$

### Useful transforms

| $f(t)$                     | $F(s)$                             |
|----------------------------|------------------------------------|
| $1$                        | $\frac{1}{s}$                      |
| $t^n$                      | $\frac{n!}{s^{n+1}}$               |
| $e^{at}$                   | $\frac{1}{s-a}$                    |
| $\sin(\omega t)$           | $\frac{\omega}{s^2+\omega^2}$      |
| $\cos(\omega t)$           | $\frac{s}{s^2+\omega^2}$           |
| $t^n e^{at}$               | $\frac{n!}{(s-a)^{n+1}}$           |
| $f'(t)$                    | $sF(s) - f(0)$                     |
| $f''(t)$                   | $s^2F(s) - s f(0) - f'(0)$         |
| $e^{at}f(t)$               | $F(s-a)$ (first shifting theorem)  |

### Solving IVPs using Laplace
1. Apply $\mathcal{L}$ to both sides of the ODE.
2. Use initial conditions and table of transforms.
3. Solve for $Y(s) = \mathcal{L}\{y(t)\}$.
4. Compute inverse Laplace (partial fractions + tables).

## 7. Systems of ODEs (optional)

A system of first‑order linear ODEs can be written as
$$\mathbf{x}' = A \mathbf{x}, \quad \mathbf{x}(t) \in \mathbb{R}^n,$$
with solution $\mathbf{x}(t) = e^{At} \mathbf{x}(0)$, where $e^{At}$ is the matrix exponential.

For non‑homogeneous systems $\mathbf{x}' = A\mathbf{x} + \mathbf{f}(t)$, use variation of parameters or Laplace transforms.

## 8. Quick Checklist for Solving ODEs

- [ ] Identify order and linearity.
- [ ] For first order: try separation → linear → exact → substitution.
- [ ] For second order constant coefficients: write characteristic equation.
- [ ] For non‑homogeneous: choose undetermined coefficients (if $g(x)$ is simple) or variation of parameters.
- [ ] For IVPs with discontinuous inputs or initial conditions at 0, use Laplace transform.
- [ ] Check your solution by plugging back into the ODE.

---

*Happy solving!* 