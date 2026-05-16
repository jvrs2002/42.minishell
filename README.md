*This project has been created as part of the 42 curriculum by jvrs2002, vinimoura99.*

# minishell

<div align="center">

**minishell** is a core project in the **42 School** curriculum. The goal is to recreate a minimalist UNIX shell that simulates the behavior of Bash, focusing on parsing, execution, pipelines, redirections, built-in commands, environment variables, and signal handling.

> _"The objective of this project is to create a simple shell, reproducing the behavior of Bash as closely as possible, with a focus on understanding how a shell works internally."_

</div>

---

## Description

minishell is a simplified UNIX shell developed in C as part of the 42 curriculum. The project aims to deepen the understanding of how shells work internally by recreating core Bash behavior from scratch.

The shell supports:

- Interactive prompt handling.
- Parsing and tokenization of user input.
- Execution of binaries and built-in commands.
- Pipes and redirections.
- Environment variable expansion.
- Signal management.
- Heredocs.
- Exit status handling.

The project focuses heavily on process creation, file descriptor management, parsing logic, memory management, and UNIX system calls.

---

## Features

### Implemented Functionalities

- Prompt display in interactive mode.
- Command parsing with support for:
  - Single quotes (`'`).
  - Double quotes (`"`).
  - Environment variable expansion (`$VAR`).
- Execution of:
  - Simple commands.
  - Pipelines (`|`).
- Support for redirections:
  - Input (`<`).
  - Output (`>`).
  - Append (`>>`).
  - Heredoc (`<<`).
- Built-in commands.
- Environment variable management.
- Signal handling (`SIGINT`, `SIGQUIT`).
- Exit status handling (`$?`).
- Memory leak prevention and cleanup.

---

## Instructions

### Requirements

- UNIX-based operating system (Linux/macOS).
- GCC compiler or compatible.
- `make`.
- `readline` library.

Ubuntu/Debian:

```sh
sudo apt install libreadline-dev
```

### Compilation

Clone the repository and compile the project:

```sh
git clone https://github.com/jvrs2002/42.minishell
cd 42.minishell
make
```

Available Makefile rules:

```sh
make          # Compile the project
make clean    # Remove object files
make fclean   # Remove object files and executable
make re       # Recompile the project
```

### Execution

Run the shell:

```sh
./minishell
```

Example usage:

```sh
jvrs2002@minishell:~/42.minishell$  ls -la
jvrs2002@minishell:~/42.minishell$  echo hello world
jvrs2002@minishell:~/42.minishell$  cat file.txt | grep minishell
jvrs2002@minishell:~/42.minishell$  export MY_VAR=42
jvrs2002@minishell:~/42.minishell$  echo $MY_VAR
```

Exit the shell with:

```sh
exit
```

or by pressing `Ctrl+D`.

---

## Implemented Built-ins

| Built-in | Description |
|---|---|
| `echo` | Prints arguments to standard output. |
| `cd` | Changes the current working directory. |
| `pwd` | Displays the current working directory. |
| `export` | Creates or updates environment variables. |
| `unset` | Removes environment variables. |
| `env` | Displays environment variables. |
| `exit` | Exits the shell. |

---

## Parsing & Execution

### Lexer

The lexer scans user input and transforms it into tokens while handling:

- Quotes.
- Special characters.
- Pipes.
- Redirections.
- Environment variables.

### Parser

The parser organizes tokens into executable structures, validating syntax and preparing commands for execution.

### Executor

The executor:

- Executes built-ins internally.
- Executes external programs using `fork()` and `execve()`.
- Handles pipes and redirections.
- Manages file descriptors.
- Restores shell state after execution.

---

## Signals & Error Handling

- `SIGINT` (`Ctrl+C`) interrupts the current process.
- `SIGQUIT` (`Ctrl+\\`) is ignored in interactive mode.
- Heredoc interruption is handled safely.
- Syntax and execution errors are reported similarly to Bash whenever possible.
- Exit codes are preserved through `$?`.

---

## Resources

### Documentation & References

- GNU Bash Documentation:
  - https://www.gnu.org/software/bash/manual/bash.html

- Linux Man Pages:
  - https://man7.org/linux/man-pages/

- POSIX Shell Command Language:
  - https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html

- Readline Library Documentation:
  - https://tiswww.case.edu/php/chet/readline/rltop.html

- Beej's Guide to UNIX IPC:
  - https://beej.us/guide/bgipc/

### AI Usage

Artificial Intelligence tools were used during the development of this project for:

- Clarifying concepts related to UNIX processes and signals.
- Understanding parsing strategies and shell behavior.
- Reviewing edge cases and debugging ideas.
- Improving documentation and README structure.

---

## Authors

- GitHub: https://github.com/jvrs2002
- GitHub: https://github.com/vinimoura99
