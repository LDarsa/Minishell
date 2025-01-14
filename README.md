# Minishell

Minishell is a simple UNIX shell implemented as part of the 42 School’s 24 project. The goal of the project is to mimic the behavior of a basic shell, handling command execution, input parsing, process management, and signal handling. 

## Features

- **Input Parsing:** User input is parsed into a linked list, where the commands and arguments are rearranged according to operator precedence (i.e., pipes and redirections have higher priority).
- **Heap Tree Construction:** The linked list is then transformed into a heap tree, with a special focus on managing pipes (`|`) and redirections (`>`, `<`, `>>`).
- **Process Execution:** Each command is executed in a separate process. When necessary, pipes are used for inter-process communication, allowing commands to be chained together.
- **Signal Handling:** Proper handling of signals such as `SIGINT` (Ctrl+C) to ensure that the shell behaves correctly when interrupted by the user.
- **Exit Codes:** Exit codes of executed processes are properly managed and returned, allowing the shell to track the success or failure of commands.

## How It Works

1. **Input Parsing:** When a command is entered, the shell parses the input and creates a linked list representing the command and its arguments. Operators (such as pipes and redirection) are given higher precedence in the linked list structure.
   
2. **Heap Tree Construction:** After parsing, the linked list is rearranged into a heap tree. The tree structure prioritizes commands with pipes or redirection operators, ensuring that these are executed in the correct order.

3. **Process Management:** A new process is created for each command. If the command includes a pipe or redirection operator, the necessary system calls are made to handle inter-process communication using pipes or redirecting input/output streams.

4. **Exit Code Management:** The shell takes into consideration the exit status of each command and returns appropriate exit codes to the user.

5. **Signal Handling:** The shell ensures that signals like `SIGINT` are properly caught and handled, preventing abrupt termination of the shell or the child processes.

## Installation

To use this shell, clone the repository and compile the project:

```bash
git clone https://github.com/LDarsa/Minishell.git
cd Minishell
make
