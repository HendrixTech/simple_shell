
# PROJECT TITLE: simple_shell

A Unix shell is a command-line interpreter or shell that provides a command line user interface for Unix-like operating systems. The shell is both an interactive command language and a scripting language, and is used by the operating system to control the execution of the system using shell scripts.

Generally, a shell is a program that executes other programs in response to text commands. A sophisticated shell can also change the environment in which other programs execute by passing named variables, a parameter list, or an input source.

Shells read configuration files in various circumstances. These files usually contain commands for the shell and are executed when loaded; they are usually used to set important variables used to find executables, like $PATH, and others that control the behavior and appearance of the shell. The table in this section shows the configuration files for popular shells.


# Table of Contents

- Description
- File Structure
- File Structure
- Requirements
- Installation
- Usage
- Example of Use
- Bugs
- Authors
- License


## File Structure

* [main.h](main.h) - program header file

* [.simple_shell_history](.simple_shell_history) - File where history's historial must be saved

* [builtins.c](builtins.c) - major builtin functions
	* `check_for_builtins` - checks if the command is a builtin
	* `new_exit` - exits the shell with the option of a specified status
	* `_env` - prints the current shell's environment variables to the standard output
	* `new_setenv` -  create a new environment variable, or edit an existing variable
	* `new_unsetenv` - removes an environment variable

* [builtins2.c](builtins2.c) - more builtin functions
	* `_new_cd` - Changes the current working directory .

* [enviroment](enviroment) - more builtin functions
	* `make_enviroment` - make the shell environment from the environment.
	* `free_env` - free the shell's environment

* [history.c](history.c) - history builting and funcions related.
	* `add_nodeint` - Add node in the beginning
	* `free_listint` - free pointers related with malloc
	* `new_history` - Print the list of a single list
	* `_puts3` - writes a string to standard output
	* `print_message` - print a string to standart output

* [add_functions.c](add_functions.c) - helpers functions for fork_child function
	* `_strcmp` - compares two strings
	* `error_printing` - Prints a message error when a comand is not found.
	* `exec_error` - Prints exec errors.

* [helper_functions.c](helper_functions.c) - Functions to manage error messages     	and utils
	* `_puts_error` - print a string to sdandart error
	* `prints_error_msg` - prints error messages to standard error
	* `integer_converter` - converts an unsigned int to a string
	* `atoi` - converts a string into an integer

* [setenv_functions.c](setenv_functions.c) - helper functions for setenv builting
	* `add_value` - create a new environment variable string
	* `find_key` - finds an environment variable
	* `add_key` - create a new environment variable

* [memory_allocation.c](memory_allocation.c) - memory allocation functions
	* `_realloc` - a custom realloc function for arrays of pointers

* [new_strtok.c](new_strtok.c) - custom strtok and helper functions
	* `check_match` - checks if a character matches any in a string
	* `new_strtok` - a custom strtok for the shell
	* `build_path` - Combines two strings one representing the path directory and another representing the command file.

* [fork_child.c](fork_child.c) - functions related to executing commands
	* `fork_child` - Creates a child in  order to execute another program.
	* `path_finder` - Acts as an interface for functions that will be able
	*  to find the full path of a program.
	* `find_env_index` - Finds the index of an environmental variable.
	* `tokenize_path` - Separates a string of path as an array of
	*  strings containing the path directories.
	* `search_directories` - Looks through directories stored in path_tokens
	*  for a specific file aka command.

* [simple_shell.c](simple_shell.c) - essential functions to the shell
	* `main` - the main function of the program
	* `sig_handler` - handles SIGINT

* [strfunctions.c](strfunctions.c) - functions related to string manipulation
	* `_puts` - writes a string to standart output
	* `_strdup` - duplicates a string
	* `_strcmpr` - compares two strings
	* `_strcat` - concatenates two strings with a `/` in the middle
	* `_strlen` - calculates the length of a string

* [tokenizer.c](tokenizer.c) - tokenizing function
	* `tokenizer` - creates an array of tokens from a buffer with a specified delimiter
	* `tokenize` -tokenizes a buffer with a delimiter just use for for_child
	* `token_interface` - token interface
	* `count_token` - token's count

