### Introduction to Differentiating Functions Involving Random Variables

Before diving into differentiating functions of random variables, let's first review the basics of traditional differentiation and then gradually move to more advanced topics like stochastic calculus, where differentiating random variable functions comes into play.

### 1. **Traditional Differentiation** (Deterministic Case)

In classical calculus, we deal with deterministic functions, where each input has a corresponding definite output. Differentiation measures how a function changes as its input changes. Mathematically, if we have a function $f(x)$, its derivative $f'(x)$ represents the rate of change of $f(x)$ with respect to $x$.

For example:

- Let $f(x) = x^2$.
- The derivative is $f'(x) = 2x$, meaning that for small changes in $x$, the change in $f(x)$ is approximately $2x \times \Delta x$.

This is straightforward because $x$ is a deterministic variable (i.e., its value is known and fixed).

### 2. **What is a Random Variable?**

A random variable $X$ is a variable whose value is subject to randomness. Instead of having a single, definite value like a deterministic variable, a random variable takes on values according to some probability distribution.

For example:

- If $X$ represents the outcome of rolling a fair die, it can take values 1, 2, 3, 4, 5, or 6, each with a probability of $\frac{1}{6}$.

### 3. **Functions of Random Variables**

If we have a function $f(X)$, where $X$ is a random variable, we call this a **function of a random variable**. This is different from a function of a deterministic variable because the value of $f(X)$ depends on the random variable $X$, which could take on different values according to its probability distribution.

#### Example:
- Let $f(X) = X^2$, where $X$ is a random variable representing the roll of a die.
- $f(X)$ can take values $1^2, 2^2, 3^2, \dots$, depending on the outcome of $X$.

Now, differentiating this kind of function becomes more complicated because $X$ is not a deterministic variable.

### 4. **Differentiation of Functions Involving Random Variables**

In traditional differentiation, we work with fixed values for $x$, but in the case of random variables, the values are governed by a probability distribution. This leads us to **stochastic calculus**, where we differentiate functions of random variables. The key tool here is **Ito's Lemma**, which is used to find the derivative of functions involving stochastic processes (random variables that evolve over time).

#### Comparison with Traditional Differentiation:
- **Traditional differentiation** deals with deterministic variables. The changes in these variables are smooth and predictable.
- **Differentiation in stochastic calculus** deals with random variables whose changes are uncertain and can involve randomness. In this case, the function of a random variable can evolve according to stochastic processes (like Brownian motion), which requires different rules for differentiation.

### 5. **Stochastic Processes and Ito's Lemma**

A common stochastic process used in finance and physics is **Brownian motion** (denoted as $B(t)$), which is a random process where the future position depends on the current position and a random term.

- In traditional calculus, if we have a function $f(x)$, we use the chain rule to differentiate.
- In stochastic calculus, if we have a function $f(B(t))$, where $B(t)$ is Brownian motion, we use **Ito’s Lemma**.

#### Example: Applying Ito's Lemma
Let’s consider a simple example where $f(B(t)) = B(t)^2$, where $B(t)$ is Brownian motion.

Ito’s Lemma tells us that the derivative of $f(B(t))$ is given by:
$$
df(B(t)) = 2B(t) dB(t) + dt
$$
This result is different from traditional differentiation because of the additional term $dt$, which comes from the fact that $B(t)$ is a stochastic process with random changes.

#### Comparison of Derivatives:
- **Traditional differentiation**: If $f(x) = x^2$, we get $f'(x) = 2x$.
- **Stochastic differentiation** (Ito's Lemma): For $f(B(t)) = B(t)^2$, we get an additional $dt$ term:
  $$
  df(B(t)) = 2B(t) dB(t) + dt
  $$
  This extra term arises because the randomness of $B(t)$ introduces additional variability that needs to be accounted for.

### 6. **Intuition Behind the Difference**

- In traditional calculus, changes are smooth, and we assume the function’s behavior is predictable. For example, if you increase $x$ by a small amount, the change in $f(x)$ is proportional to this increase.
- In stochastic calculus, the changes in the random variable $X$ are unpredictable, so the function $f(X)$ must account for not only the deterministic changes but also the random fluctuations. This is why Ito’s Lemma includes extra terms related to the randomness of $X$.

### 7. **Practical Applications**

This differentiation method is crucial in fields like finance, where prices of stocks and options evolve randomly over time. For example, in the famous **Black-Scholes model** for option pricing, the stock price follows a stochastic process, and Ito's Lemma is used to derive the formula for the price of options.

### Summary of Differences:

| **Traditional Differentiation** | **Differentiation of Random Variable Functions (Stochastic)** |
|----------------------------------|--------------------------------------------------------------|
| Variables are deterministic.     | Variables are random, following a probability distribution.   |
| Smooth and predictable changes.  | Changes involve randomness, leading to unpredictable outcomes.|
| Chain rule is used.              | Ito’s Lemma is used for stochastic processes.                |
| Example: $f(x) = x^2$, $f'(x) = 2x$ | Example: $f(B(t)) = B(t)^2$, $df(B(t)) = 2B(t) dB(t) + dt$ |

### Conclusion

Differentiating functions involving random variables requires stochastic calculus, which accounts for the randomness inherent in such variables. The key difference from traditional differentiation is the additional randomness term that appears due to the uncertain nature of random variables, which is captured by tools like Ito’s Lemma.
