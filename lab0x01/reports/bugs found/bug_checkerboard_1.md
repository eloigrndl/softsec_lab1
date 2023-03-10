# BUG-CHECKERBOARD-1
## Category
Temporal safety violation

## Description
In case of a failure, the `img` variable is freed two times.

## Affected Lines in the original program
In `checkerboard.c:91`

## Expected vs Observed
If the program fails to allocate the memory for the pixel array, the `img` variable is freed before executing the `error_img` routine which frees the variable a second time. Result were obtained using `valgrind`.

## Steps to Reproduce

To trigger the double-free bug, one can invert the boolean condition at `checkerboard.c:90` and then run a correct command.

### Command

`./checkerboard test.png 100 100 50 000000 FFFFFF`

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Remove the first `free` operation at line `checkerboard.c:91`.