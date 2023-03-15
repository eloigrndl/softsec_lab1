# BUG-SOLID-0
## Category
Memory leak

## Description

In normal behavior, there is a memory leak as the `palette` variable is never freed. 

## Affected Lines in the original program
In `solid.c:16`

## Expected vs Observed
The program should not leak memory but `palette`is never freed. Result were obtained using `valgrind`.


## Steps to Reproduce

### Command

```
./solid test.png 400 400 FFFFFF
```

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Instead of allocating the `palette` variable on the heap, we should allocate it on the stack since it is only used locally. This prevents the memory leak and avoids using external function (`allocate_palette()`) to create the variable.