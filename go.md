# <language> Command Line Debugging Cheatsheet

This guide assumes you are using [Delve](https://github.com/derekparker/delve) to debug your Go code

## Help

- List available commands from the debugger: `help` (abbr `h`)

## Start the debugger

- From the current directory's package: `$ dlv debug`
- From a specific package: `$ dlv debug <package>`

## Attach the debugger

```
$ dlv attach <pid>
```

## Breakpoints

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Set a breakpoint on the current line: `break +0` (abbr `b +0`)
- Set a breakpoint on *line_number* in the current file: `break <line_number>` (abbr `b <line_number>`)
- Set a breakpoint on *line_number* in *file_name*: `break <file_name>:<line_number>` (abbr `b <file_name>:<line_number>`)
- List all breakpoints: `breakpoints` (abbr `bp`)
- Remove a breakpoint: `clear <breakpoint_id>`
- Remove all breakpoints: `clearall`

## Control

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Continue until next breakpoint: `continue` (abbr `c`)
- Step to the next statement in the current function: `next` (abbr `n`)
- Step in to the next statement or into the next function: `step` (abbr `s`)
- Step out of the current function on the stack: `stepout`

## Analysis

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- List the current source and *line_count* before and after: `list` (abbr `l`)
- Run an expression in the current context: `print <expr>` (abbr `p <expr>`)
- Show the current stacktrace: `stack` (abbr `bt`) 
- List all local variables: `locals`
- Search all local variables: `locals <search_regex>`
- Show detailed information for a local var: `locals -v <search_regex>`
- Print local variable data: `print <local_variable_name>` (abbr `p <local_variable_name>`)

## Global control

- Stop debugging: `exit` (abbr `q`)
