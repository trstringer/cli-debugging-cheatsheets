# Perl Command Line Debugging Cheatsheet

## Help

- List available commands from the debugger: `h`
- Longer list of available commands with more information: `h h`
- Get help on particular command: `h <command>`

## Start the debugger

- Debug and break immediately: `$ perl -d <filename>`
- Break on a code line: insert `$DB::single = 1` directly in the code

## Attach the debugger

Perl debugger does not support attaching to a running process.

## Breakpoints

- Set **static/code breakpoints**: insert `$DB::single = 1` before the line you
want to break on
- Set **static/code conditional breakpoints**: insert `$DB::single = 1 if <condition>` before
the line you want to break on

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Set a breakpoint on the current line: `b`
- Set a breakpoint on the first line of *subroutine_name* in the current file: `b <sub_name>`
- Set a breakpoint on *line_number* in the current file: `b <line_number>`
- Set a breakpoint on *line_number* in *file_name*: `f <file_name>` `b <line_number>`
- Remove a breakpoint: `B <line_number>`
- Add an action (expression) to run on current line: `a <expr>`
- Add an action to run on *line_number*: `a <line_number> <expr>`
- Remove an action on *line_number*: `A <line_number>`
- List all breakpoints: `L b`
- List all actions: `L a`
- Remove all breakpoints: `B *`
- Remove all actions: `A *`

## Control

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- Continue until next breakpoint: `c`
- Continue until *line_number* or *subroutine_name*: `c <line_number|sub_name>`
- Step to the next statement in the current function: `n`
- Step in to the next statement or into the next function: `s`
- Repeat the last Step to/Step in command: `<CR>` (Enter key)
- Step out of the current function on the stack: `r`

## Analysis

> :bulb: The following commands pertain to the debugger when a breakpoint is met or code is paused

- List the source around current line: `l` (Repeat to list forward)
- View the source around *line_number*: `v <line_number>` (Repeat to view forward)
- List the current source and *line_count* after: `l +<line_count>`
- List the first 10 lines of *subroutine_name*: `l <sub_name>` (`l` to keep going)
- Return to the current source line: `.`
- Run an expression in list context, dump the result: `x <expr>`
- Run an expression and display the result with `print` built-in: `p <expr>`
- Watch an expression: `w <expr>`
- Stop watching an expression: `W <expr>`
- Display all watched expressions: `L w`
- Display lexical variables (matching *pattern*) in current scope: `y [~pattern]`
- Display current call stack trace: `T`
- Toggle trace mode (to *N* levels deep): `t [N]`

## Global control

- Terminate the program and exit the debugger: `q` or `Ctrl-D`
- Restart the program: `R`
