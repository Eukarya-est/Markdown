Linux Roadmap 4

# Text Processing

[toc]

## 1. Intro

Text processing is an essential task for system administrators and developers. Linux, being a robust operating system, provides powerful tools for text searching, manipulation, and processing.

Users can utilize commands like **awk**, **sed**, **grep**, and **cut** for text filtering, substitution, and handling regular expressions. Additionally, the shell scripting and programming languages such as Python and Perl also provide remarkable text processing capabilities in Linux.

Although being primarily a command-line operating system, Linux also offers numerous GUI-based text editors including ‘gedit’, ‘nano’, and ‘vim’, which make text editing convenient for both beginners and advanced users.

## 2. 'stdout' and 'stderr'

The concepts of stdout and stderr in Linux belong to the fundamentals of Linux text processing. In Linux, when a program is executed, three communication channels are typically opened, namely, STDIN (Standard Input), STDOUT (Standard Output), and STDERR (Standard Error).

Each of these channels has a specific function. STDOUT is the channel through which the output from most shell commands is sent. STDERR, on the other hand, is used specifically for sending error messages. This distinction is very useful when scripting or programming, as it allows you to handle normal output and error messages in different manners.

```shell
command > stdout.txt 2)>stderr.txt
```

In this example, the ”>” operator redirects the standard output (stdout) into a text file named stdout.txt, while “2>” redirects the standard error (stderr) into stderr.txt. This way, normal output and error messages are separately stored in distinct files for further examination or processing.

## 3. Cut

The *cut* command is a text processing utility that allows you to cut out sections of each line from a file or output, and display it on the standard output (usually, the terminal). It’s commonly used in scripts and pipelines, especially for file operations and text manipulation.

This command is extremely helpful when you only need certain parts of the file, such as a column, a range of columns, or a specific field. For example, with Linux system logs or CSV files, you might only be interested in certain bits of information.

A basic syntax of cut command is:

```shell
cut [OPTIONS] [FILE-NAME]
```

- Example

  - Input

  ```shell
  echo "one,two,three,four" | cut -d "," -f 2
  ```

  - Ouput

  ```shell
  Two
  ```

This command will output the second field (two) by using the comma as a field delimiter (*-d* ",").

Here is a list of the most commonly used options with the `cut` command:

| **Option**                   | **Description**                                              |
| ---------------------------- | ------------------------------------------------------------ |
| **-b,**  **-bytes=LIST**     | Selects  only the bytes specified in LIST .                  |
| **-c,**  **character=LIST**  | Selects only the characters specified  in LIST.              |
| **-d,**  **Delimiter=DELIM** | Uses DELIM as  the field delimiter character instead of the tab character. |
| **-f,**  **-fields=LIST**    | Selects only the fields specified  in LIST, sep arated by the delimiter character (default is tab). |
| **-n**                       | Do  not split multi-byte characters (no effect  unless -b or -c is specified). |
| **-complement**              | Invert the selection of  fields/characters. Print the fields/characters not selected. |

### 1) *-b* (byte): Extract specific bytes

To extract the specific bytes, you need to follow *-b* option with the list of byte numbers separated by comma. Range of bytes can also be specified using the hyphen(-). It is necessary to specify list of byte numbers otherwise it gives error.

Tabs and backspaces are treated like as a character of 1 byte.

- Example

  1. List without ranges

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -b 1,2,5 test.txt
    ```

    - Output

    ```shell
    ACR
    BA 
    CU
    DI
    EQV
    ```

  2. List with ranges

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -b 1-3, 5-7 test.txt
    ```

    - Output

    ```shell
    ACERACE
    BAS CA
    CUT
    DIC
    EQUVAL
    ```

Special Form: Selecting bytes from beginning to end of line

1. Postmodifier (*x-*)

  - In this, 2- indicate from 2nd byte to end byte of a line

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -b 2- test.txt
    ```

    - Output

    ```shell
    CE RACE
    ASE CASE
    UT
    ICE
    QUVALENT
    ```

2. Premodifier (*-x*)

  - In this, -3 indicate from 1st byte to 3rd byte of a line

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -b -3 test.txt
    ```

    - Output

    ```shell
    ACE
    BAS
    CUT
    DIC
    EQU
    ```

