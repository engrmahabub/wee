## Statements

Wee has 28 keywords to create statements.

### Definition statements

Next statements are used to import modules or declare something.

| Keyword  | Purpose
|----------|--------------------------------------------------
| asm      | Import Assembly
| cpp      | Import C or C++ module
| wee      | Import Wee module
| def      | Define user data type or type alias using :
| con      | Define user constant (immutable variable) :
| let      | Declare mutable variables with type or value


### Execution statements

Next statements represents actions. Also called Imperative statements.

| Keyword  | Purpose
|----------|--------------------------------------------------
| set      | Establish or modify value for variables using =
| out      | Add something to console buffer but no new line 
| put      | Put some parameters to console and add new line
| write    | Output expression result to console 
| get      | Accept input from console and wait for read
| read     | Accept user input from console 
| exit     | Interrupt program execution with error number (0..n)
| end      | End of file. Must be followed by a "."

## Control statements

Also known as selectors or control statements.

| Keyword  | Purpose
|----------|--------------------------------------------------
| when     | Create a decision case using a logical expression
| check    | Multi-path value selector
| cycle    | Start point for repetitive block
| for      | Start _range iteration_ or _collection iteration_


## Semantic keywords

These keywords are associated with other statements to customize the statement behavior.

| Keyword  | Purpose
|----------|--------------------------------------------------
| if       | Conditional in statements and pattern matching
| else     | Alternative path executed in _when_ statement
| for      | Start _range iteration_ or _collection iteration_
| do       | Used with iteration _for_
| next     | Continue iteration _for_ from beginning
| done     | Terminate iteration _for_ and continue after for;
| repeat   | Jump to beginning of _cycle_ block
| stop     | stop inner cycle and continue after end of cycle.
| is       | Used in check to verify a single value and create a path
| in       | Used in check to verify if one value belong to specific tuple
| other    | Used in check to verify other cases not analyzed with is & in

**Read next:** [Syntax Overview](syntax.md)