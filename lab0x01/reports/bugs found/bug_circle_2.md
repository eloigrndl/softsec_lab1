# BUG-CIRCLE_2
## Category
Wrong operators/variables

## Description
The `x`and `y` indices are not completely computed : the operator `==` is used instead of `=`, resulting into a comparison instead of a variable assignement. Thus, the same operation is made on the data array two times with the same parameters.

## Affected Lines in the original program
`circle.c:61` and `circle.c:84`

## Expected vs Observed
The circle is not completely drawn: the top-left corner is missing.

## Steps to Reproduce

### Command
```
./circle test.png circle.png 100 100 20 000000
```

### Proof-of-Concept Input (if needed)


## Suggested Fix Description
Replace the `==` operator by `=` on the said lines.