### 2) *-c *(column): Cut by character

- Example

  1. List without ranges

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -c 2,5,7 test.txt
    ```

    - Output

    ```shell
    CRC
    A A
    U
    I
    QVL
    ```

  2. List with ranges

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -c 1-3, 5-7 test.txt
    ```

    - Output

    ```shellp
    ACERACE
    BAS CA
    CUT
    DIC
    EQUVAL
    ```

Special Form: Selecting bytes from beginning to end of line

1. Postmodifier (*x-*)

  - In this, 2- indicate from 2nd byte to end byte of a line

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -c 2- test.txt
    ```

    - Output

    ```shell
    CE RACE
    ASE CASE
    UT
    ICE
    QUVALENT
    ```

2. Premodifier (*-x*)

  - In this, -3 indicate from 1st byte to 3rd byte of a line

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -c -5 test.txt
    ```

    - Output

    ```shell
    ACE R
    BASE
    CUT
    DICE
    EQUIV
    ```

### 3) *-f *(field)

To extract the useful information, you need to cut by fields rather than columns. *-c* option is useful for fixed-length lines. List of the fields number specified must be separated by comma. Ranges are not described with *-f* option. cut uses tab as a default field delimiter but can also work with other delimiter by using *-d* option.

Space is not considered as delimiter in UNIX.

- Example

  1. Extract first field

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -f 1 test.txt
    ```

    - Output

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

  2. ‘*-d*’ option is used

    - test.txt

    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```

    - Input

    ```shell
    cut -d “ ” -f 1 test.txt
    ```

    - Output

    ```shell
    ACE
    BASE
    CUT
    DICE
    EQUIVALENT
    ```

  3. Extract fields 1 to 4

    - test.txt

    ```shell
    ABC DEF GHI JKL MNO PQR STU
    BASE CASE DICE EASE FACE 
    CONCOCT DEMOLISH
    DEVICE
    EQUIVALENT
    Ego ipse hoc reci
    Faber est suqe quisque fortunae
    ```

    - Input

    ```shell
    cut -d “ ” -f 1-4 test.txt
    ```

    - Output

    ```shell
    ABC DEF GHI JKL 
    BASE CASE DICE EASE 
    CONCOCT DEMOLISH
    DEVICE
    EQUIVALENT
    Ego ipse hoc reci
    Faber est suqe quisque
    ```

  4. --complement
  
    - As the name suggests it complement the output. 
  
      When using this option, ‘*cut*’ displays all bytes, characters, or fields except the selected ones.
  
      This option can be used in the combination with other options either with *-f* or with *-c.*
  
    - exp.txt
  
    ```shell
    ABC DEF GHI JKL MNO PQR STU
    BASE CASE DICE EASE FACE 
    CONCOCT DEMOLISH
    DEVICE
    EQUIVALENT
    Ego ipse hoc reci
    Faber est suqe quisque fortunae
    ```
  
    - Input
  
    ```shell
    cut --complement -d “ ” -f 1-3 test.txt
    ```
  
    - Output
  
    ```shell
    JKL MNO PQR STU
    EASE FACE 
    
    DEVICE
    EQUIVALENT
    reci
    quisque fortunae
    ```
  
    - test.txt
  
    ```shell
    ACE RACE
    BASE CASE
    CUT
    DICE
    EQUIVALENT
    ```
  
    - Input
  
    ```shell
    cut -d “ ” -f 1-3 exp.txt --output-delimiter=’%’
    ```
  
    - Output
  
    ```shell
    ABC%DEF%GHI 
    BASE%CASE%DICE 
    CONCOCT%DEMOLISH
    DEVICE
    EQUIVALENT
    Ego%ipse%hoc
    Faber%est%suqe
    ```
  
  5. *--version*
  
    - Input
  
    ```shell
    cut --version
    ```
  
    - Output
  
    ```shell
    cut (GNU coreutils) 8.32
    Copyright (C) 2020 Free Software Foundation, Inc.
    License GPLv3+: GNU GPL version 3 or later <https://gnu.rog/licenses/gpl.html>.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.
    
    Written by David M. Ihnat, David MacKenzie, and Jim Meyering.
    ```
  
  6. How to use tail with pipes(*|*) in cut Command
  
    - The cut command can be piped with many other commands of the unix.
    - exp.txt
  
    ```shell
    ABC DEF GHI JKL MNO PQR STU
    BASE CASE DICE EASE FACE 
    CONCOCT DEMOLISH
    DEVICE
    EQUIVALENT
    Ego ipse hoc reci
    Faber est suqe quisque fortunae
    ```
  
    - Input
  
    ```shell
    cat exp.txt | head -n 3 | cut -d ‘ ’ -f 3-4 > pipe.txt
    ```
  
    - pipe.txt
  
    ```shell
    GHI JKL
    DICE EASE
    ```

