# BUG-0
## Category
Memory leak

## Description

In normal behavior, there is a memory leak as the `palette` variable is never freed. 

## Affected Lines in the original program
In `solid.c:16`

## Expected vs Observed
The program should not leak memory but `palette`is never freed. Result were obtained using `valgrind`.


## Steps to Reproduce

### Command

`./solid test.png 400 400 FFFFFF`

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Free the variable at the same time than the `img` and `img->pxl` variables. This also requires to change error handlers to free the palettte if the image or pixels allocation have failed.