# C Command Line Debugging Cheatsheet

## Help

- List available command classes from the debugger: `help`
- List available commands in a class from the debugger: `help <class_name>`
- List all available commands from the debugger: `help all`

## Start the debugger

- Compile your source with the gcc `-g` option: `$ gcc -g -o <bin_name> <source>`
- Run the debugger: `$ gdb <bin_name>`
- Start the program in the debugger until the first breakpoint or completion: `run` (abbr `r`)
- Start the program in the debugger until the main procedure: `start`

## Attach the debugger

```
$ gdb -p <pid>
```

`pid` can be found by running `ps -aux | grep <bin_search>`

## Breakpoints

- Set **static/code breakpoints**:

```c
#include <signal.h>
/* ... code ... */
raise(SIGINT);
```

In gdb when this breakpoint is hit, the top of the stack is the libc shared object file. Go up a frame in the stack from gdb by running `up`

- Set **static/code conditional breakpoints**: same as above, but with a conditional statement surrounding the `raise()` call

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Set a breakpoint on the current line: `break` (abbr `b`)
- Set a breakpoint on *line_number* in the current file: `break <line_number>` (abbr `b <line_number>`)
- Set a breakpoint on *line_number* in *file_name*: `break <file_name>:<line_number>` (abbr `b <file_name>:<line_number>`)
- Set a breakpoint on a *function*: `break <function_name>` (abbr `b <function_name>`)
- Set a breakpoint on a *function* in a *file_name*: `break <file_name>:<function_name>` (abbr `b <file_name>:<function_name>`)
- Remove a breakpoint: `delete <breakpoint_number>`
- List all breakpoints: `info break` (abbr `info b`)

## Control

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Continue until next breakpoint: `continue` (abbr `c`)
- Step to the next statement in the current function: `next` (abbr `n`)
- Step in to the next statement or into the next function: `step` (abbr `s`)
- Step out of the current function on the stack: `finish` (abbr `f`)
- Continue to given location: `advance`

## Analysis

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- List the current source: `list` (abbr `l`)
- Run an expression in the current context: `print <expr>` (abbr `p <expr>`)
- Watch an expression: `watch <expr>`
- List the current stacktrace: `backtrace` (abbr `bt`)
- Go up one frame in the stack (the one that ran the current frame): `up`
- Go down one frame in the stack (the one called by the current frame): `down`

## Global control

- Terminate the program: `kill`
- Terminate the program and exit the debugger: `quit` (abbr `q`)
