# What is it?

- A uniform distribution, also called a rectangular distribution, is a probability distribution that has constant probability
- This distribution is defined by **two [parameters](https://www.statisticshowto.com/what-is-a-parameter-statisticshowto/)**, a and b:
    - a is the minimum
    - b is the maximum
    - The distribution is written as U(a, b)

# Probability Density Function

$$
f(x) = \begin{cases}
   \dfrac{1}{b-a} & a \le x \leq b \\
   0 &\text{else}
\end{cases}
$$

# Likelihood Function

- Suppose our data $x_1, . . . x_n$ are independently drawn from a uniform distribution $U (a, b)$. The density is defined as: $\dfrac{1}{a-b}$ on $[a,b]$ so our likelihood function is:

$$
f(x_1,....x_n|a,b) = \begin{cases}
   \Big(\dfrac{1}{b-a}\Big)^n & a \le x \leq b \\
   0 &\text{else}
\end{cases}
$$

# Numerical Characteristics

- **PDF:** $f(x|a,b) = \frac{1}{b-a}$
- **CDF:** $F(x|a,b) = \frac{x-a}{b-a}$
- **Mean:** $\frac{a+b}{2}$
- **Variance:** $\frac{(b-a)^2}{12}$
- **Support:** $[a, b]$
- **Parameters:** $a$ (lower bound), $b$ (upper bound)
- **Notation:** $X \sim U(a, b)$

# Resources

- [https://www.probabilitycourse.com/chapter4/4_2_1_uniform.php](https://www.probabilitycourse.com/chapter4/4_2_1_uniform.php)
- [https://mathworld.wolfram.com/UniformDistribution.html](https://mathworld.wolfram.com/UniformDistribution.html)
- [https://courses.lumenlearning.com/introstats1/chapter/the-uniform-distribution/](https://courses.lumenlearning.com/introstats1/chapter/the-uniform-distribution/)
- [https://www.statisticshowto.com/probability-and-statistics/statistics-definitions/uniform-distribution/](https://www.statisticshowto.com/probability-and-statistics/statistics-definitions/uniform-distribution/)