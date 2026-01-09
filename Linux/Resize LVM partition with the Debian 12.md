# Resize LVM partition with the Debian 12

[toc]

## 1. Check for Available Space

### 1) Identify the Volume Group

```shell
sudo vgdsiplay
```

OR

```shell
sudo vgs
```

### 2) **Find the Logical Volume**

```shell
sudo lvs
```

OR

```shell
lvdisplay
```

## 2. Extend the Logical Volume

### 1) Ratio

```shell
sudo lvextend -l +20%FREE /dev/[vg-name]/var.
```

### 2) Absolute Value

```shell
sudo lvextend -L +10G /dev/[vg-name]/var
```

## 3. Resize the File system

```shell
sudo resize2fs /dev/[vg-name]/var
```

