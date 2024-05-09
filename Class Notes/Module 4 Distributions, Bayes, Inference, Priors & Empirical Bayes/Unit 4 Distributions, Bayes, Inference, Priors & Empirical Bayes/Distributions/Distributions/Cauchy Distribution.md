# What is it?
- The Cauchy distribution, or the Lorentzian distribution, is a continuous probability distribution that is the ratio of two independent normally distributed random variables if the denominator distribution has mean zero. It is a “pathological” distribution, i.e. both its expected value and its variance are undefined

# Numerical Characteristics

- **PDF:** $f(x|x_0,\gamma) = \frac{1}{\pi\gamma[1 + ((x-x_0)/\gamma)^2]}$
- **CDF:** $F(x|x_0,\gamma) = \frac{1}{\pi}\arctan\left(\frac{x-x_0}{\gamma}\right) + \frac{1}{2}$
- **Mean:** undefined
- **Variance:** undefined
- **Support:** $(-\infty, \infty)$
- **Parameters:** $x_0$ (location), $\gamma$ (scale)
- **Notation:** $X \sim Cauchy(x_0, \gamma)$