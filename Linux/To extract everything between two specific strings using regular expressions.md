#  To extract everything between two specific strings using regular expressions

[toc]

## 1. Regular expressions

```shell
<StartString>(.*?)<EndString>
```

Ex) a Scan Session using \<Service Generic Scan\> protocol in 'Service' protocol category

```shell
a Scan Session using (.*?) protocol in '(.*?)' protocol category
```

## 2. Grep with regex

```shell
grep [options] '<regular_expression>' [file(s)]
```

Ex) a Scan Session using \<Service Generic Scan\> protocol in 'Service' protocol category

```shell
grep -rP "a Scan Session using (.*?) protocol in '(.*?)' protocol category" .
```

## 3. Replace string

For all files on sub directories.

```shell
find . -type f -name "*.py" -exec sed -i 's/<old_function_name>/<new_function_name>/g' {} +
```

- -type f : only matches files (not directories)

- -name "*.py" : filters to Python files

- -exec : runs the following command

- sed -i : -i flag tells sed to modify the files in place.

- 's/old/new/g' : sed substitution command

- {} : find replaces with the current filename.

- \+ : recursive