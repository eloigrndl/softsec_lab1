# BUG-FILTER-2
## Category
Arithmetic overflow/underflow

## Description
Since the `new_width` and `new_height` variables are stored in an `unsigned short` (which has a max value of 65,535), those variables will overflow if the factor is too big or if the provided image's size is too big.

## Affected Lines in the original program
`resize.c:33-34`

## Expected vs Observed
Using the provided command below, the program should output an image of size 70000x70000 but the values mentionned above overflowed and the resulting image has a size of 2464x2464. 

## Steps to Reproduce

### Command
```
./solid test.png 2000 2000 123456
./resize test.png very_big.png 34 
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Using an intermediate value, we check if the `new_height`and `new width` variables are greater than the largest possible value for `unsigned short` and if it is the case, we print an error (the same way as in `checkerboard.c`).