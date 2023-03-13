# BUG-EPFL-2
## Category
Logic error
## Description
When using a size greater than 1, the logo isn't fully drawn. This is caused by the `if` statement that check if the current image column is a column where the logo should be drawn : there is an error in the boolean condition which only takes into account the `logo_width` instead of the projected size of the logo which is `size * logo_width`.

## Affected Lines in the original program
In `epfl.c:77`

## Expected vs Observed
When using a logo size greater than 1 as argument, the program only draws part of it instead of drawing a complete EPFL logo.

## Steps to Reproduce

### Command

`./epfl test.png epfl.png 100 100 10 FF0000`

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
In the faulty line, replace the second part of the condition `j < top_left_x + logo_width` by `j < top_left_x + logo_width * size`.