# BUG-15
## Category
Heap overflow/underflow

## Description
The program wrongly allocates memory for the pixels of the new image : the memory size isn't calculated correctly, causing a heap overflow.

## Affected Lines in the original program
`resize.c:48`

## Expected vs Observed
The program should resize the given image but it fails indicating a segmentation fault because of an heap overflow.

## Steps to Reproduce

### Command
```
./resize ./test_imgs/desert.png resize.png 3
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
We must allocate `n_pixels` pixels. Therefore, we should replace `n_pixels + sizeof(struct pixel)` by `n_pixels * sizeof(struct pixel)` with the `*` operator.