# BUG-EPFL-0
## Category
Logic error
## Description
In case of wrong arguments, the function does not return with an error code, causing a segmentation fault later on.

## Affected Lines in the original program
In `epfl.c:14-18`

## Expected vs Observed
If the program is launched with a wrong number of arguments, the program will print an error but instead of exiting with an error code, it will continue normally and fail afterwards.

## Steps to Reproduce

### Command

```
./epfl ./test_imgs/ck.png epfl.png 100 100 FF0000
```

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Add a `return` statement inside the concerned `if` lines.