* [new_help.c](new_help.c) - Help builting and functions
	* `new_help` - help builtin command
	* `new_help_help` -  help builtin command help
	* `new_help_exit` - help builtin command exit
	* `new_help_cd` - help builtin command cd
	* `new_help_env` -  help builtin command env

* [more_help_functions.c](more_help_functions.c) - More help functions
	* `new_help_history` - help builtin command history
	* `new_help_unalias` - help builtin command unalias
	* `new_help_unset` - help builtin command unset
	* `new_help_unsetenv` -  help builtin command unsetenv
	* `new_help_setenv` -  help builtin command setenv

* [more_help_functions2.c](more_help_functions2.c) -  More help functions
	* `new_help_alias` - help builtin command alias
	* `new_help_else` - Error message if not command found

* [print_functions.c](print_functions.c) -  More utils
	* `print_str` - Prints a string character by character.
	* `_write_char` - Writes a character to stdout
	* `print_number` - Prints an unsigned number

* [man_1_simple_shell](man_1_simple_shell) -  Shell Man page


## Directories

* [helpfiles](helpfiles) - arguments files for help building.
* [Mishell](Mishell) - testing shell apart.
* [shell2](shell2) - backup to test shell, outdated version.



## Requirements

simple_shell is designed to run in the `Ubuntu 14.04 LTS` linux environment and to be compiled using the GNU compiler collection v. `gcc 4.8.4` with flags`-Wall, -Werror, -Wextra, and -pedantic.`

## Installation

 - Clone this repository: `https://github.com/yoyogold-a11/shelltestenviroment.git`.
	 - Change directories into the repository: `cd simple_shell`
	 - Compile: `gcc -Wall -Werror -Wextra -pedantic *.c -o hsh`
	 - Run the shell in interactive mode: `./hsh`
	 - Or run the shell in non-interactive mode: example `echo "pwd" | ./hsh`
## Usage

The simple_shell is designed to execute commands in a similar manner to sh, however with more limited functionality. The development of this shell is ongoing. The below features will be checked as they become available (see man page for complete information on usage):


### Features

- [x] uses the PATH
- [x] implements builtins
- [x] handles command line arguments
- [x] custom strtok function
- [x] uses exit status
- [x] shell continues upon Crtl+C (**^C**)
- [x] handles comments (#)
- [x] handles **;**
- [ ] custom getline type function
- [ ] handles **&&** and **||**
- [ ] aliases
- [ ] variable replacement


### Builtins

- [x] exit
- [x] env
- [x] setenv
- [x] unsetenv
- [x] cd
- [x] help
- [x] history


## Example of usage

$ ls
add_functions.c           helpfiles            more_help_functions2.c  shell2
builtings.c               main.h          more_help_functions.c   strfunctions.c
enviroment.c              hsh                  new_help.c              tokenizer.c
env_unsetenv_functions.c  main.c               new_strtok.c
fork_child.c              memory_allocation.c  print_functions.c
helper_functions.c        Mishell              README.md
$ help 2
./hsh: 5: help: no help topics match: `2'.  Try `help help' or `man -k 2' or `info 2'.
$ help cd
cd: cd
	Change the shell working directory.

	Change the current directory to DIR.  The default DIR is the value of the
	HOME shell variable.

	The variable CDPATH defines the search path for the directory containing
	DIR.  Alternative directory names in CDPATH are separated by a colo
n (:).
	A null directory name is the same as the current directory.  If DIR begins
	with a slash (/), then CDPATH is not used.

	Exit Status:
	Returns 0 if the directory is changed, and if $PWD is set successfully when
	-P is used; non-zero otherwise.
$ pwd
/home/shell_test/shelltestenviroment
$


## Bugs

At this time, there are no known bugs.


## Authors

- Ebrudu Hendrix Obukome | [GitHub](https://www.github.com/HendrixTech)
- Grace Bamidele | [GitHub](http:/www.github.com/Gracy222)


## License

simple_shell is open source and therefore free to download and use without permission.

