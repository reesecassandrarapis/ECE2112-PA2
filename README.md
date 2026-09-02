# EXPERIMENT 2: NUMERICAL PYTHON (NUMPY)
Name: Reese Cassandra T. Rapis <br> Section: 2ECE-C

This repository contains my **Programming Assignment 2** for **ECE 2112: Advanced Computer Programming and Algorithms**. The activity focuses on using NumPy for three problems: **Reproducible Normalization**, **Cubes Divisible by 4**, and **Above-Mean Squares**.

## I. OBJECTIVES
- To create and reshape NumPy arrays using NumPy functions.
- To perform vectorized numerical operations on an ndarray.
- To compute array statistics and use Boolean conditions to select elements.
- To save computed NumPy arrays as .npy files.

## II. REPRODUCIBLE NORMALIZATION PROBLEM
**Goal:** Create a reproducible 5x5 random integer array named `X`, then normalize the whole array using the z-score formula so the result has a mean of 0 and a standard deviation of 1.

**How it works:**
```python
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))

X_mean = np.mean(X)
X_std = np.std(X)

X_normalized = (X - X_mean) / X_std
```
- `np.random.seed(2112)` fixes the starting point of NumPy's random number generator, so every time the cell runs, the np.random.randint creates the exact same numbers instead of a different random set each run.
- `np.random.randint(10, 101, size=(5, 5))` generates integers from 10 up to but not including 101, and arranges them directly into a 5x5 array.
- `X_mean` and `X.std` compute the mean and the standard deviation across all elements of the array at once.
- `(X - X_mean) / X_std` subtracts the mean from every element and divides every element by the standard deviation in a single vectorized step.

**Checking Values:** 
``` python
Mean of X_normalized: 0.0
Std of X_normalized: 0.9999999999999999
```
- Since every element was shifted by the same mean and same standard deviation, the transformed array will mathematically have an average of 0 and spread out with a standard deviation of 1 (0.99...).

## III. CUBES DIVISIBLE BY 4 PROBLEM
**Goal:** Build a 10x10 array of the cubes of the first 100 positive integers, then select only the cubes divisible by 4 using a Boolean condition.

**How it works:** 
``` python
C = np.arange(1, 101) ** 3

C = C.reshape(10, 10)

div_by_4 = C[C % 4 == 0]
```
- `np.arange(1, 101)` generates the integers 1 through 100 as a single 1D array, then apply `** 3` to the whole array, which cubes every element.
- `.reshape(10, 10)` rearranges the 100 cubed values into a 10x10 grid, so C starts with 1³ and ends with 100³.
- `[C % 4 == 0]` compares every element of C against the divisibility condition, and `C[C % 4 == 0]` immediately uses it to pull out only the elements where it's True, those divisible by 4, making the result into a 1D array.

**Checking Values:** 
``` python
Shape of C: (10, 10)
Number of selected elements: 50
First selected value: 8
Last selected value: 1,000,000
```
- Out of the 100 cubes, half turn out to be divisible by 4, which is why div_by_4 ends up with 50 elements. 2³ = 8 is the smallest cube, and 100³ = 1,000,000 is the largest, that satisfies the condition.

## IV. ABOVE-MEAN SQUARES PROBLEM
**Goal:** Build a 6x6 array of the squares of the first 36 positive integers, then compute the mean of the array, and select only the elements greater than that mean.

**How it works:** 
``` python
S = np.arange(1, 37) ** 2

S = S.reshape(6, 6)

S_mean = S.mean()

above_mean = S[S > S_mean]
```
- `np.arange(1, 37) ** 2` generates the integers 1 through 36 and squares each one of them, creating a 1D array of 36 squared values.
- `.reshape(6, 6)` arranges those 36 values into a 6x6 grid, so S starts with 1² and ends with 36².
- `S.mean()` computes the average value of all 36 elements of the array.
- `S > S_mean` compares every element of S to the mean value, and `S[S > S_mean]` uses that to pull out only the elements where it's True, making the result into a 1D array.

**Checking Values:** 
``` python
S_mean: 450.1666666666667
Number of selected elements: 15
First selected value: 484
Last selected value: 1296
```
- Only the largest 15 of the 36 elements, which range from 22² = 484 to 36² = 1296, exceed the mean.

We save the selected array using the code: `np.save("file name", ndarray)`
- `np.save("X_normalized.npy", X_normalized)`
- `np.save("div_by_4.npy", div_by_4)`
- `np.save("above_mean.npy", above_mean)`

Thank you for reading.
