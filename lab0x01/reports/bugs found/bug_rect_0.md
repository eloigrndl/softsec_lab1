# BUG-RECT-0
## Category
Wrong operators/variables

## Description
The program crashes for any given input as it does not parse correctly the provided arguments because of an index error.

## Affected Lines in the original program
`rect.c:34-35`

## Expected vs Observed
When parsing the arguments, the program tries to access the `argv[8]` value. Because we only have 8 elements in the `argv` variable, this results in a out-of-bounds error, causing a segmentation fault.

## Steps to Reproduce

### Command
```
./rect test.png test_rec.png 10 10 100 60 000000
```

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
The index should be changed to 7 in the faulty lines.