## 4. Paste

In Linux, *paste* is primarily used for merging lines from multiple files. It allows users to combine data by columns rather than rows, adding immense flexibility to textual data manipulation. Users can choose a specific delimiter for separating columns, providing a range of ways to format the output.

A basic syntax of cut command is:

```shell
paste [option] [filename]
```

A common use case of the paste command in Linux is the combination of two text files into one.

- Example

  - test.txt

  ```shell
  ACE
  BASE
  CASE
  DICE
  ERASE
  ```

  - exp.txt

  ```shell
  ABC
  BIG
  CAST
  ```

  - Input

  ```shell
  paste test.txt exp.txt > combined.txt
  ```

  - combined.txt

  ```shell
  ACE 	ABC
  BASE	BIG
  CASE	CAST
  DICE
  ERASE
  ```

  ### 1) *-d* (delimiter)

  - Paste command uses the tab delimiter by default for merging the files. The delimiter can be changed to any other character by using the *-d* option. If more than one character is specified as delimiter then paste uses it in a circular fashion for each file line separation.
  - number.txt

  ```shell
  1
  2
  3
  4
  5
  6
  ```

  - country.txt

  ```shell
  Nigeria
  Japan
  France
  Canada
  Brazil
  Australia
  ```

  - capital.txt

  ```shell
  Abuja
  Tokyo
  Paris
  Ottawa
  Brasilia
  Canberra
  ```

  - Input

  ```shell
  paste -d “|,” number.txt country.txt capital.txt > combined.txt
  ```

  - combined.txt

  ```shell
  1|Nigeria,Abuja
  2|Japan,Tokyo
  3|France,Paris
  4|Canada,Ottawa
  5|Brazil,Brasilia
  6|Australia,Canberra
  ```

  ### 2) *-s *(serial)

  - We can merge the files in sequentially manner using the *-s* option. It reads all the lines from a single file and merges all these lines into a single line with each line separated by tab. And these single lines are separated by newline.
  - number.txt

  ```shell
  1
  2
  3
  4
  5
  6
  ```

  - country.txt

  ```shell
  Nigeria
  Japan
  France
  Canada
  Brazil
  Australia
  ```

  - capital.txt

  ```shell
  Abuja
  Tokyo
  Paris
  Ottawa
  Brasilia
  Canberra
  ```

  - Input

  ```shell
  paste -s -d “:” number.txt country.txt capital.txt > serial.txt
  ```

  - serial.txt

  ```shell
  1:2:3:4:5:6
  Nigeria:Japan:France:Canada:Brazil:Australia
  Abuja:Tokyo:Paris:Ottawa:Brasilia:Canberra
  ```

  ### 3) *--version*

  - This option is same thing of ‘*cut*’ that.

  1. Combining *N* consecutive lines

     - The paste command can also be used to merge N consecutive lines from a file into a single line by specifying number hyphens(-) after paste.
     - country.txt

     ```shell
     Nigeria
     Japan
     France
     Canada
     Brazil
     Australia
     ```

     - Input

     ```shell
     $ cat coutry.txt | paste - -
     ```

     - capital.txt

     ```shell
     Nigeria  Japan
     France  Canada	
     Brazil   Australia
     ```

     - Input

     ```shell
     $ paste - - - - < country.txt
     ```

     - serial.txt

     ```shell
     Nigeria  Japan  France  Canada	
     Brazil   Australia
     ```

     

  2. Combination with other commands

     - number.txt

     ```shell
     1
     2
     3
     4
     5
     6
     ```

     - country.txt

     ```shell
     Nigeria
     Japan
     France
     Canada
     Brazil
     Australia
     ```

     - Input

     ```shell
     cut -d “ ” -f 1 country.txt | paste number.txt
     ```

     - Output

     ```shell
     1        Nigeria
     2        Japan
     3        France
     4        Canada
     5        Brazil
     6        Australia
     ```

     - Input

     ```shell
     cut -d “ ” -f 1 country.txt | paste - number.txt
     ```

     - Output

     ```shell
     Nigeria  1
     Japan    2
     France   3
     Canada  4
     Brazil    5
     Australia    6 
     ```

