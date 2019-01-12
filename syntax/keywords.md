## Statements

Wee has 28 keywords to create statements.

| Keyword  | Purpose
|----------|--------------------------------------------------
| asm      | Import Assembly
| cpp      | Import C or C++ module
| wee      | Import Wee module
| def      | Define user data type or type alias using :
| let      | Declare variables using : with type or =
| set      | Establish or modify value for variables using =
| out      | Add something to console buffer but no new line 
| put      | Put some parameters to console and add new line
| write    | Output expression result to console 
| get      | Accept input from console and wait for read
| read     | Accept user input from console 
| if       | Conditional statement execution 
| for      | Start _range iteration_ or _collection iteration_
| do       | Used with iteration _for_
| next     | Continue iteration _for_ from beginning
| done     | Terminate iteration _for_ and continue after for;
| cycle    | Start point for repetitive block
| repeat   | Jump to beginning of _cycle_ block
| stop     | stop inner cycle and continue after end of cycle.
| check    | Multi-path value selector
| is       | Used in check to verify a single value and create a path
| in       | Used in check to verify if one value belong to specific tuple
| other    | Used in check to verify other cases not analyzed with is & in
| when     | Create a decision case using a logical expression
| else     | Alternative path executed when no case is true
| exit     | Interrupt program execution with error number (0..n)
| end      | End of file. Must be followed by a "."

**Read next:** [Syntax Overview](syntax/syntax.md)