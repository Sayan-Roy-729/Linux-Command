# Redirection:
## Standart Streams:
The three standard streams are communication channels between a computer program and its environment.
They are:
- Standard Input
- Standard Output
- Standard Error

![Redirection](https://www.codercrunch.com/image/531209810/process-streamspng)

Standard output is a place to which a program or command can send information. The information could go to a screen to be displayed, to a file or even to a printer or other devices.

Commands and programs also have a destination to send error message: standard error. By default, the shell directs standard error information to the screen for us to read, but we can change that destination if needed!

Standard input is where a program or command gets its input information from. By default, the shell directs standard input from the keyboard. The input information could come from a keyboard, a file or even from another command.

## Standard Output:
"redirection" describes the ways we can alter the source of standard input, and the destinations for standard output and standard error.

The redirection output symbol (>) tells the shell to redirect the output of a command to a specific file instead of the screen. By default, the **date** command will print the current date to the screen. If we instead run **date > output.txt** the output will be redirected to a file called output.txt.

If the output file is already exits and then you want to redirect to that file, then the previous contents will be overwritten by the new output.

```bash
ls -l /usr/sayan/bin > list.txt
sort -k5n list.txt  # -k5 stands for column no 5 and n for numeric
sort -k5n list.txt > sorted_list.txt
```

## Apending Standard Output:
When we redirect output into a file using > any existing contents in the file are overwritten. Sometimes this is not what we want. To snstead keep the existing contents in the file and add new content to the end of the file, use >> when redirecting.

```bash
echo "hello" >> greeting.txt
echo "world" >> greeting.txt
cat greeting.txt
```

## Standard Input:
To pass the contents of a file to standard input, use the < symbol followed by the filename.
```bash
command < filename
```
For example, we could pass the contents of the *chickens.txt* file to the cat command using
```bash
cat < chickens.txt
```
cat (and many other commands) are set up to accept filenames as arguments directly, but we can also redirect to standard input manually.
```bash
sort < cal.txt>
```

## Redirecting StdIn & StdOut Together:
We can redirect standard input and output at the same time! In this example, we are using *cat* to read in the contents of original.txt and then redirecting the output to a file called output.txt.
```bash
cat < original.txt > output.txt
```

## Standard Error:
By default, error messages are output to the screen, but we can change this by redirecting standard output. The standard error redirection operator is **2>**.

If you ran a command like *cat nonexistentfile* (where the file really does not exits) we would see an error printed to the screen. We can instread redirect standard error to a file with
```bash
cat nonexistentfile 2> error.txt
cat idontexist 2>> errorlog.txt
```
We can use the same >> syntax to append when redirecting standard error.

### Why 2> ?
Each stream gets its own numeric file descriptor, and for standard error the number is 2. 0 for standard input, 1 for standard output and 2 for standard error. The > operator actually defaults to using 1 as the file descriptor number, which is why we don't need to specify 1> to redirect standard output.

Similarly, the < operator uses a default file descriptor number of 0, so we don't need to specify 0< to redirect to standard input (though we can!).

## All Together:
We can redirect multiple streams at once. In this example, we are concatenating two files, redirecting standard output to a file called insects.txt, and redirecting standard error to a file called error.txt. When redirecting both standard output and standard error, make sure standard output comes FIRST. Always redirect standard error after standard output.
```bash
cat bees.txt ants.txt > insects.txt 2> error.txt
```
If we wanted to redirect both standard output and standard error to the same file, we could do this
```bash
ls docs > output.txt 2> output.txt
```
Or we could instead use **2>&1** which is a fancy syntax for saying "redirect standard error to the same location as standard output (or whatever has the file descriptor #1)"
```bash
ls docs > output.txt 2>&1
```
Newer versions of bash also supports a fancier syntax for redirecting both standard output and standard error to the same file: the **&>** notation.
```bash
ls docs &> output.txt
ls docs &>> output.txt
```