## 5. Sort

The *sort* command in Linux is used to sort the contents of a text file, line by line. The command uses ASCII values to sort files. You can use this command to sort the data in a file in a number of different ways such as alphabetically, numerically, reverse order, or even monthly. The sort command takes a file as input and prints the sorted content on the standard output.

```shell
sort [option] [filename]
```

```shell
sort [option] [filename] > [sorted-filename]
```

- Example

  - country.txt

  ```shell
  Nigeria
  Japan
  France
  Canada
  Brazil
  Australia
  ```

  - Input

  ```shell
  sort country.txt
  ```

  - Output

  ```shell
  Australia
  Brazil
  Canada
  France
  Japan
  Nigeria
  ```

- Options

| **Option** | **Description**                                              |
| ---------- | ------------------------------------------------------------ |
| -o         | Specifies  an output file for the sorted data. Functionally equivalent to redirecting  output to a file. |
| -r         | Sorts data in reverse order  (descending).                   |
| -n         | Sorts  a file numerically (interprets data as numbers).      |
| -nr        | Sorts a file with numeric data in  reverse order. Combines -n and -r options. |
| -k         | Sorts  a table based on a specific column number.            |
| -c         | Checks if the file is already sorted  and reports any disorder. |
| -u         | Sorts  and removes duplicate lines, providing a unique sorted list. |
| -M         | Sorts by month names.                                        |

- Example with option

  - combined.txt

  ```shell
  1 Nigeria Abuja
  2 Japan Tokyo
  3 France Paris
  4 Canada Ottawa
  5 Brazil Brasilia
  6 Australia Canberra
  ```

  - Input

  ```shell
  sort -k3 country.txt
  ```

  - Output

  ```shell
  1 Nigeria Abuja
  5 Brazil Brasilia
  6 Australia Canberra
  4 Canada Ottawa
  3 France Paris
  2 Japan Tokyo
  ```

  - The Option(-k3) in above example indicates that the sorting should be done based on the third column (Capital).

## 6. Tr

The *tr* command in Linux is a command-line utility that translates or substitutes characters.

It supports a range of transformations including uppercase to lowercase, squeezing repeating characters, deleting specific characters, and basic find and replace.

- Input

```shell
echo "hello" | tr ‘a-z’ ‘A-Z’
```

- Output

```shell
HELLO
```

### 1) To convert lower case characters to upper case.

- country.txt

```shell
Nigeria
Japan
France
Canada
Brazil
Australia
```

- Input

```shell
cat country.txt | tr [a-z] [A-Z]
or
cat country.txt | tr [:lower:] [:upper:]
or
tr [:lower:] [:upper:] < country.txt
```

- Output

```shell
NIGERIA
JAPAN
FRANCE
CANADA
BRAZIL
AUSTRALIA
```

### 2) To translate white-space character to tabs.

- test.txt

```shell
ACE RACE
BASE CASE
EQUIVALENT
```

- Input

```shell
cat test.txt | tr [:space:] “\t”
or	
tr [:space:] “\t” < test.txt
```

- Output

```shell
ACE    RACE    BASE    CASE    EQUIVALENT
```

### 3) To translate angle brackets into parenthesis. 

- test.txt

```shell
<test>
ACE RACE
BASE CASE
EQUIVALENT
```

- Input

```shell
cat test.txt | tr “<>” “()”
or	
tr “<>” “()” < test.txt
```

- Output

```shell
(test)
ACE RACE
BASE CASE
EQUIVALENT
```

### 4) To squeeze a sequence of repetitive characters using *-s* option.

To squeeze repetitive occurrences of characters specified in a set use the *-s* option. This removes repeated instances of characters of the last set specified. Or we can say that, you can convert multiple continuous spaces with a single space.

