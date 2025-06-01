---
tags:
  - terminology
  - ML
  - math/calculus
date: 2025-05-27
---
# Gradient Descent
*The steepest descent is the fastest path...*

⭐ When you have two or more derivatives of the *same* function, they are called a **Gradient**. The calculated **Gradient** is used to **descend** to the lowest point in the **Loss Function**.

Notes taken while watching Josh Starmer's video *Gradient Descent, Step-by-Step*: [https://www.youtube.com/watch?v=sDv4f4s2SB8](https://www.youtube.com/watch?v=sDv4f4s2SB8)

> [!info]+ General Steps
> 1. Take the derivative of the **Loss Function** for *each parameter* in it. In ML lingo, this translates to: "take the **Gradient** of the **Loss Function**."
> 	- The derivatives of all parameters within the loss function are collectively referred to as the **Gradient**.
> 2. Pick random values for the parameters.
> 3. Plug the parameter values into the **Gradient** (i.e. plug them into *each* derivative that makes up the Gradient).
> 4. Calculate the step sizes.
> 5. Calculate the new parameters for the next "step."

- Linear Regression → Optimizing the intercept and slope
- Logistic Regression → Optimizing a squiggle
- t-SNE → Optimizing clusters
- ...

Gradient descent can optimize all of these, and more.

Takes big steps when far away from the optimal value and small steps when close.

Uses derivatives to find the minimum value by taking steps from an initial guess until reaching the optimal value.

Very useful when it's not possible to solve for where the derivative = 0.

The size of your next step should be informed by the resultant slope of each derivative.

 Step Size = Slope x **Learning Rate**

In practice, a reasonable **Learning Rate** can be determined automatically by starting large and getting smaller with each step.

NewIntercept = OldIntercept - Step Size

In practice, the **Minimum Step Size** = 0.001 or smaller

Gradient Descent also includes a limit on the number of steps it will take before stopping.

In practice, the **Maximum Number of Steps** = 1000 or greater

> [!info]+ Machine Learning - What are Loss Functions?
> *"A loss function in machine learning is a mathematical measure of how well a model’s predictions match the true targets. During training, the **optimizer** adjusts model parameters to minimize this loss."*
> 
> The [Sum of the Squared Residuals](Sum%20of%20the%20Squared%20Residuals.md) is a type of **Loss Function**.

**Stochastic Gradient Descient** → Uses a randomly selected subset of data at every step, rather than the full dataset. This is often used with **big data**, reducing the time spent calculating Gradients of the Loss Function.