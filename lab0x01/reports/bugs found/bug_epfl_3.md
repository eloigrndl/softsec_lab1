# BUG-EPFL-3
## Category
Logic error
## Description
When the logo is shifted upward (because it would be cut on the bottom otherwise), the program draws the ETHZ logo instead of the EPFL logo. When the program shifts the logo, it also adds adjustements to the logo, transformating it into the ETHZ logo.

## Affected Lines in the original program
In `epfl.c:82`

## Expected vs Observed
The program draws the ETHZ logo instead of the EPFL logo when it shifts the logo upward.

## Steps to Reproduce

### Command

`./epfl ./test_imgs/ck_edge.png epfl.png 15 60 1 FF0000`

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Delete the faulty line that add the adjustements to the initial logo.