- test.txt

```shell
ACE           RACE
BASE aaaaaa CASE
EQUIVALENT aaaaaaaaaaaaa
```

- Input

```shell
cat test.txt | tr -s “ ” 
or	
tr -s “ ”< test.txt
```

- Output

```shell
ACE RACE
BASE aaaaaa CASE
EQUIVALENT aaaaaaaaaaaaa
```

- Input

```shell
cat test.txt | tr -s “a” 
or	
tr -s “a”< test.txt
```

- Output

```shell
ACE           RACE
BASE a CASE
EQUIVALENT a

```

### 5) To delete specified character using *-d* option.

- test.txt

```shell
ACE           RACE
BASE aaaaaa CASE
EQUIVALENT aaaaaaaaaaaaa
```

- Input

```shell
cat test.txt | tr -d “a” 
or	
tr -d “a”< test.txt
```

- Output

```shell
ACE RACE
BASE  CASE
EQUIVALENT 
```

- Input

```shell
cat test.txt | tr -d “E” 
or	
tr -d “E”< test.txt
```

- Output

```shell
AC           RAC
BAS aaaaaa CAS
QUIVALENT aaaaaaaaaaaaa
```

### 6) To remove all the digits from the string

- test.txt

```shell
ACE RACE 32768
BASE CASE
EQUIVALENT
```

- Input

```shell
cat test.txt | tr -d [:digit:]
or	
tr -d [:digit:] < test.txt
```

- Output

```shell
ACE RACE
BASE CASE
EQUIVALENT
```

### 7) To use *-c* (complement) option

- test.txt

```shell
ACE RACE 32768
BASE CASE
EQUIVALENT
```

- Input

```shell
cat test.txt | tr -cd [:digit:]
or	
tr -cd [:digit:] < test.txt
```

- Output

```shell
32768
```

## 7. Head

The *head* command in Linux is a text processing utility that allows a user to output the first part (or the “head”) of files. It is commonly used for previewing the start of a file without loading the entire document into memory, which can act as an efficient way of quickly examining the data in very large files. By default, the `head` command prints the first 10 lines of each file to standard output, which is the terminal in most systems.

```shell
head [option] [filename]
```

- head.txt

```shell
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

- Input

```shell
head head.txt
```

- Output

```shell
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
```

### 1) *-n [x]*

Prints the first ‘*x*’ lines instead of first 10 lines. *[x]* is mandatory to be specified in command otherwise displays an error.

- head.txt

```shell
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

- Input

```shell 
head -n 3 head.txt
```

- Output

```shell
A1
B2
C3
```

### 2) *-c [x]*

Prints the first ‘x’ bytes from the file specified. Newline count as a single character, so if head prints out a newline, it will count it as a byte. *[x]* is mandatory to be specified in command otherwise displays an error. 

- head.txt

```shell
head.txt
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

- Input

```shell
head -c 5 head.txt
```

- Output

```shell
A1
B2
```

### 3) *-q*

It is used if more than 1 file is given. Because of this command, data from each file is not precedes by its file name.

- country.txt

```shell
Nigeria
Japan
France
Canada
Brazil
Australia
```

- capital.txt

```shell
Abuja
Tokyo
Paris
Ottawa
Brasilia
Canberra
```

- Input

```shell
head country.txt capital.txt
```

- Output

```shell
==> country.txt <==
Nigeria
Japan
France
Canada
Brazil
Australia

==> capital.txt <==
Abuja
Tokyo
Paris
Ottawa
Brasilia
Canberra
```

- Input

```shell
head -q country.txt capital.txt
```

- Output

```shell
Nigeria
Japan
France
Canada
Brazil
Australia
Abuja
Tokyo
Paris
Ottawa
Brasilia
Canberra
```

### 4) *-v*

By using this option, data from the specified file is always preceded by its file name.

- country.txt

```shell
Nigeria
Japan
France
Canada
Brazil
Australia
```

- Input

```shell
head -v country.txt
```

- Output

```shell
==> country.txt <==
Nigeria
Japan
France
Canada
Brazil
Australia
```

## 8. Tail

The *tail* command is used to output the last part of the files. This command is common in situations where the user is interested in the most recent entries in a text file, such as log files. By default, ‘*tail*’ returns the last 10 lines of each file to the standard output.

```shell
tail [option] [filename]
```

- head.txt

```shell
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

