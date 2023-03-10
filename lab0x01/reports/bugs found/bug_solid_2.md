# BUG-0
## Category
Unchecked return code from system call

## Description

The return value of the `allocate_palette` is never check.

## Affected Lines in the original program
In `solid.c:16`

## Expected vs Observed
The program should always check if memory allocation have succeeded and inform the user if it is not the case. This is not done with the 


## Steps to Reproduce

### Command

Can't be reproduce

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Add an `if` statement that returns an error if the memory allocation failed.