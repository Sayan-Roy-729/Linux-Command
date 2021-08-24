---
title: 'Navigate Between Folders'
date: '2022-10-16'
image: basic-command-nomenclatures.jpg
excerpt: We will learn all about command structures look like as well as arguments and options. We also learn combining options and long form options and when what have to use! Also learn some commands.
category: linux-commands
isFeatured: false
---

## touch
To create a new file from the command line, use the **touch** command. Provide a filename, and that file will be created for you (assuming it doesn't exits).\

For example, **touch chicken.txt** would create a chicken.txt file in the current directory.
```bash
touch <filename>
```
If you try to use touch with a file that already exits, it will simply update the access and modification dates to the current time.\

You can also create multiple files at a time. The file names will be space separated.
```bash
touch rose lily jacob
```

You can also create files with the help of relative paths like
```bash
touch ../cutePic
```

## file
The file command can be used to determine the file type of a specific file. It's honestly not that important!\
```bash
file <filename>
```
For example, running **file contract.pdf** will tell us the file type of contract.pdf *"contract.pdf: PDF document, version 1.4"*\
Note, it does not use the file extension to decide on the file type. We could have a pdf file named app.png.

## mkdir
To create new directories, we use the make directory (mkdir) command.
```bash
mkdir <foldername>
```
We provide one or more directory names and it will create them for us.\
For example, we could run
```bash
mkdir images styles
```
This command will create two folders into your current directory named *images* and *styles*.\
Now in your current directory, let's assume there is no directory named Horses. So, this bellow command gives error *mkdir: cannot create directory 'Horses/Mares': No such file or directory*.
```bash
mkdir Horses/Mares
```
But if you pass **-p** option, then it will create *Mares* directory inside the *Horses* directory. If the parent *Horses* directory is not present, then it will also create that directory.
```bash
mkdir -p Horses/Mares
```