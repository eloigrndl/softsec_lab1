# BUG-CHECKERBOARD-1
## Category
Heap overflow

## Description
For square sizes which are either greater than the image size or which does not divide the image size perfectly (the image size not being a multiple of the square size), the program fails.

## Affected Lines in the original program
From `checkerboard.c:115` to `checkboard.c:122`

## Expected vs Observed
If we give such a square sizes (explained above), the `for` loops that fills the image data will access memory address that are out of the bounds of the image data array : there is no bound check for the array indices, thus making the program crash. 
If we give a square size bigger than the image size, we expect the image to be of only one color and if we give a square size that does not divide perfectly the image size, we expect the squares to be cut on the bottom and right edges of the image (since we fill the image for upper left to lower right corners). This is not the case.

## Steps to Reproduce

### Command

`./checkerboard test.png 100 100 150 000000 FFFFFF`

`./checkerboard test.png 100 100 30 000000 FFFFFF`

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Before accessing addresses in the image data array, add a `min` operation on the array indices : if the indices are higher than the image size, upper-bound them.