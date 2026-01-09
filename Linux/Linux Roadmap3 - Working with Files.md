Linux Roadmap 3

# Working with Files

## 1. Intro

Working with files is an essential part of Linux and it’s a skill every Linux user must have. In Linux, everything is considered a file: texts, images, systems, devices, and directories. Linux provides multiple command-line utilities to create, view, move or search files. Some of the basic commands for file handling in Linux terminal include touch for creating files, **mv** for moving files, **cp** for copying files, **rm** for removing files, and **ls** for listing files and directories.

## 2. File Permissions

By design, Linux is a multi-user operating system. In an enterprise system, there would be multiple users accessing the same system. But if any user could access and modify all files belonging to other users or system files, this would certainly be a security risk.

This is why UNIX and thus Linux (Linux is a Unix-like system) has built-in security measure in place. This ensures that a file or directory can be accessed, modified or executed by only desired users.

Which file would be accessed by which user is decided by two factors in Linux:

- File ownership

- File permission

Understanding file ownership and permission is crucial for a Linux user

### 1) File ownership

Every file and directory in Linux has three kinds of owners

#### (1) User

User is the owner of the file. When you create a file, you become the owner of the file. The ownership

can be changed as well, but we’ll see that later.

#### (2) Group

 Every user is part of a certain group(s). A group consists of several users and this is one way to manage users in a multi-user environment.

For example, if you have dev team, QA team and sysadmin team accessing the same system, you should create separate groups for them. This way, you can manage files and security of the system effectively. It saves time because instead of manually adding permission for each user, you can simply add them to a group and change the permission for the group. You’ll see how to do it later in this article.

#### (3) Other

‘Other’ can be considered as a big group with all the users on the system. Basically, anyone with access to the system belongs to this group.

In other words, ‘User’ is a single user, Group is a collection of users and Other consists of all the users on the system.

### 2) File permission

Every file and directory in Linux have the following three permissions for all the three kinds of owners:

#### (1) Permissions for files

- Read
  - View or copy file contents
- Write
  - Modify file contents
- Execute
  - Run the file (If it’s executable)

#### (2) Permissions for directories

- Read
  - List all files and copy the files from directory
- Write
  - Add or delete files into directory (needs execute permission as well)
- Execute
  - Enter the directory

### 3) Understanding file permissions and ownership

When use the ‘ls’ command with option -l on a file, an output like this:

```shell
-rwxrw-r-- 1 abcd xyz 10 Aug 8 13:43 test.txt
```

![image-20250915172620256](.\imgs\image-20250915172620256.png)

#### (1) File type

Denotes the type of file. ‘d’ means directory, ‘-’ means regular file, ‘l’ means a symbolic link.

#### (2) Permissions

This field shows the permission set on a file. I’ll explain it in detail in the next section.

![image-20250915173027526](.\imgs\image-20250915173027526.png)

- The file has read, write and execute permissions for the User owner. (abcd)
- The file has read and write permissions for the Group but not execute. (group xyz)
- The file has only read permission for Other i.e. everyone that has access to the system.

#### (3) Hard link count

Shows if the file has hard links. Default count is one.

#### (4) User

The user who owns the files.

#### (5) Group

The group that has access to this file. Only one group can be the owner of a file at a time.

#### (6) File size

Size of the file in bytes.

#### (7) Modification time

The date and time the file was last modified.

#### (8) Filename

Filename: Obviously, the name of the file or directory.



The file ‘test.txt’ is owned by user ‘abcd’ and ‘abcd’ has read, write and execute permission. All the members of group ‘xyz’ have read and write access to this file while everyone else has only read access to this file.

Root user has super powers and normally, it has read, write and execute permissions to all the files, even if you don’t see it in file permissions.

A single user may be the member of several groups but only the primary group of the user is the group owner of a file created by the user. The primary group of a user can be found using the id command.

```shell
id -gn [username]
```

### 4) Change file permissions

There are two ways to use the ‘chmod’ command for changing the permissions on a file in Linux:

- Absolute mode
- Symbolic mode

#### (1) Using 'chmod' in absolute mode

In the absolute mode, permissions are represented in numeric form (octal system to be precise). In this system, each file permission is represented by a number.

##### a. r (read) = 4

##### b. w (write) = 2

##### c. x (execute) = 1

##### d. – (no permission) = 0

With these numeric values, you can combine them and thus one number can be used to represent the entire permission set.

| **Number**         | **Permission** |
| ------------------ | -------------- |
| **0**              | ---            |
| **1**              | --x            |
| **2**              | -w-            |
| **3 (i.e. 2+1)**   | -wx            |
| **4**              | r--            |
| **5 (i.e. 4+1)**   | r-x            |
| **6 (i.e. 4+2)**   | rw-            |
| **7 (i.e. 4+2+1)** | rwx            |

Suppose you want to change the file permission on agatha.txt so that everyone can read and write but no one can execute it? In that case, you can use the **'chmod'** command like this:

- Input

```shell
chmod 666 test.txt
```

- Output