- Input

```shell
tail head.txt
```

- Output

```shell
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

### 1) *-n [x]*

Prints the last ‘x’ lines instead of last 10 lines. [x] is mandatory to be specified in command otherwise displays an error. 

- head.txt

```shell
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

- Input

```shell
tail -n 3 head.txt
```

- Output

```shell
J10
K11
L12
```

Tail command also comes with an **‘+’** option which is not present in the head command. With this option tail command prints the data starting from specified line number of the file instead of end. 

- head.txt

```shell
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

- Input

```shell
tail +9 head.txt
```

- Output

```shell
I9
J10
K11
L12
```

### 2) *-c [x]*

Prints the last ‘x’ bytes from the file specified. Newline count as a single character, so if tail prints out a newline, it will count it as a byte. [x] is mandatory to be specified in command otherwise displays an error. By ‘+x’, it displays all the data after skipping num bytes from starting of the specified file and by ‘-x’, it displays the last num bytes from the file specified. Without whichever sign before ‘x’, command will display the last num bytes from the file specified.

- head.txt

```shell
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

- Input

```shell
tail -c 7 head.txt
OR
tail -c -7 head.txt
```

- Output

```shell
11
L12
```

- Input

```shell
tail -c +28 head.txt
```

- Output

```shell
J10
K11
L12
```

### 3) *-q*

It is used if more than 1 file is given. Because of this command, data from each file is not precedes by its file name.

- country.txt

```shell
Nigeria
Japan
France
Canada
Brazil
Australia
```

- capital.txt

```shell
Abuja
Tokyo
Paris
Ottawa
Brasilia
Canberra
```

- Input

```shell
tail country.txt capital.txt
```

- Output

```shell
==> country.txt <==
Nigeria
Japan
France
Canada
Brazil
Australia

==> capital.txt <==
Abuja
Tokyo
Paris
Ottawa
Brasilia
Canberra
```

- Input

```shell
tail -q country.txt capital.txt
```

- Output

```shell
Nigeria
Japan
France
Canada
Brazil
Australia
Abuja
Tokyo
Paris
Ottawa
Brasilia
Canberra
```

### 4) *-v*

By using this option, data from the specified file is always preceded by its file name.

- country.txt

```shell
Nigeria
Japan
France
Canada
Brazil
Australia
```

- Input

```shell
head -v country.txt
```

- Output

```shell
==> country.txt <==
Nigeria
Japan
France
Canada
Brazil
Australia
```

### 5) *-f*

This option is mainly used by system administration to monitor the growth of the log files written by many Unix program as they are running. This option shows the last ten lines of a file and will update when new lines are added. As new lines are written to the log, the console will update with the new lines.

The prompt doesn’t return even after work is over so, we have to use the *interrupt key* to abort this command. In general, the applications writes error messages to log files. You can use the *-f* option to check for the error messages as and when they appear in the log file.

### 6) To use head/tail with pipes(*|*)

- head.txt

```shell
A1
B2
C3
D4
E5
F6
G7
H8
I9
J10
K11
L12
```

- Input

```shell
cat head.txt | head -n 5 | tail -n 3 | sort -r > withpipe.txt
```

- withpipe.txt

```shell
E5
D4
C3
```

## 9. Join

The join command is particularly useful when you’re dealing with large volumes of data. Specifically, join uses the lines from two files to form lines that contain pairs of lines related in a meaningful way.

```shell
join [OPTION] [filename1] [fileneame2]
```

- country.txt

```shell
1 Nigeria
2 Japan
3 France
4 Canada
5 Brazil
```

- capital.txt

```shell
1 Abuja
2 Tokyo
3 Paris
4 Ottawa
5 Brasilia
6 Canberra
```

- Input

```shell
join country.txt capital.txt
```

- Output

```shell
1 Nigeria Abuja
2 Japan Tokyo
3 France Paris
4 Canada Ottawa
5 Brazil Canberra
```

| **Option**       | **Description**                                              |
| ---------------- | ------------------------------------------------------------ |
| **-a [FILENUM]** | Print  unpairable lines from file FILENUM, where FILENUM is 1 or 2, corresponding to  FILE1 or FILE2. |
| **-e [INPUT]**   | Replace missing input fields with ‘INPUT’.                   |

