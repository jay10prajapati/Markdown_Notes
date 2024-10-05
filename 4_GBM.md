### Introduction to Geometric Brownian Motion (GBM) and Ito's Geometric Random Walk

**Ito’s Geometric Random Walk** or **Geometric Brownian Motion (GBM)** is a widely used model to describe the stochastic (random) behavior of a variable, particularly in finance for modeling stock prices. Unlike a regular Brownian motion, where the changes are purely random, GBM assumes that the changes in a variable are proportional to the current value of the variable. This model captures the real-world phenomenon that stock prices grow over time but with a random component (volatility).

### 1. **Basic Brownian Motion (Recap)**

Before we dive into geometric Brownian motion, let’s recall basic **Brownian motion** $B(t)$. Brownian motion is a mathematical model for random movement, often used to describe the unpredictable motion of particles in a fluid, or the fluctuations of stock prices.

- **Key properties of Brownian motion $B(t)$**:
  1. $B(0) = 0$ (it starts at zero).
  2. Changes over small intervals are random and normally distributed.
  3. The paths are continuous but non-differentiable (i.e., rough and unpredictable).

However, **regular Brownian motion** doesn’t capture the real-world behavior of stock prices because stock prices:
- Tend to grow over time (i.e., they don’t oscillate randomly around zero).
- Changes are proportional to the current price, not independent of it.

### 2. **Geometric Brownian Motion (GBM)**

In **Geometric Brownian Motion (GBM)**, we model a stochastic process where the changes in the variable (like a stock price) are proportional to the value of the variable. This means that larger values of the variable result in larger random fluctuations.

The GBM equation for a variable $S(t)$ (e.g., a stock price at time $t$) is:

$$
dS(t) = \mu S(t) dt + \sigma S(t) dB(t)
$$

Where:
- $S(t)$: The value of the process at time $t$ (e.g., the stock price).
- $\mu$: The drift rate (the expected return or growth rate over time).
- $\sigma$: The volatility (how much randomness or fluctuation occurs in the process).
- $dB(t)$: An infinitesimal increment of Brownian motion (representing the random component).

#### Intuition Behind the Equation:

- The **deterministic part** $\mu S(t) dt$: This represents the steady or predictable growth (e.g., if the stock price increases by a certain percentage over time).
- The **stochastic part** $\sigma S(t) dB(t)$: This represents the random fluctuations (the volatility in stock price due to market conditions). The size of these fluctuations depends on the current value of $S(t)$, meaning larger stock prices tend to fluctuate more.

### 3. **From the GBM Equation to a Geometric Random Walk**

Now, let’s apply **Ito’s Lemma** to understand how this stochastic process evolves over time and derive the final equation for the price at any time $t$.

#### Step-by-Step Application of Ito’s Lemma:

1. **Start with the GBM equation** for $S(t)$:
 
 $$
 dS(t) = \mu S(t) dt + \sigma S(t) dB(t)
 $$

2. **Let’s model the logarithm of the stock price**: $X(t) = \ln(S(t))$. We use the logarithm because it simplifies the math and helps capture the fact that prices change multiplicatively (percentage changes) rather than additively.

3. **Apply Ito’s Lemma** to the function $f(S(t)) = \ln(S(t))$. From Ito’s Lemma, we know:

$$
df(X(t)) = \frac{\partial f}{\partial t} dt + \frac{\partial f}{\partial S} dS + \frac{1}{2} \frac{\partial^2 f}{\partial S^2} (dS)^2
$$

   Let’s compute the partial derivatives for $f(S(t)) = \ln(S(t))$:
   - $\frac{\partial f}{\partial S} = \frac{1}{S}$
   - $\frac{\partial^2 f}{\partial S^2} = -\frac{1}{S^2}$

   Substituting these into Ito’s Lemma:

$$
d\ln(S(t)) = \frac{1}{S(t)} \cdot \left( \mu S(t) dt + \sigma S(t) dB(t) \right) + \frac{1}{2} \cdot -\frac{1}{S(t)^2} \cdot \sigma^2 S(t)^2 dt
$$

   Simplifying this:

