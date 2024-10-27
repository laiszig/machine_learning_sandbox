## Linear Regression

### Main Ideas
1. Use least-squares to fit a line to the data
2. Calculate $R^2$
3. Calculate a p-value for $R^2$

First, we draw a line through the data. Second, measure the distance from the line to the data,
square each distance, and then add them up.

- **`Residual:`** Distance from a line to a data point.

Third, rotate the line a little bit. measure the residuals, square them, and then sum up the squares.
We rotate and sum up the square residuals.
After some rotations, we can plot the sum of squared residuals and corresponding rotation.
Finally, we find the rotation that has the least sum of squares.

The equation for the line with least-squares estimates 2 parameters: a y-axis intercept and a slope.
If the slope is not 0, it means that knowing the y will help us make a guess about the x.

Calculating $R^2$ is the first step in determining how good the guess will be.

1. First we calculate the average of y values only.
2. Sum the squared residuals (distance from the mean to the data point).
**`SS(mean):`** Sum of squares around the mean.

$SS(mean) = (data - mean)^2$
Variation around the mean = $\frac{(data - mean)^2}{n}$
