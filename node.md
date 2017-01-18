# Node.js Command Line Debugging Cheatsheet

## Help

- List available commands from the debugger: `help`

## Start the debugger

```
$ node debug <entry_file>
```

## Attach the debugger

- Get the pid of the node process: `$ ps aux | grep "search"`
- Attach the debugger: `$ node debug -p <pid>`

> :bulb: Attaching the debugger or starting the process with the debugger attached automatically breaks on entry

## Breakpoints

> :bulb: In order to hit any breakpoints you need to start the process with the `debug` option (`node debug <entry_file>`)

- Set **static/code breakpoints**: insert `debugger;` directly in the code
- Set **static/code conditional breakpoints**: insert `if (<condition>) debugger;` directly in the code

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Set a breakpoint on the current line: `sb()`
- Set a breakpoint on *line_number* in the current file: `sb(<line_number>)`
- Set a breakpoint on *line_number* in *file_name*: `sb(<file_name>, <line_number>)`
- Remove a breakpoint: `cb(<file_name>, <line_number>)`
- List all breakpoints: `breakpoints`

## Control

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Continue until next breakpoint: `c`
- Step to the next statement in the current function: `n`
- Step in to the next statement or into the next function: `s`
- Step out of the current function on the stack: `o`

## Analysis

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- List the current source and *line_count* before and after: `list(<line_count>)` (defaults to 5)
- Run an expression in the current context: `exec <expr>`
- Watch an expression: `watch('<expr>')` (watched expressions display at every breakpoint or when running `watchers`)
- Stop watching an expression: `watch('<expr>')`
- Display all watched expressions: `watchers`

## Global control

- Terminate the program: `kill`
- Terminate the program and exit the debugger: `quit`
- Restart the program: `restart`
