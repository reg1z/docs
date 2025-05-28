---
tags:
  - terminology
  - ML
  - math/linear-algebra
date: 2025-05-28
---
# Sum of the Squared Residuals

More commonly known as the **Residual Sum of Squares** or **RSS**...

The **Sum of Squared Residuals** is the total, across every data point in a dataset, of the squared difference between the ground-truth target value (the actual observed outcome from your training labels) and the model’s predicted output for that input.

## Formula

$$
\mathrm{SSR} = \sum_{i=1}^{n} \bigl(y_i - \hat{y}_i\bigr)^2
$$
