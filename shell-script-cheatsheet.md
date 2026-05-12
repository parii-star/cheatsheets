# Bash Shell Script Cheat Sheet

> **Goal:** Understand shell scripting concepts and syntax clearly enough to write and debug scripts, even as a beginner.

This cheat sheet focuses on Bash and POSIX shell scripting concepts, variables, loops, functions, input/output, and debugging. System administration and advanced Linux management commands are intentionally excluded to keep the sheet focused on scripting.

## How To Read This Sheet

| Pattern | Meaning |
|---|---|
| `[script]` | replace with a real script name, such as `myscript.sh` |
| `[variable]` | replace with a variable name, such as `name` |
| `[value]` | replace with an actual value, such as `"hello"` or `5` |
| `[condition]` | replace with a test expression, such as `[ -f file.txt ]` |
| `[command]` | replace with a real command or program name |

Example:

```bash
chmod +x [script]
```

If the script is named `deploy.sh`, run:

```bash
chmod +x deploy.sh
```

## Table Of Contents

| Section | What You Learn |
|---|---|
| [Script Basics](#script-basics) | shebang, running, and safety flags |
| [Variables](#variables) | create and manage variables |
| [Script Variables](#script-variables) | access arguments and status |
| [Input And Output](#input-and-output) | read from user and print output |
| [Redirection And Pipes](#redirection-and-pipes) | connect commands and save output |
| [Conditions](#conditions) | test and branch logic |
| [Loops](#loops) | repeat commands |
| [Functions](#functions) | create reusable code blocks |
| [String And Arithmetic](#string-and-arithmetic) | manipulate text and numbers |
| [Arrays](#arrays-bash) | work with lists in Bash |
| [Debugging](#debugging) | troubleshoot scripts |
| [Shell Reload](#shell-reload) | reload configuration files |
| [PowerShell](#powershell-windows) | shell commands outside Linux |
| [Command Prompt](#command-prompt-cmd) | Windows CMD commands |
| [Handy Shortcuts](#handy-shortcuts) | useful keyboard shortcuts |

## Script Basics

Writing and running scripts.

**Syntax:**

```bash
#!/usr/bin/env bash
command [options]
```

| Command | Clear Description |
|---|---|
| `#!/usr/bin/env bash` | portable Bash script shebang |
| `#!/bin/sh` | POSIX shell shebang |
| `bash script.sh` | run a script with Bash |
| `sh script.sh` | run a script with POSIX shell |
| `chmod +x script.sh` | make a script executable |
| `./script.sh` | run an executable script |
| `set -e` | exit when a command fails |
| `set -u` | fail on unset variables |
| `set -o pipefail` | fail pipeline if any command fails |
| `set -euo pipefail` | common strict mode for safety |

## Variables

Creating and using variables.

**Syntax:**

```bash
variable_name="value"
echo "$variable_name"
```

| Command | Clear Description |
|---|---|
| `name="Ada"` | create a variable with a string value |
| `echo "$name"` | print the value of a variable |
| `readonly name="Ada"` | make a variable read-only (cannot change) |
| `unset name` | remove a variable from memory |
| `export NAME="Ada"` | export variable so child processes can access it |
| `DATE=$(date)` | store command output in a variable |

## Script Variables

Special values available in scripts.

**Syntax:**

```bash
$0, $1, $#, $?, $$, "$@"
```

| Command | Clear Description |
|---|---|
| `$0` | script name or program name |
| `$1` | first argument passed to script |
| `$2` | second argument passed to script |
| `$#` | total number of arguments |
| `$?` | exit status of last command |
| `$$` | current shell process ID |
| `"$@"` | all arguments, safely quoted as separate words |

## Input And Output

Reading input and printing output.

**Syntax:**

```bash
read [options] variable
echo [options] string
```

| Command | Clear Description |
|---|---|
| `read -r name` | read one line from user into variable |
| `read -p "Name: " name` | read from user with a prompt message |
| `printf "%s\n" "$name"` | formatted output with specific format |
| `echo "Hello"` | simple output to console |

## Redirection And Pipes

Connecting command output and input.

**Syntax:**

```bash
command > file
command1 | command2
```

| Command | Clear Description |
|---|---|
| `cmd > file` | redirect stdout (output) to a file |
| `cmd >> file` | append stdout to end of file |
| `cmd < file` | read stdin (input) from a file |
| `cmd 2> err.log` | redirect stderr (errors) to a file |
| `cmd > out.log 2>&1` | combine stdout and stderr into one file |
| `cmd1 | cmd2` | pipe output from one command to another |
| `cmd | tee file` | show output and also save to file |

## Conditions

Branching logic.

**Syntax:**

```bash
if [ condition ]; then
    # code
fi
```

| Command | Clear Description |
|---|---|
| `if [ condition ]; then ... fi` | run block when condition is true |
| `if [[ cond1 && cond2 ]]; then ... fi` | Bash conditional with logical operators |
| `case "$var" in a) ... ;; b) ... ;; esac` | multi-branch matching on value |
| `[ -z "$value" ]` | test if string is empty (true if empty) |
| `[ -n "$value" ]` | test if string is not empty |
| `[ "$a" = "$b" ]` | test if two strings are equal |
| `[ "$a" -eq "$b" ]` | test if two numbers are equal |

## Loops

Repeating commands.

**Syntax:**

```bash
for item in list; do
    # code to repeat
done
```

| Command | Clear Description |
|---|---|
| `for x in a b c; do ... done` | iterate over words in a list |
| `for i in {1..5}; do ... done` | iterate over a numeric range |
| `while read -r line; do ... done < file` | loop over each line of a file |
| `until [ condition ]; do ... done` | run loop until condition becomes true |
| `break` | exit loop immediately |
| `continue` | skip to next iteration of loop |

## Functions

Reusable script blocks.

**Syntax:**

```bash
function_name() {
    # code
    return [status]
}
```

| Command | Clear Description |
|---|---|
| `my_func() { ... }` | define a function with statements |
| `my_func` | call a function to execute it |
| `local x="v"` | create a local variable inside function (Bash) |
| `return 1` | return a status code from function |

## String And Arithmetic

Common manipulations in scripts.

**Syntax:**

```bash
${variable}
$((arithmetic))
```

| Command | Clear Description |
|---|---|
| `len=${#name}` | get length of string variable |
| `echo "${name^^}"` | convert string to uppercase (Bash) |
| `echo "${name,,}"` | convert string to lowercase (Bash) |
| `sum=$((a + b))` | perform arithmetic calculation |
| `((count++))` | increment variable value |

## Arrays (Bash)

Working with lists.

**Syntax:**

```bash
arr=(item1 item2 item3)
${arr[index]}
```

| Command | Clear Description |
|---|---|
| `arr=(one two three)` | create array with three elements |
| `echo "${arr[0]}"` | access and print first array element |
| `echo "${arr[@]}"` | print all array elements |
| `echo "${#arr[@]}"` | get total number of elements |

## Debugging

Troubleshooting scripts.

**Syntax:**

```bash
bash -x script.sh
set -x
```

| Command | Clear Description |
|---|---|
| `bash -n script.sh` | check script syntax only, do not run |
| `bash -x script.sh` | run script and trace each step |
| `set -x` | enable trace mode inside running script |
| `set +x` | disable trace mode inside script |

## Shell Reload

Reloading shell configuration.

**Syntax:**

```bash
source ~/.bashrc
```

| Command | Clear Description |
|---|---|
| `source ~/.bashrc` | reload Bash configuration file |
| `. ~/.bashrc` | short form of source command |
| `source ~/.profile` | reload profile settings |

## PowerShell (Windows)

Shell commands outside Linux.

**Syntax:**

```powershell
Command-Name [parameter]
```

| Command | Clear Description |
|---|---|
| `Get-Location` | show current directory |
| `Get-ChildItem` | list files and folders |
| `Set-Location path` | change to a different directory |
| `New-Item file.txt -ItemType File` | create a new file |
| `Get-Content file.txt` | read and display file content |
| `Select-String -Path file.txt -Pattern "text"` | search for text in files |
| `Get-Process` | list all running processes |
| `Stop-Process -Id 1234` | stop a process by PID |
| `Get-Help Get-Process` | open help for a command |

## Command Prompt (CMD)

Shell commands outside Linux.

**Syntax:**

```cmd
COMMAND [options]
```

| Command | Clear Description |
|---|---|
| `cd` | show or change current directory |
| `dir` | list files and directories |
| `cls` | clear terminal screen |
| `copy source destination` | copy files to new location |
| `move source destination` | move or rename files |
| `del file.txt` | delete a file permanently |
| `type file.txt` | print file content to console |
| `findstr "text" file.txt` | search for text in files |
| `tasklist` | show all running processes |
| `taskkill /PID 1234 /F` | force stop process by ID |
| `help` | list available commands |

## Handy Shortcuts

Useful shell key bindings.

**Syntax:**

```bash
Keyboard shortcut
```

| Command | Clear Description |
|---|---|
| `Ctrl+C` | stop current command |
| `Ctrl+D` | close shell or end input |
| `Ctrl+L` | clear screen |
| `Ctrl+A` | move to start of line |
| `Ctrl+E` | move to end of line |
| `Ctrl+R` | search command history |
| `Tab` | autocomplete commands and paths |# Shell Script Cheat Sheet

> **Goal:** Learn the most common shell scripting syntax clearly enough to write simple scripts as a beginner.

This cheat sheet uses POSIX shell and Bash-style examples that work on most Linux systems.

## How To Read This Sheet

| Pattern | Meaning |
|---|---|
| `[file]` | replace with a real file name |
| `[value]` | replace with a value you want to use |
| `[command]` | replace with a command name |

## Table Of Contents

| Section | What You Learn |
|---|---|
| [Basics](#basics) | shebang, variables, and comments |
| [Conditionals](#conditionals) | if statements and tests |
| [Loops](#loops) | repeat work with for and while |
| [Functions](#functions) | organize reusable code |
| [Input And Output](#input-and-output) | read input and print text |
| [Exit Codes](#exit-codes) | handle success and failure |

## Basics

| Pattern | Clear Description |
|---|---|
| `#!/bin/bash` | Shebang line that tells the system which shell to use. |
| `name="value"` | Create a variable. |
| `echo "$name"` | Print a variable safely. |
| `# comment` | Add a comment. |

Example:

```bash
#!/bin/bash

name="world"
echo "Hello, $name"
```

## Conditionals

| Pattern | Clear Description |
|---|---|
| `if [ condition ]; then` | Start a conditional block. |
| `-f [file]` | Test whether a file exists and is a normal file. |
| `-d [path]` | Test whether a path is a directory. |
| `-z [value]` | Test whether a string is empty. |

Example:

```bash
if [ -f "notes.txt" ]; then
	echo "File exists"
else
	echo "File missing"
fi
```

## Loops

| Pattern | Clear Description |
|---|---|
| `for item in list; do` | Loop through a list of values. |
| `while [ condition ]; do` | Repeat while a condition stays true. |

Example:

```bash
for file in *.txt; do
	echo "$file"
done
```

## Functions

| Pattern | Clear Description |
|---|---|
| `name() { ... }` | Define a function. |
| `$1`, `$2`, `$@` | Access function or script arguments. |

Example:

```bash
greet() {
	echo "Hello, $1"
}

greet "Ada"
```

## Input And Output

| Pattern | Clear Description |
|---|---|
| `read [var]` | Read a line of input from the user. |
| `>` | Write output to a file. |
| `>>` | Append output to a file. |
| `2>/dev/null` | Hide error output. |

Example:

```bash
read name
echo "Hello, $name"
```

## Exit Codes

| Pattern | Clear Description |
|---|---|
| `exit 0` | Exit successfully. |
| `exit 1` | Exit with an error. |
| `$?` | Show the exit code of the last command. |

Example:

```bash
ls /tmp
echo "$?"
```

## Where DevOps Engineers Use This

Use shell scripts when you want quick glue between Linux commands in automation.

- Run setup steps in CI jobs and deployment pipelines.
- Automate backups, checks, and server maintenance tasks.
- Chain Linux tools together for small operational workflows.
