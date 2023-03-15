# BUG-SOLID-1
## Category
Command injection

## Description
The user's input is not validated when the program uses the `stat` system command to output the size of the final image, allowing an arbitrary command to be run.

## Affected Lines in the original program
`solid.c:122` to `solid.c:125`

## Expected vs Observed
The program should only run the `stat`system function, but the user is allow to run any command using command concatenation.
The following example uses the `touch` command to create a file. 

## Steps to Reproduce

### Command

```
./solid "test.png; touch infected_file.txt" 350 50 AEF178
```

### Proof-of-Concept Input (if needed)

## Suggested Fix Description
Instead of using the system command, we can use the `stat`method from the `sys` package which will return stats (and size among others) of a file for a given filename.