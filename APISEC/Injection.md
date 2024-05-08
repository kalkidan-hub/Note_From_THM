Fuzzing is all about requesting the unexpected. When reviewing API documentation, if the API is expecting a certain type of input (number, string, boolean value) send:

- A very large number
- A very large string
- A negative number
- A string (instead of a number or boolean value)
- Random characters
- Boolean values
- Meta characters

`SQL Metacharacters` are characters that SQL treats as functions rather than data. For example, -- is a metacharacter that tells the SQL interpreter to ignore the following input because it is a comment