# BUG-0
## Category
Unchecked return code from system call
## Description

In normal behavior, there is a memory leak as the `palette`varaible is never freed. 

## Affected Lines in the original program
In `solid.c:16`

## Expected vs Observed
The program should not leak memory but `palette`is never freed. Result were obtained using `valgrind`.


## Steps to Reproduce

### Command

`./solid test.png 400 400 FFFFFF`

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Either free the palette value at the end of the program or allocate the variable locally. This last solution is a better solution as we avoid using the `allocate_palette`method and do not need to free the variable.