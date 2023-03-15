# BUG-EPFL-3
## Category
Logic error
## Description
When the provided `top_left_x` or `top_left_y` arguments are negative, the program fails with a segmentation fault. It tries to access incorrect memory locations that lead to a heap overflow. This error is caused by the fact that there are no check for the provided arguments, allowing the user to run the program with negative coordinates.

This differs from the wanted behavior of the program stated in the comments of the file which is to convert those values to 0.

## Affected Lines in the original program
In `epfl.c:25-26`

## Expected vs Observed
For negative arguments, the program fails with a segmentation fault. Instead, the program should decode those values as 0.

## Steps to Reproduce

### Command

```
./epfl ./test_imgs/ck_edge.png epfl.png 15 -10 3 FF0000
```

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Check the correctness of the provided `top_left_x` or `top_left_y` and if one of them is negative, set it to 0.