# BUG-CIRCLE-1
## Category
Type error

## Description
When calling the `strtol` method, instead of providing a `char **`, the program provides a `char *` variable.  

## Affected Lines in the original program
`circle.c:30`

## Expected vs Observed
The program should draw a circle on the provided image but instead, we get a segmentation fault error.

## Steps to Reproduce

### Command
```
./circle test.png test_circle.png 100 100 30 FFFFFFF
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
We must add the `&` operation to the `end_ptr` so that we gives the correct type of variable : `char **`.
