# BUG-RECT-1
## Category
Iteration error

## Description
When iterating over the input image to draw the rectangle, the program wrongly loops over the image pixels as it increments both `i` and `j` simultaneously. This results in the program iterating diagonally rather than over the entire image.


## Affected Lines in the original program
`rect.c:80-81`

## Expected vs Observed
A rectangle should be drawn on the given image but instead we only see a diagonal of the wanted rectangle.

## Steps to Reproduce
To generate this bug, the argument parsing bug (`bug_rect_0`) should be fixed, otherwise the program will always fail to read the provided arguments.

### Command
```
./rect ./test_imgs/ck.png test_rec.png 10 10 50 50 000000
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
We should increment `i` outside `j`'s `while` loop and when increasing `i`, `j`should be reset to 0.