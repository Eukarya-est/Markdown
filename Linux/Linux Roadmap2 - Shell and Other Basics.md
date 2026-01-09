Linux Roadmap 2

# Shell and Other Basics

[toc]

## 1. Intro

The Linux shell is a command-line interface or terminal used to interact directly with the operating system. The shell helps facilitate system commands and acts as an intermediary interface between the user and the system’s kernel. The shell can perform complex tasks efficiently and quickly. There are many types of shells available in Linux, including the Bourne Shell (sh), the C Shell (csh), and the Bourne-Again Shell (bash).

The basics of using a Linux shell include navigating between directories, creating, renaming and deleting files and directories, and executing system commands. This introductory level knowledge is crucial for Linux system administration, scripting, and automation.

## 2. Command Path

In Linux, the command path is an important concept under shell basics.

```shell
echo $PATH
```

Running this command in a Linux terminal will return all the directories that the shell will search, in order, to find the command it has to run. The directories are separated by a colon.

## 3. Environment Variables

In Linux, environment variables are dynamic named values that can affect the behavior of running processes in a shell. They exist in every shell session. A shell session’s environment includes, but is not limited to, the user’s home directory, command search path, terminal type, and program preferences.

Environment variables help to contribute to the fantastic and customizable flexibility you see in Unix systems. They provide a simple way to share configuration settings between multiple applications and processes in Linux.

You can use the ‘env’ command to list all the environment variables in a shell session. If you want to print a particular variable, such as the PATH variable, you can use the ‘echo $PATH’ command.

- List all environment variables

```shell
env
```

- Print a particular variable like PATH

```shell
echo $PATH
```

Every shell, such as Bourne shell, C shell, or Korn shell in Unix or Linux has different syntax and semantics to define and use environment variables.

## 3. Command Help

Command help in Linux is an essential feature that enables users to navigate through Linux shell commands with ease. This feature displays brief information on how to use these commands. 

```shell
man [COMMAND]
```

For built-in shell functions, use:

```shell
help [COMMAND]
```

## 4. Redirect

The shell in Linux provides a robust way of managing input and output streams of a command or program, this mechanism is known as Redirection. Linux being a multi-user and multi-tasking operating system, every process typically has 3 streams opened: 

- Standard Input (stdin) 
  - This is where the process reads its input from. The default is the keyboard.
- Standard Output (stdout)
  - The process writes its output to stdout. By default, this means the terminal.
- Standard Error (stderr) 
  - The process writes error messages to stderr. This also goes to the terminal by default.

Redirection in Linux allows us to manipulate these streams, advancing the flexibility with which commands or programs are run. Besides the default devices (keyboard for input and terminal for output), the I/O streams can be redirected to files or other devices.

For example, if you want to store the output of a command into a file instead of printing it to the console, we can use the ’>’ operator.

```shell
ls -al > testfile.txt
```

This command will write the output of ‘ls -al’ into ‘file_list.txt’, whether or not the file initially existed. It will be created if necessary, and if it already exists – it will be overwritten.

## 5. Super user

The Super User, also known as “root user”, represents a user account in Linux with extensive powers, privileges, and capabilities. This user has complete control over the system and can access any data stored on it. This includes the ability to modify system configurations, change other user’s passwords, install software, and perform more administrative tasks in the shell environment.

The super user can be accessed through the **'sudo'** or **'su'** commands.

Specifically, '**su**' switches the current user to the root, whereas '**sudo**' allows you to run a command as another user, default being root. However, they also have a key difference which is sudo will log the commands and its arguments which can be a handy audit trail.

- This would prompt for root password and switch you to root usermode

```shell
su -
```

- To perform a command as superuser (if allowed in sudoers list)

```shell
sudo [COMMAND]
```

super user privileges should be handled with care due to their potential to disrupt the system’s functionality. Mistaken changes to key system files or unauthorized access can lead to severe issues.

## Reference

1. Developer Roadmaps [Linux Roadmap] 
   - https://roadmap.sh/linux