```shell
-rw-rw-rw- 1 abcd xyz 10 Aug 8 13:51 test.txt
```

#### (2) Using chmod in symbolic mode

The problem with the absolute mode is that you should always provide three numbers for all the three owners even if you want to change the permission set for just one owner.

This is where you can use the symbolic mode with **'chmod'** command.

In symbolic mode, owners are denoted with the following symbols:

##### a. u = user owner

##### b. g = group owner

##### c. o = other

##### d. a = all (user + group + other)

The symbolic mode uses mathematical operators to perform the permission changes:

##### a. \+ : for adding permissions

##### b. – : for removing permissions

##### c. = : for overriding existing permission with new value

- Input

```shell
chmod g+x test.txt
```

- Output

```shell
-rw-rwxrw- abcd xyz 10 Aug 8 13:56 test.txt
```

You can also combine multiple permission changes in one command. Suppose you want to remove the read and write permission and add execute permissions for Other. You also want to add execute permission for the User owner. You can do all of it one single command:

- Input

```shell
chmod o-rw+x, u+x test.txt
```

- Output

```shell
-rwxrwx--x 1 abcd xyz 10 Aug 8 14:02 test.txt
```

If you want to change the permissions for all three kinds of users at the same time, you can use it in the following manner:

- Input

```shell
chmod a-x test.txt
```

- Output

```shell
-rw-rw---- 1 abcd xyz 10 Aug 8 14:02 test.txt
```

### 5) Change file ownership

To change the ownership of a file, you can use the command ‘chown’.

```shell
chown [NEW-USER-NAME] [FILE-NAME]
```

If you want to change the user as well as group:

```shell
chown [NEW-USER-NAME]:[NEW-USER-GROUP] [FILE-NAME]
```

If you just want to change the group:

```shell
chown :[NEW-USER-GROUP] [FILE-NAME]
```

or use chgrp command:

```shell
chgrp [NEW-USER-GROUP] [FILE-NAME]
```

If you want to change the user owner and group to root:

- Input

```shell
sudo chown root:root agatha.txt
```

- Output

```shell
-rw-rw---- 1 root root 10 Aug 8 14:05 test.txt
```

Finally, two groups cannot own the same file.

### 6) A precedence in file permissions

Think of a situation, where the user owner doesn’t have any permissions, group has read permission while others have read and write permissions.

```shell 
----r--rw- 1 abcd xyz 10 Aug 8 13:43 test.txt
```

In this case, although the group ‘xyz’ to which ‘abcd’ belongs has read access and everyone (including user ‘abcd’ can read and write file, user ‘abcd’ cannot do anything about the file.

In Linux, the precedence takes from user and then group and then to other. Linux system checks who initiated the process (cat or less in our example). If the user who initiated the process is also the user owner of the file, the user permission bits are set.

If the owner of the file didn’t initiate the process, then the Linux system checks the group. If the user who initiated the process is in the same group as the owner group of the file, group permissions bit are set.

If this process owner is not even in the group as the file’s group owner, then the other permission bits are set.



## 2. Archiving and Compressing

Linux offers powerful utilities for archiving, where multiple files and directories are combined into a single file, primarily for backup and simplification of distribution. The main tools used for this purpose are **tar**, **gzip**, and **bzip2**.

The ‘tar’ command, originally for tape archiving, is a versatile tool that can manage and organize files into one archive. Meanwhile, ‘gzip’ and ‘bzip2’ are used for file compression, reducing the file size and making data transmission easier.

- To create a tar archive

```shell
tar cvf archive_name.tar directory_to_archive/
```

- To extract a tar archive

```shell
tar xvf archive_name.tar
```

- To create a gzip compressed tar archive

```shell
tar cvzf archive_name.tar.gz directory_to_archive/
```

- To create a bzip2 compressed tar archive

```shell
tar cvjf archive_name.tar.bz2 directory_to_archive/
```

## 3. Copying and Renaming Files

- To copy files

```shell
cp /path/to/original/file /path/to/copied/file
```

- To rename or move files

```shell
mv /path/to/original/file /path/to/new/file
```

## 4. Soft and Hard Links

In Unix-like operating systems like Linux, soft (symbolic) and hard links are simply references to existing files that allow users to create shortcuts and duplication effects within their file system.

A hard link is a mirror reflection of the original file, sharing the same file data but displaying a different name and inode number. It’s vital to note that if the original file is deleted, the hard link still retains the file data.

On the other hand, a soft link, also known as a symbolic link, is more like a shortcut to the original file. It has a different inode number and the file data resides only in the original file. If the original file is removed, the symbolic link breaks and will not work until the original file is restored.

- To create a hard link

```shell
ln source_file.txt hard_link.txt
```

- To create a soft link

```shell
ln -s source_file.txt soft_link.txt
```

## Reference

1. Developer Roadmaps [Linux Roadmap]
   - https://roadmap.sh/linux
2. LINUX HANDBOOK [Linux File Permissions and Ownership Explained with Examples]
   - https://linuxhandbook.com/linux-file-permissions/

