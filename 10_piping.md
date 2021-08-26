# Piping
## Pipes:
Pipes are used to redirect a stream from one program to another program. We can take the output of one command and redirect it to the input of another. We use the pipe character (**|**) to separate two commands. The output of the first command will be passed to the standard input of the second command.

```bash
command1 | command2
date | rev
```

## ls | less
This example pipes the output of **ls** to **less**. The /usr/bin directory typically contains a bunch of stuff, so it can be nice to use less to read the results in a more manageable way.

```bash
ls -l /usr/bin | less
ls /usr/bin -1 | wc -l
```
## Comparing Redirection & Piping:
Though both the > character and the | character are used to redirect output, they do it in very different ways.
- > connects a command to some file
- | connects a command to another command

```bash
ls -l /usr/bin > list.txt
ls -l /usr/bin | less
ls /usr/bin -1 | wc -l > count.txt
```

## **tr** command:
We use the pipe character (|) to separate two commands. The output of the first command will be passed to the standard input of the second command.

```bash
cat somefile | tr s $
```
According to manual of **tr** command, this command **translate, sequeeze and/or delete characters from standard input, writing to standard output**. The above tr command example, replace all the "s" to the "$". This below command replaces the all lower case letters to the upper case letters.

```bash
cat somefile | tr a-z A-Z
```

Delete every "s" character

```bash
cat somefile | tr -d s
cat data.txt | tr -d [:alpha:] | tr -d : | tr -d [:blank:] > phones.txt
```

## Working with Multiple Pipes:
In this example, we are calling tac with a file and then piping the output to rev. The final result is the content of file.txt printed "horizontally" and "vertically" reversed.

```bash
tac file.txt | rev
cat file | head -7 | tail -5
```

Another example can be

```bash
ls -lh | sort -rhk 5 | head -3
```
This example displays the 3 largest files in the current directory, using ls, sort and head commands. First **ls -lh** lists out all the files in the current directory. That output is passed to sort, which sorts based on the fifth field (the file size). The -h option is for human readable sort (comparing 100b, 40k, 1g etc) and the -r reverses the order so that we end up with the largest files first. Finally, that output is passed to head, which limits the results to the first 3. [Note: this is not the preferred way to find largest file! Use the **du** command instead]

```bash
du -ha /usr/bin/ | sort -h | tail -4 | head -3
```

## **tee** command:
In this example, I'm using cat to concatenate three files together before piping the output to wc to get a count of the total number of words.

```bash
cat file1 file2 file3 | wc -w
```

**What if I wanted to create a file with the output of cat?**

The tee program reads standard input and copies it both to standard output and to a file. This allows us to capture information part of the way through a pipeline, without interrupting the flow.

```bash
command1 | tee file.txt | command2
cat colors.txt words.txt | tee colors_words.txt | wc
```