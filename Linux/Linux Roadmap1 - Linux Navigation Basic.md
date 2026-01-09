Linux Roadmap 1

# Linux Navigation Basic

[toc]

## 1. Intro

In Linux, navigation between directories and files is a fundamental, yet essential function that allows you to exploit the power of the command-line interface (CLI).

## 2. Basic Commands

### 1) Change directory

```shell
cd /path/to/directory
```

### 2) Create directory

```shell
mkdir [DIRECTORY-NAME]
```

### 3) Lists files and directories in the current directory

```shell
ls
```

### 4) View current working directory (<u>P</u>rint <u>W</u>orking <u>D</u>irectory)

```shell
pwd
```

### 5) View a manual page for a command

```shell
man [COMMAND]
```

- ex)

```shell
man ls
```

## 3. File Handling

### 1) File creation

Creating files in Linux is about making new blank or filled files on your computer. You can use commands like touch to create an empty file, echo to make a file with some text inside, or cat to type directly into a new file. These commands help you set up and save your documents or data.

```shell
touch [FILE-NAME]
```

* Con<u>cat</u>enate

```shell
cat > [FILE-NAME]
```

Both these commands create a new “[filename].txt” if it does not already exist.

### 2) File move

In Linux, moving files is an essential task that you will need to perform quite frequently. The mv command, short for move, is used to move files and directories from one location to another. The mv command can also be used for renaming files in Linux.

```shell
mv [options] <source> <destination>
```

Here, source denotes the file or directory that you want to move while destination denotes the location where you want to move your source file or directory.

### 3) File removal

Deleting files in Linux means getting rid of unwanted or unnecessary files from your computer. You use the rm command to delete a file, and it’s permanent, so be careful. You can also use rm -i (interactive) to ask for confirmation before deleting, which helps prevent accidental loss of important files.

- <u>r</u>e<u>m</u>ove

```shell
rm [OPTIONS] [FILE-NAME]
```

- Ask for confirmation

```shell
rm -i [FILE-NAME]
```

- Removes an empty directory

```shell
rmdir [DIRECTORY-NAME]
```

## 4. Understanding Directory Hierarchy

In Linux, understanding the directory hierarchy is crucial for efficient navigation and file management. A Linux system’s directory structure, also known as the Filesystem Hierarchy Standard (FHS), is a defined tree structure that helps to prevent files from being scattered all over the system and instead organize them in a logical and easy-to-navigate manner.

- /: Root directory, the top level of the file system.
- /home: User home directories.
- /bin: Essential binary executables.
- /sbin: System administration binaries.
- /etc: Configuration files.
- /var: Variable data (logs, spool files).
- /usr: User programs and data.
- /lib: Shared libraries.
- /tmp: Temporary files.

## Reference

1. Developer Roadmaps [Linux Roadmap] 
   - https://roadmap.sh/linux

