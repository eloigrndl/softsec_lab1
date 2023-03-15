# BUG-FILTER-4
## Category
Stack buffer overflow/underflow

## Description
When running the program with filter arguments, if those arguments are longer than `ARG_SIZE`, the program will fail with a buffer overflow. This failure is due to the usage of the `strcpy` method that copy the filter argument value `argv[4]` into the `char` array `arg` which has a fixed length of `ARG_SIZE` (255 elements). When copying a larger value into this array, since `strcpy` doesn't check the length of the given parameters, it will generate a buffer overflow error.

## Affected Lines in the original program
`filter.c:228`

## Expected vs Observed
The command below will generate a buffer overflow and make the program crash instead of safely copying the argument.

## Steps to Reproduce

### Command
```
./filter ./test_imgs/ck.png filter.png blur 1111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
We should use the `strncopy` method (which is done for the other arguments) in order to safely copy the argument into the new variable.