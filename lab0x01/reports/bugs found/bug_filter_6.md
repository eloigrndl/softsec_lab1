# BUG-FILTER-6
## Category
Logic error

## Description
In order to apply a blur effect on a given image, the program averages the color of the new pixel by computing the direct sum of adjacent pixel, using the formula `(2 * radius + 1) * (2 * radius + 1)`. This calculation is wrong as the file's comments state that "Pixels of the square which fall outside the image do not count towards the average". Hence, the above formula is false when computing the sum for pixels on the edge. This leads to a logic error regarding the computation of this filter.

## Affected Lines in the original program
`filter.c:228`

## Expected vs Observed
The program wrongly computes the average of adjacent pixels assuming there is always a complete circle of pixels around any given pixel of the image which is not the case for pixels on the edges.

## Steps to Reproduce

### Command
```
./filter ./test_imgs/summer.png blurred.png blur 3
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
We should manually count the number of pixels that have been used to compute the average : this can be done by incrementing the `num_pixels` variable directly inside the `for` loop for pixels that satisfy the condition.