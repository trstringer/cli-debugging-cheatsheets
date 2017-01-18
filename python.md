# Python Command Line Debugging Cheatsheet

## Help

- List available commands from the debugger: `h`

## Start the debugger

- Debug and break immediately: `$ python3 -m pdb <filename>`
- Break on a code line: insert `import pdb; pdb.set_trace()` directly in the code

## Attach the debugger

The standard library module `pdb` currently does not support attaching and debugging a running program

## Breakpoints

- Set **static/code breakpoints**: insert `import pdb; pdb.set_trace()` directly in the code
- Set **static/code conditional breakpoints**: insert `if <condition>: pdb.set_trace()` directly in the code

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Set a breakpoint on *line_number* in the current file: `b <line_number>`
- Set a breakpoint on *line_number* in *file_name*: `b <file_name>:<line_number>`
- Remove a breakpoint: `cl <bp_number>` (`bp_number` can be retrieved from `b`)
- List all breakpoints: `b`

## Control

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Continue until next breakpoint: `c`
- Step to the next statement in the current function: `n`
- Step in to the next statement or into the next function: `s`
- Step out of the current function on the stack: `r`

## Analysis

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- List the current source: `l .`
- Run an expression in the current context: `p <expr>`
- Watch an expression: `display <expr>`
- Stop watching an expression: `undisplay <expr>`
- Display all watched expressions: `display`

## Global control

- Terminate the program and exit the debugger: `q`
- Restart the program: `restart`
