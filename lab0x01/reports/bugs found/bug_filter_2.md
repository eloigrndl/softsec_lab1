# BUG-FILTER-2
## Category
Iteration error

## Description
When iterating through the image's pixel to apply the negative filter, the loops access `img->size_y` and `img->size_x` locations in the pixel array, resulting in a heap overflow, as those memory locations are out-of-bound of the allocated image.

## Affected Lines in the original program
`filter.c:118-119`

## Expected vs Observed
The program fails when we use the `negative` filter on a given image instead of applying the filter.

## Steps to Reproduce

### Command
```
./filter ./test_imgs/ck.png filter.png negative
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
In the faulty `for`loops iterating over the image's pixels, replace the `<=` operator by the `<`.