## 10. split

The *split* command in Linux divides a file into multiple equal parts, based on the lines or bytes specified by the user. It’s a useful command because of its practical applicability. For instance, if you have a large data file that can’t be used efficiently because of its size, then the split command can be used to break up the file into more manageable pieces. 

It splits the files into 1000 lines per file(by default) and even allows users to change the number of lines as per requirement. The names of the files are [prefix]aa, [prefix]ab, [prefix]ac, and so on.

```shell
split [OPTION] [input [prefix]]
```

- Input

```shell
split test.txt
ls
```

- Output

```shell
test.txt    xaa    xab
```

- Input

```shell
split test.txt split_
ls
```

- Output

```shell
test.txt    split_aa    split_ab
```

### 1) Split file based on number of lines.

- number.txt

```shell
1
2
3
4
5
6
```

- Input

```shell
split -l 4 number.txt split_
ls
```

- Output

```shell
test.txt    split_aa    split_ab
```

- split_aa.txt

```shell
1
2
3
4
```

- split_ab.txt

```shell
5
6
```

### 2) Split command with verbose option. 

- number.txt

```shell
1
2
3
4
5
6
```

- Input

```shell
split -l 4 number.txt split_ --verbose
```

- Output

```shell
creating file ‘split_aa’
creating file ‘split_ab’
```

- split_aa.txt

```shell
1
2
3
4
```

- split_ab.txt

```shell
5
6
```

### 3) Split file size using ‘*-b*’(byte) option

- test.txt

```shell
ACE RACE 32768
BASE CASE
EQUIVALENT
```

- Input

```shell
split -b 16 test.txt --verbose
```

- Output

```shell
creating file ‘xaa’
creating file ‘xab’
creating file ‘xac’
```

- xaa.txt

```shell
ACE RACE 32768
B
```

- xab.txt

```shell
ASE CASE
EQUIVAL
```

- xac.txt

```shell
ENT
```

### 4) Change in suffix length using ‘*-a’* option

By default, the suffix length is 2.

- number.txt

```shell
1
2
3
4
5
6
```

- Input

```shell
split -l 3 -a 4 number.txt --verbose
```

- Output

```shell
creating file ‘xaaaa’
creating file ‘xaaab’
```

### 5) Split files created with numeric suffix using ‘*-d*’ option

- number.txt

```shell
1
2
3
4
5
6
```

- Input

```shell
split -l 3 -d number.txt --verbose
```

- Output

```shell
creating file ‘x00’
creating file ‘x01’
```

### 6) Create n chunks output files using ‘*-n*’ option

- test.txt

```shell
ACE RACE 32768
BASE CASE
EQUIVALENT
```

- Input

```shell
split -n 4 test.txt
```

- xaa.txt

```shell
ACE RACE 
```

- xab.txt

```shell
32768
BAS
```

- xac.txt

```shell
E CASE
EQ
```

- xad.txt

```shell
UIVALENT
```

### 7) Avoid zero-sized split files using ‘*-e*’ option

- test.txt

```shell
ACE RACE 32768
BASE CASE
EQUIVALENT
```

- Input

```shell
split -l 2 -e test.txt
```

- xaa.txt

```shell
ACE RACE 32768
BASE CASE
```

- xab.txt

```shell
EQUIVALENT
```

## 9. Pipe

The *pipe* (*|*) is a powerful feature in Linux used to connect two or more commands together. This mechanism allows output of one command to be “piped” as input to another.

```shell
ls | grep .txt
```

In this example, *ls* lists the files in the current directory and 'grep .txt' filters out any files that don’t end with .txt. The pipe command, |, takes the output from ls and uses it as the input to grep .txt. The output of the entire command is the list of text files in the current directory.

- Input

```shell
ls | grep .txt
```

- Output

```shell
capital.txt
combined.txt
country.txt
country_list.txt
exp.txt
head.txt
number.txt
pipe.txt
reverse.txt
serial.txt
sorted_tst.txt
test.txt
withpipe.txt
```

## 11. Tee

