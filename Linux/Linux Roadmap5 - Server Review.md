Linux Roadmap 5

# Server Review

[toc]

## 1. Intro

The process of reviewing a server in Linux involves assessing the server’s performance, security, and configuration to identify areas of improvement or any potential issues. The scope of the review can include checking security enhancements, examining log files, reviewing user accounts, analyzing the server’s network configuration, and checking its software versions.

## 2. Uptime load

When managing a Linux server, one critical metric deserving close scrutiny is the “uptime”. The **'uptime'** command in Linux gives information about how long the system has been running without shutting down or restarting, and the system load average.

The system load average is an important indicator that illustrates the amount of computational work that a computer system performs. It’s a reflection of how many processes are waiting in line to get CPU time. The system load average is typically shown for 1, 5, and 15 minutes durations.

By consistently analyzing the uptime and load on a Linux server, administrators can identify system usage patterns, diagnose possible performance issues, and determine an efficient capacity planning strategy. If a server has a high load average, it may suggest that the system resources are not sufficient or are misconfigured, leading to possible slow performance or system unresponsiveness.

- Example

  - Input

  ```shell
  uptime
  ```

  - Output

  ```shell
  11:00:57 up 3 min, 1 user, load average: 0.01, 0.02, 0.00
  ```

In the output above, “3 min” tells us how long the system has been up, while “0.01, 0.02, 0.00” shows the system’s load average over the last one, five, and fifteen minutes, respectively.

## 3. Authentication Logs

When dealing with a Linux server and its maintenance, one of the most critical components to regularly review is the auth logs. These logs, usually located in /var/log/auth.log (for Debian-based distributions) or /var/log/secure (for Red Hat and CentOS), record all authentication-related events and activities which have occurred on the server. This includes, among others, system logins, password changes, and issued sudo commands.

Auth logs are an invaluable tool for monitoring and analyzing the security of your Linux server. They can indicate brute force login attacks, unauthorized access attempts, and any suspicious behavior. Regular analysis of these logs is a fundamental task in ensuring server security and data integrity.

Here is an example of how you can use the ‘*tail*’ command to view the last few entries of the authentication log:

- Example

  - Input

  ```shell
  tail /var/log/auth.log
  ```

  - Output

  ```shell
  Aug 28 09:18:04 TEST systemd-logind[168]: New seat seat0.
  Aug 28 09:18:04 TEST login[334]: pam_unix(login:session): session opened for user TEST(uid=1000) by (uid=0)
  Aug 28 09:18:04 TEST systemd-logind[168]: New session 1 of user TEST.
  Aug 28 09:18:04 TEST systemd: pam_unix(systemd-user:session): session opened for user TEST(uid=1000) by (uid=0)
  Aug 28 10:17:01 TEST CRON[14490]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
  Aug 28 10:17:01 TEST CRON[14490]: pam_unix(cron:session): session closed for user root
  Aug 29 10:57:46 TEST systemd-logind[177]: New seat seat0.
  Aug 29 10:57:47 TEST login[340]: pam_unix(login:session): session opened for user TEST(uid=1000) by (uid=0)
  Aug 29 10:57:47 TEST systemd-logind[177]: New session 1 of user TEST.
  Aug 29 10:57:47 TEST systemd: pam_unix(systemd-user:session): session opened for user TEST(uid=1000) by (uid=0)
  
  ```

## 4. Services Running

Linux servers are popular for their stability and flexibility, factors that make them a preferred choice for businesses and organizations when it comes to managing various services. Services that run under a Linux server can range from web services to database services, DNS servers, mail servers, and many others.

As a Linux system administrator, it’s important to periodically review these running services to manage resources, check their statuses, and troubleshoot issues, ensuring the health and performance of the server.

Linux has a variety of tools to achieve this, such as: **systemctl**, **service**, **netstat**, **ss** and **lsof**.

\* systemd is like the traffic manager for your Linux system. It’s a modern tool that organizes and supervises how different parts of your system start and run.

