# BUG-FILTER-4
## Category
String vulnerability

## Description
When the program fails to load the input image, it directly prints the input path given by the user, allowing format string attacks to access illegal portions of the memory.


## Affected Lines in the original program
`filter.c:233`

## Expected vs Observed
The command below will make the program fail and allow an attacker to read parts of the heap memory.

## Steps to Reproduce

### Command
```
./filter "Input is accessing data : %s%p%u%d" filter.png negative
```
### Proof-of-Concept Input (if needed)

## Suggested Fix Description
We should use formatted string to enforce the type : replace the print statement with `print("%s", input)`.