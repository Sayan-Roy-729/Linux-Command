---
title: 'Navigate Between Folders'
date: '2022-10-16'
image: basic-command-nomenclatures.jpg
excerpt: We will learn all about command structures look like as well as arguments and options. We also learn combining options and long form options and when what have to use! Also learn some commands.
category: linux-commands
isFeatured: false
---

## cat:
The cat command con**cat**enates and prints the contents of files.
```bash
cat <filename>
```
cat < filename > will read the contents of a file and print them out. For example, **cat instructions.txt** will read in from the instructions.txt and then print the contents out to the screen.

## cat cont'd:
If we provide cat command with multiple files, it will concatenate their contents and output them.\
```bash
cat <file1> <file2>
```
**cat peanutbutter.js jelly.js** will output peanutbutter.js first and immediately after print the contents of jelly.css.

## less:
The **less** command displays the contents of a file, one page at a time.
```bash
less <fileName>
```
We can navigate forwards and backwards through the file, which is especially useful with very large files.\

**less somefile.txt** will display the contents of somefile.txt using less.\

When viewing a file using less...
- press **space** or **f** to go to the next page of the file
- press **b** to go back to the previous page
- press **Enter** or **Down arrow** to scroll by one line
- to search, type forward slash (**/**) followed by a pattern and type what you want to search
- press **q** to quite

## tac:
tac (cat spelled backwards) will concatenate and print files in reverse. It prints each line of a file, staring with last line. You can think of it as printing in reverse "vertically".\
```bash
tac file.txt
```

## rev:
The **rev** command prints the contents of a file, reversing the order of each line. Think of it as a "horizontal" reverse, whereas tac is "vertical" reverse.
```bash
rev file.txt
```

## head:
The **head** command prints a portion of a file, staring from the beginning of the file. By default, it prints the first 10 lines of a file.\
```bash
head filename.txt
```
**head warAndPeace.txt** would print the first 10 lines of the wardAndPeace.txt file.

## head contd:
We can also specify a number of lines for head to print using the **-n** option (or --lines) followed by an integer.\
```bash
head -n 21 warAndPeace.txt
```
The above command would print the first 21 lines of the warAndPeace.txt file.\
We can also use an even shorted syntax to specify a number of lines:
```bash
head -3 filename.txt
```
This will print the first 3 lines of the file.

## head contd contd:
We can also provide a number of bytes to print out, rather than lines using the **-c** option.
```bash
head -c 8 warAndPeace.txt
```
Above command would print the first 8 bytes of the warAndPeace.txt file.

## tail:
The tail command works similarly to the head command, except it prints from the end of a file. By default, it prints the last 10 lines of a file.\
```bash
tail filename.txt
```
**tail warAndPeace.txt** would print the last 10 lines of the warAndPeace.txt file.\
The same **-n** and **-c** options we saw with head also work with the tail command.\
Another very useful option is **-f**. It follows the file and if any changes to the file, it will print that. It helps very much for monitoring the log files.

## wc:
The word count command can tell us the number of words, lines or bytes in files.
```bash
wc -l students.txt
```
By default, it prints out three numbers: *the lines*, *words* and *bytes* in a file.\
- We can use the **-l** option to limit the output to the number of lines.\
- The **-w** option limits the output to the number of words in the file.\
- The **-m** option limits the output to the number of characters in the file.\
- The **-c** option limits the number of bytes of the file.\

## sort:
The sort command outputs the sorted contents of a file (it does not change the file itself). By default, it will sort the lines of a file alphabetically.
```bash
sort filename.txt
```
**sort names.txt** would print each line from names.txt sorted in alphabetical order.\

## sort cont'd:
The **-r** option tells the sort command to sort in reverse order.
```bash
sort -r filename.txt
```
**sort names.txt -r** would print each line from names.txt, sorted in reverse alphabetical order.

## uniques only:
The **-u** option tells the sort command to ignore duplicates and instead only sort unique values.
```bash
sort -u prices.txt
```

## sorting by field:
We can specify a particular "column" that we want to sort, using the **-k** option followed by a field number.
```bash
sort data.txt -nk 2
```
In this example, **sort data.txt -nk 2** tells sort to use the numeric sort and to sort using the 2nd field.

```txt
pencil 0.50
flowers 9.99
pie 4.99
soda 0.99
```
to
```txt
pencil 0.50
soda 0.99
pie 4.99
flowers 9.99
```