### 1) systemctl

A remote control for your Linux system. With this tool, you can start, stop, or restart services.

```shell
systemctl [COMMAND] [SERVICE]
```

- [COMMAND] : The action we want to perform (start, stop, enable, disable, etc.)
- [SERVICE] : The name of the service we want to perform the action on.

#### a. Start and Stop Services.

```shell
systemctl start sshd
```

```shell
systemctl stop sshd
```

#### b. Enable and Disable Service

```shell
systemctl enable firewalld
```

```shell
systemctl disable firewalld
```

#### c. View the Status of Services

```shell
systemctl status firewalld
```

#### d. Restart and Reload Services

```shell
systemctl restart sshd
```

```shell
systemctl reload httpd
```

#### e. Mask and Unmask Services

```shell
systemctl mask mysql
```

```shell
systemctl unmask mysql
```

#### f. Change the Default Target

```shell
systemctl set-default graphical.target
```

#### g. List Unit Files

```shell
systemctl list-unit-files
```

#### f. Mask and Unmask Unit Files

```shell
systemctl mask sshd.service
```

```shell
systemctl unmask sshd.service
```

### 2) service

The **'service'** command manages system services, which are long-running processes that are started at boot time and run in the background. The ‘service’ command is used to start, stop, restart, and check the status of these services. It is a front-end to the systemctl command, which is used to manage the systemd service manager.

### 3) netstat

The **'netstat'** stands for network statistics. It allows users to display network-related information and diagnose various networking issues. The command has several options that can be combined to retrieve specific details.

```shell
netstat [OPTIONS]
```

## 5. Nano: A File Editing Tool

Nano is a popular, user-friendly text editor used for creating and editing files directly within the Linux command line interface (CLI). It is an alternative to editors like Vi and Emacs and is considered more straightforward for beginners due to its simple and intuitive interface.

### 1) Install

#### a. apt(Ubuntu, Debian) based distributions

```shell
sudo apt update
sudo apt install nano
```

#### b. Arch Linux

```shell
sudo pacman -S nano
```

#### c. yum (CentOS) based distributions

```shell
sudo yum install nano
```

#### d. dnf (Fedora) based distributions

```shell
sudo dnf install nano
```

### 2) Open a File

```shell
nano [FILE-NAME]
```

### 3) Editing a File

Once you’ve opened a file, you can start editing right away.

### 4) Save a File

To save your changes, you press [Ctrl] + [O], then [Enter].

### 5) Exit

To exit nano, you press [Ctrl] + [X]. If you’ve made changes that you haven’t saved, nano will ask you if you want to save them.

Press [Y] to save your changes, or [N] to discard them.

### 6) Advanced Commands with Nano

| **Flag** | **Description**                                            | **Example**           |
| -------- | ---------------------------------------------------------- | --------------------- |
| **-B**   | Makes a backup of the  current file before saving changes. | nano -B [filename]    |
| **-I**   | Enables automatic indentation.                             | nano -I [filename]    |
| **-N**   | No conversion from  DOS/Mac format.                        | nano -N [filename]    |
| **-T**   | Sets the size of a tab to the given number of spaces.      | nano -T 3 [filename]  |
| **-U**   | Enables undo  functionality.                               | nano -U [filename]    |
| **-Y**   | Syntax highlighting                                        | nano -Y sh [filename] |
| **-c**   | Constantly show the  cursor position.                      | nano -c [filename]    |
| **-i**   | Automatically indents new lines.                           | nano -i [filename]    |
| **-k**   | Toggle cut so it cuts  from cursor position.               | nano -k [filename]    |
| **-m**   | Enable mouse support.                                      | nano -m [filename]    |

## Reference

1. Developer Roadmaps [Linux Roadmap]
   - https://roadmap.sh/linux
2. Geeksforgeeks [How to Manage System Services in Linux]
   - https://www.geeksforgeeks.org/systemctl-in-unix/

