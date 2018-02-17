# C Command Line Debugging Cheatsheet

## Help

- List available command classes from the debugger: `help`
- List available commands in a class from the debugger: `help <class_name>`
- List all available commands from the debugger: `help all`

## Start the debugger

- Compile your source with the gcc `-g` option: `$ gcc -g -o <bin_name> <source>`
- Run the debugger: `$ gdb <bin_name>`

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

- Set a breakpoint on the current line: `b`
- Set a breakpoint on *line_number* in the current file: `b <line_number>`
- Set a breakpoint on *line_number* in *file_name*: `b <file_name>:<line_number>`
- Set a breakpoint on a *function*: `b <function_name>`
- Set a breakpoint on a *function* in a *file_name*: `b <file_name>:<function_name>`
- Remove a breakpoint: `delete <breakpoint_number>`
- List all breakpoints: `info b`

## Control

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Continue until next breakpoint: `c`
- Step to the next statement in the current function: `n`
- Step in to the next statement or into the next function: `s`
- Step out of the current function on the stack: `f`

## Analysis

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- List the current source: `l `
- Run an expression in the current context: `p <expr>`
- Watch an expression: `watch <expr>`

## Global control

- Terminate the program: `kill`
- Terminate the program and exit the debugger: `q`
