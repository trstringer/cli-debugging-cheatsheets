# Bash Script Debugging Cheatsheet

:warning: If you are finding that you would like deeper debugging with a bash script, consider using another platform (like Python) to do what your shell script is intending :warning:

## Expanding commands

This is the biggest help when trying to figure out what or why a bash script is doing what it is doing. This trick will allow you to see all command expansions and dump them to stdout (effectively taking any guesswork out)

### In a script

Add `set -x` before you want to start expanding all commands

(optionally) add `set +x` to not expand commands that follow

### From the terminal

Run your script with `-x`: `$ bash -x <script>`

## Stop script on a non-zero exit code

If you want to stop executing your script when a command returns a non-zero exit code, this is an effective way to see what is failing

### In a script

Add `set -e` when you want this behavior to take effect

### From the terminal

Run your script with `-e`: `$ bash -e <script>`
