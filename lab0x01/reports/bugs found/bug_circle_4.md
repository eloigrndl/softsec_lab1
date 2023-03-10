# BUG-CIRCLE-4
## Category
Iteration error

## Description
When drawing the circle, there is no image bound check : for some particular arguments, the program will try to access either negative indices or indices that are beyond the array's limits, resulting in a heap overflow.

## Affected Lines in the original program
`circle.c:52` and `circle.c:75`

## Expected vs Observed
On every parameter, the program should only draw the part of the circle that is within the image : it should not try to write out of the image's bounds, even if the center has negative coordinates or if the circle goes beyond the edges of the image.

## Steps to Reproduce

### Command
```
./circle test.png circle.png -3 10 100 FFFFFF
```

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
When drawing the circle, before accessing addresses in the image data array, we should check if the pixel is inside of the image by looking at its coordinates and draw it only if it is the case.
