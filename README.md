

# Monte Carlo Pi Estimation
This is a beginner Monte Carlo Pi Estimation.
This repository contains a Python script that uses the Monte Carlo method to estimate the value of Pi. The Monte Carlo method is a statistical technique that allows for solving mathematical problems using random sampling.

## Description

The script generates random points within a unit square and checks how many of them fall inside a quarter circle. By using the ratio of points inside the circle to the total number of points, it estimates the value of Pi. The script also plots the points and the quarter circle to visualize the process.

## Installation

To run this script, you'll need Python 3 installed on your system along with the following Python libraries:

- numpy
- matplotlib

You can install the required libraries using pip:

```bash
pip install numpy matplotlib

Usage
To use the script, simply run it using Python. You can adjust the number of points to generate by changing the n_points variable.

import numpy as np
import matplotlib.pyplot as plt
from numpy.random import uniform

# Number of points
n_points = 1000  # Change this value for a different number of points

# Generate random points
x = uniform(size=n_points)
y = uniform(size=n_points)

# Check if points are inside the unit circle
inside_circle = x**2 + y**2 < 1 

# Estimate Pi
pi_estimate = 4 * np.sum(inside_circle) / n_points
accuracy = abs((pi_estimate - np.pi) / np.pi) * 100

print(f"Pi estimation with MC using {n_points} points, pi: {pi_estimate}")
print(f"Accuracy of Pi: {accuracy}%")

# Plot the data
theta = np.linspace(0, np.pi/2, 1000)
x_theta = np.cos(theta)
y_theta = np.sin(theta)

plt.figure(figsize=(8,8))

# Plot points inside the circle
plt.scatter(x[inside_circle], y[inside_circle], color='blue', label='Inside Circle')

# Plot the quarter circle
plt.plot(x_theta, y_theta, color='green', label='Circle')

# Plot points outside the circle
plt.scatter(x[~inside_circle], y[~inside_circle], color='red', label='Outside Circle')

plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.title('Monte Carlo Pi Estimation')
plt.legend()
plt.show()


#Example Output
When you run the script, it will print the estimated value of Pi and its accuracy. It will also display a plot showing the points inside and outside the quarter circle.

Pi estimation with MC using 1000 points, pi: 3.148
Accuracy of Pi: 0.2188760615880527%

#Contributing
If you have suggestions for improving this script, please feel free to submit a pull request or open an issue.
