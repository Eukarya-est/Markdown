#  '\ufeff',  A string is the same quasi, but not the same  

[toc]

## 1. Phenomenon

The variable 'target' is from a csv file, the other variable 'file' is from a 'os' package.

Both 'target' and 'file' have 'axial.feature' value, but result of operator '==' is <u>False</u>  

### 1) Code

```python
for  root, _, files  in os.walk(START.dir_name):
  for  file  in  files:
     print(f"[{str(target)}] vs [{str(file)}]" )
     print(f"{str(target) ==  str(file)}" )
```

### 2) Result

```shell
[axial.feature] vs [axial.feature]
```

## 2. Cause

The Python opens the csv file with no encoding option, Thus,  the variable 'target' from the csv file encode as UTF-16. Then, the variable 'target' add a code '\ufeff' in front of UTF code.

\* In [UTF-16](https://en.wikipedia.org/wiki/UTF-16 "UTF-16"), a Byte Order Mark; BOM (`U+FEFF`) may be placed as the first bytes of a file or character stream to indicate the endianness (byte order) of all the 16-bit code units of the file or stream.

### 1) UTF-8 code of 'target'

''\ufeff\u0061\u0078\u0069\u0061\u006c\u002e\u0066\u0065\u0061\u0074\u0075\u0072\u0065'

### 2) UTF-8 code of 'file'

''\u0061\u0078\u0069\u0061\u006c\u002e\u0066\u0065\u0061\u0074\u0075\u0072\u0065'

## 3. Solution

Add the encoding option(encoding="utf-8-sig") to the 'with open' logic.

- Before

```python
try:
  with  open(f'{_target_list_path}', 'r', newline='') as  csvfile:
	reader  =  csv.reader(csvfile)
	  for  row  in  reader:
		if  row:
		  data.append(row[0])
			else:
              continue
```

- After

```python
try:
  with  open(f'{_target_list_path}', 'r', newline='', encoding="utf-8") as  csvfile:
	reader  =  csv.reader(csvfile)
	  for  row  in  reader:
		if  row:
		  data.append(row[0])
              else:
              continue
```

## Reference

1. Wikipedia [Byte order mark]
   - https://en.wikipedia.org/wiki/Byte_order_mark#:~:text=In