$$
d\ln(S(t)) = \mu dt + \sigma dB(t) - \frac{1}{2} \sigma^2 dt
$$

5. **Integrating both sides** over the time interval from 0 to $t$ gives us the solution:

$$
\ln(S(t)) = \ln(S(0)) + \left( \mu - \frac{1}{2} \sigma^2 \right) t + \sigma B(t)
$$

   This means that the logarithm of the stock price grows linearly over time with both a deterministic part $\left( \mu - \frac{1}{2} \sigma^2 \right) t$ and a random part $\sigma B(t)$.

6. **Exponentiating both sides** to solve for $S(t)$, we get the final equation:

$$
S(t) = S(0) \exp\left( \left( \mu - \frac{1}{2} \sigma^2 \right) t + \sigma B(t) \right)
$$

#### The Final Simplified Equation for GBM:

$$
S(t) = S(0) \exp\left( \left( \mu - \frac{1}{2} \sigma^2 \right) t + \sigma B(t) \right)
$$

### 4. **Real-Life Example: Stock Prices**

Let’s apply this to a real-life example, such as modeling the price of a stock.

- **Initial stock price** $S(0) = 100$: Suppose a stock starts at $100.
- **Drift $\mu = 5\%$**: The stock is expected to grow by 5% per year on average.
- **Volatility $\sigma = 20\%$**: The stock has a volatility of 20%, meaning its price fluctuates significantly.

Using the GBM model, the stock price $S(t)$ at time $t$ (say, in 1 year) can be written as:

$$
S(1) = 100 \exp\left( (0.05 - \frac{1}{2} \cdot 0.2^2) \cdot 1 + 0.2 \cdot B(1) \right)
$$

Simplifying:

$$
S(1) = 100 \exp\left( (0.05 - 0.02) + 0.2 B(1) \right) = 100 \exp\left( 0.03 + 0.2 B(1) \right)
$$

Now, because $B(1)$ is random (normally distributed with mean 0 and variance 1), the stock price in one year is uncertain, but we know the expected drift (growth) and the volatility.

### 5. **Understanding the Terms**:

1. **Deterministic part**: $\left( \mu - \frac{1}{2} \sigma^2 \right) t$ is the expected growth adjusted for volatility. The subtraction of $\frac{1}{2} \sigma^2$ corrects for the fact that volatility has a dampening effect on the overall growth.
   - If $\mu = 0.05$ and $\sigma = 0.20$, the stock doesn’t just grow at 5%—volatility reduces the effective growth slightly, to around 3%.
   
2. **Stochastic part**: $\sigma B(t)$ represents the random fluctuation around the expected path due to the market’s uncertainty.

### 6. **Why Use Geometric Brownian Motion?**

- **Stock prices are never negative**: In real life, stock prices can’t become negative. GBM ensures that prices stay positive, because the exponential function always produces a positive value.
- **Proportional changes**: GBM models price changes as proportional to the current price, which aligns with the idea that larger prices fluctuate more.
- **Captures randomness**: The random part $\sigma B(t)$ captures market volatility and uncertainty, which is crucial for real-world models.

### 7. **Comparison with Traditional Random Walks**

- **Traditional random walk**: In a simple random walk, the changes are additive and not proportional to the current value. For example, if you start at $10 and flip a coin to move up or down by $1, the price changes are fixed increments.
  - This doesn’t match the behavior of stock prices, where percentage changes are

 more relevant than absolute changes.
  
- **Geometric random walk (GBM)**: The changes are multiplicative (proportional to the current value), meaning larger values fluctuate more, which better matches real-world behavior.

### Summary: Key Takeaways

- **Ito’s Geometric Random Walk** or **Geometric Brownian Motion (GBM)** models processes where changes are proportional to the current value, such as stock prices.
- The GBM equation is: 

$$
S(t) = S(0) \exp\left( \left( \mu - \frac{1}{2} \sigma^2 \right) t + \sigma B(t) \right)
$$

- **Real-life example**: GBM is used extensively in finance to model stock prices, capturing both expected growth (drift) and market volatility (randomness).
- GBM ensures prices remain positive and models the realistic proportional fluctuations in stock prices.

