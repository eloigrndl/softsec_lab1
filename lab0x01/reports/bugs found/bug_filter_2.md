# BUG-FILTER-2
## Category
Local persisting pointers

## Description
When using the `get_pixel` function, the `pixel` variable is allocated on the stack. Thus, when the function returns, the variable gets deallocated and the returned pointer becomes invalid.

## Affected Lines in the original program
`filter.c:108`

## Expected vs Observed
When using the negative filter, the program fails with a segmentation fault.

## Steps to Reproduce

### Command
```
./filter ./test_imgs/summer.png filter.png negative
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
The `pixel` variable should be allocate on the heap : when the function will return, the pointer will still be valid.