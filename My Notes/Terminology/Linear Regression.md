---
tags:
  - terminology
  - math
  - ML
date: 2025-05-27
---
# Linear Regression
Fitting a line to data. "Finding the rotation of a line plotted through data points that has the lowest possible sum of its squared **Residuals**"

Consists of:

1. Using **least-squares** to fit a line to the data
2. Calculating R^2
3. Calculating a ***p-value*** for R^2

Related terms

- **Residual** → the distance from a data point on a graph to the line drawn
- **SS(mean)** → "sum of squares around the mean" = (data - mean)^2
- R^2 = (Var(mean) - Var(fit)) / Var(mean)
	1. Measure, square, and sum the distance from the data to the mean
	2. Measure, square, and sum the distance from the data to the complicated equation
		- Remember: the "complicated equation" is the **equation for your fitted line**!
	3. Plug in your calculations