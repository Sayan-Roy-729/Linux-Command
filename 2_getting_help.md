## man pages:
The **man pages**, short for manual pages, are a built-in form of documentation available on nearly all UNIX-like operating systems.

The specific contents vary from one operating system to another, but at a bare minimum, the man pages include information on commands and their usage. To read the specific piece of documentation associated with a given command, run **man command**.

For example, to learn more about the ncal command we could run **man ncal**. This displays a bunch of information on ncal that we can scroll through. Type "q" to exit and use arrow keys to scroll the terminal page.

## Navigating & Searching A man page:
Sometimes many man pages of commands are longer and some are short. To move from one page to another, press the *spacebar* key of the *F* key and there we go. One page is the content are can display the content of the man page at the time of your terminal. And press the *B* key to go back one page.
- **Spacebar** or **f** key to move forward one page
- **b** key to move back one page
- **h** key for help

Now, one question, What is the purpose of command **ncal -w**?

Execute the commands one by one
- **man ncal**
- **/** (press the forward slash)
- Type **-w** and hit enter

## man pages contents
In general, each man page will follow this pattern:
- The title/name of the command with a short explanation of its purpose
- Synopsis of the command's syntax
- Description of all command options.

## man pages synopsis:
**ncal [-31bhJeoSM] [-A number] [-B number] [-d yyyy-mm] [year]**
Anything listed inside of square brackets is optional. The only required part is **ncal**.

The above synopsis for ncal tells us that we can use the following options without providing any sort of additional parameter: -3, -1, -b, -h, -J, -e, -o, -S, and -M. To keep things brief, they are all lumped together as [-31bhJeoSM].

Then, we see other options in square brackets followed by their expected parameters: [-A number] means the -A option expects a number. [-d yyyy-mm] indicates that the -d option expects us to pass in a date in the format: yyyy-mm like 1980-04.

Finally, in the end, we see [year] which means that we can pass a year as a parameter.

**echo [OPTION]...[STRING]...**

The above synopsis is for the **echo* command, which echoes text back at us. All allipsis (...) indicate that one or more of the proceeding operands are allowed:
- [OPTION]... means that we can pass more than one option to echo
- [STRING]... indicates that we can pass multiple strings to echo. For example, we can run **echo hello** and also **echo hello there you cutie little chicken pot pie**.

**cp [OPTION]... SOURCE DEST**

So far, all of the operands we have seen have been optional, but some commands do require certain arguments in order to run. In a man-page synopsis, required operands are not wrapped in square brackets.

In the above synopsis for the copy (cp) command, we see that we can optionally provide one or more options. **SOURCE** indicates that we must pass one source, and **DEST** indicates that we must pass a destination as well. Those two arguments are required.

## Manual Sections:
The manual is broken into 8 different sections:
- User Commands
- System Calls
- C Library Functions
- Special forms
- Games
- Miscellaneous
- System admin commands

## Types of Commands:
There are really four types of commands:
- An executable program, usually stored in /bin, /usr/bin, or /usr/local/bin. These are compiled binary files (hence bin)
- A built-in shell command. These commands are part of the shell (bash in our case)
- A shell function
- An alias

```bash
type command
```
The type command will tell us the type of a command.

## Which:
To find the exact location of an executable, run **which command**. This only works for executables, not built-in shell commands or aliases.
```bash
which command
```

## Help Command:
We will learn the command **cd**. For the manual page, type
```bash
man cd
```
And you will get **No manual entry for cd**. **cd** is a built-in shell command and that's why there is no manual entry. But we need some help with this command. For that, we can **help**. We can find documentation for those commands using the **help** command. For example, to learn more about the **cd** command we would run
```bash
help cd
```
