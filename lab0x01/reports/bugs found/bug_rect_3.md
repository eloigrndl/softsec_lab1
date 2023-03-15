# BUG-RECT-3
## Category
Type error

## Description
For the rectangle's coordinates, the program convert the user's input (from a `string` to a `unsigned`) using the `atoi` function that returns an `int`. Therefore, there is a implicit conversion between the function's return value (an `int`) and the variable (`unsigned`). This can lead to buggy coordinates.

## Affected Lines in the original program
`rect.c:23-27`

## Expected vs Observed
When entering negative coordinates, the program should convert them to 0 : if a user enters negative values for `top_left_x` and `top_left_y`, the rectangle should be drawn from the top left corner of the provided image. Instead, the coordinates are wrongly converted and (using the following input), the rectangle starts from `x = 40` and `y = 40`.

## Steps to Reproduce
As for `bug_rect_1` and `bug_rect_2`, to generate this bug, the argument parsing bug (`bug_rect_0`) should be fixed, otherwise the program will always fail to read the provided arguments.

If `bug_rect_1` is not fixed, it will only produce a diagonal line instead of a rectangle but still in the wrong coordinates.

### Command
```
./rect ./test_imgs/ck.png rect.png -4294967256 -4294967256 50 50 FFFFFF
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
We should use the `strtoul` function that convert a `string` to an `unsigned long int`. Then, the same way as in `checkerboard.c`, we can check the correctness of the converted coordinates and reset them if necessary.
