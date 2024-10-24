# Minishell - Building Your Own Shell

## Project Overview

**Minishell** is a project focused on developing a basic UNIX shell. This shell mimics some of the essential features of the widely used Bash shell. Through this project, I gained deep insights into process creation, signal handling, file descriptors, and command parsing. The project involved creating a functional shell capable of executing commands, managing environment variables, handling redirections, and implementing pipelines. Additionally, it explores how to handle interactive user inputs and manage built-in shell commands.

---

## Key Features

- **Program Name**: `minishell`
- **Core Features**:
  - **Prompt**: Displays a prompt while waiting for the user to input commands.
  - **Command Execution**: Executes commands by searching for the executable based on the `PATH` variable or a relative/absolute path.
  - **Redirections**:
    - `<`: Redirect input from a file.
    - `>`: Redirect output to a file.
    - `<<`: Here-document, accepts input until a specified delimiter is reached.
    - `>>`: Append output to a file.
  - **Pipelines**: Implements pipelines (`|`), where the output of one command is fed as input to the next command.
  - **Environment Variables**: Handles `$` expansion for environment variables, as well as `$?` for the exit status of the last executed command.
  - **Built-in Commands**:
    - `echo` (with `-n` option)
    - `cd` (with relative or absolute paths)
    - `pwd`
    - `export`
    - `unset`
    - `env`
    - `exit`
  - **Signal Handling**: Correctly handles signals like `ctrl-C`, `ctrl-D`, and `ctrl-\` to match Bash behavior in interactive mode.
    - `ctrl-C`: Display a new prompt on a new line.
    - `ctrl-D`: Exit the shell.
    - `ctrl-\`: Does nothing.
  - **History**: Keeps track of commands entered by the user using `readline`'s history mechanism.

---

## Technical Details

- **Process Management**:
  - Executes commands by forking child processes and managing their execution using system calls like `fork`, `execve`, and `wait`.
  - Handles pipes (`pipe` system call) to pass data between commands in a pipeline.
  
- **Redirection Handling**:
  - Manages file descriptors to redirect input/output for commands.
  - Supports both input and output redirections, including appending to files.

- **Environment Variables**:
  - Manages environment variables and allows the user to modify them with `export` and `unset`.
  - Expands environment variables within commands.

- **Signal Handling**:
  - Implements custom signal handlers to manage the shell's response to `ctrl-C`, `ctrl-D`, and `ctrl-\`.

- **Built-in Commands**:
  - `echo`: Prints text to the terminal, with support for the `-n` flag to suppress the newline.
  - `cd`: Changes the current working directory.
  - `pwd`: Prints the current working directory.
  - `export`: Adds or modifies environment variables.
  - `unset`: Removes environment variables.
  - `env`: Prints the environment variables.
  - `exit`: Exits the shell with an optional exit code.

---

## Skills Demonstrated

- **Process Creation**: Gained deep understanding of how to create and manage child processes in a UNIX-like environment using `fork`, `execve`, and `wait`.
- **Signal Handling**: Implemented signal handlers to manage terminal behavior and cleanly handle interrupts such as `ctrl-C` and `ctrl-D`.
- **File Descriptors and Redirection**: Managed file descriptors to implement input/output redirection and pipelines.
- **Command Parsing**: Built a robust parser to tokenize and process user commands, handle quoting, and manage complex shell features like redirection and pipelines.
- **Memory Management**: Ensured proper allocation and freeing of memory to prevent leaks, especially in cases of environment variables and dynamic user input.

---

## Conclusion

The **Minishell** project provided an immersive experience in systems programming by creating a simplified shell that mimics Bash behavior. This project helped me gain proficiency in process management, file descriptor handling, and command parsing. The challenges of implementing a functional shell, complete with built-in commands and signal handling, made this an invaluable learning experience in understanding how a shell operates at its core.