The *tee* command reads from the standard input and writes to standard output and files. This operation gets its name from the T-splitter in plumbing, which splits the flow into two directions, paralleling the function of the ‘tee’ command.

![image-20250927225255368](.\imgs\image-20250927225255368.png)

```shell
tee [OPTION] [filename]
```

- Input

```shell
echo “hello” | tee tee_test.txt
```

- tee_test.txt

```shell
hello
```

### 1) *-a* (append) option

- tee_test.txt

```shell
hello
```

- Input

```shell
echo “hello” | tee -a test.txt
```

- tee_test.txt

```shell
hello
world	
```

### 2) The reason of using ‘*tee*’

We can use the IO redirection operator for echo or cat, so why do we need ‘*tee*’ ?

If you redirect the output from shell, ‘*sudo*’ is used to switch to regular users, so it does not work properly if you need to write to a file or add content with root permissions.

So if you run ‘*sudo echo*’ on the root-owned file as shown below, you will get a "permission denied" error and fail to add the contents.

- Status

```shell
-rw-r--r-- 1 root root   12 Aug 25 09:51 tee_test.txt 
```

- Input

```shell
sudo echo “ABC” >> tee_test.txt
```

- Output

```shell
-bash: tee_test.txt: Permission denied
```

In this case, if you receive ‘echo’ and do ‘sudo tee’, it works normally, and ‘tee’ is mainly used in shell scripts to write or append specific files with root rights.

- Status

```shell
-rw-r--r-- 1 root root   12 Aug 25 09:51 tee_test.txt 
```

- Input

```shell
echo “ABC” >> sudo tee -a tee_test.txt
```

- Output

```shell
ABC
```

- tee_test.txt

```shell
Hello
World
ABC
```

## 12. Nl

*nl* command in Linux is a utility for numbering lines in a text file. Also known as ‘number lines’, it can be handy when you need an overview where certain lines in a file are located.

```shell
nl [OPTION] [filename]
```

- test.txt

```shell
ACE RACE 32768
BASE CASE
EQUIVALENT
```

- Input

```shell
nl test.txt
```

- Output

```shell
1  ACE RACE 32768
2  BASE CASE
3  EQUIVALENT	
```

| **Option**      | **Description**                                  |
| --------------- | ------------------------------------------------ |
| **-b [STYLE]**  | Used  for numbering body lines.                  |
| **-i [NUMBER]** | Line number increment at each line.              |
| **-n [FORMAT]** | Insert  line numbers according to FORMAT.        |
| **-v [NUMBER]** | Change first line number of the given  input.    |
| **-l [NUMBER]** | Group  of NUMBER empty lines are counted as one. |
| **-s [STRING]** | Add any STRING after every logical line  number. |
| **-w [NUMBER]** | Use  different NUMBER columns for line numbers.  |

### 1) *-b* option

- test.txt

```shell
ACE RACE 32768

BASE CASE
EQUIVALENT
```

- Input

```shell
nl -b a test.txt
```

- Output

```shell
1  ACE RACE 32768
2
3  BASE CASE
4  EQUIVALENT	
```

- Input

```shell
nl -b t test.txt
```

- Output

```shell
1  ACE RACE 32768

2  BASE CASE
3  EQUIVALENT	
```

- Input

```shell
nl -b n test.txt
```

- Output

```shell
 ACE RACE 32768

 BASE CASE
 EQUIVALENT
```

## Reference

1. Developer Roadmaps [Linux Roadmap]
   - https://roadmap.sh/linux
2. Geeksforgeeks [cut command in Linux with examples]
   - https://www.geeksforgeeks.org/cut-command-linux-examples/
3. Geeksforgeeks [paste command in Linux with examples]
   - https://www.geeksforgeeks.org/paste-command-in-linux-with-examples/
4. Geeksforgeeks [tr command in Linux with examples]
   - https://www.geeksforgeeks.org/tr-command-in-unix-linux-with-examples/
5. Geeksforgeeks [head command in Linux with examples]
   - https://www.geeksforgeeks.org/head-command-linux-examples/
6. Geeksforgeeks [join Command in Linux]
   - https://www.geeksforgeeks.org/join-command-linux/
7. Geeksforgeeks [tee Command in Linux]
   - https://www.geeksforgeeks.org/tee-command-linux-example/