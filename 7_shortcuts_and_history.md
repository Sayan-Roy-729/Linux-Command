---
title: 'Navigate Between Folders'
date: '2022-10-16'
image: basic-command-nomenclatures.jpg
excerpt: We will learn all about command structures look like as well as arguments and options. We also learn combining options and long form options and when what have to use! Also learn some commands.
category: linux-commands
isFeatured: false
---

## Shortcuts:
We can speed up our command-line experience by taking advantage of the many built-in shortcuts.\

These shortcuts are designed so that your hands never have to leave your keyboard "home base".\

They take a little bit of practice to get comfortable with, but it's worth the effort!

## Clearing:
Use **ctrl-l** to clear the entire screen. This is the shortcut of the command **clear**.

## Line Jumping:
Use **ctrl-a** to move the cursor to the beginning of the line.\
Use **ctrl-e** to move the cursor to the end of the line.

## Moving Characters:
Use **ctrl-f** to move the cursor forward one character at a time (same as the right arrow).\
Use **ctrl-b** to move the cursor backwards one character at a time (same as the left arrow).

## Jumping Words:
Use **alt-f** to move the cursor forward one word.\
Use **alt-b** to move the cursor backwards one word.

## Swapping:
use **ctrl-t** to swap the current character under the cursor with the one preceding it. This can be useful to correct typos made by typing to quickly! And to swap the words use **alt-t**.

## Killing The Line:
Use **ctrl-k** to kill the text from the current cursor location until the end of the line. --->\
Use **ctrl-u** to kill the text from the current cursor location to the very beginning of the line <---\

## Killing a Word:
Use **alt-d** to kill the text from the current cursor location through the end of the word ---> \
Use **ctrl-w** or **alt-delete** to kill the text from the current cursor through the beginning of the word <--- \

## Reviving Text (Yanking):
When we kill text using commands like ctrl-k, ctrl-u, alt-d and alt-backspace, the "killed" text is stored in a memory in an area known as the "kill-ring".\
We retrieve the most recently killed text using **ctrl-y**.

## History:
Bash keeps a record the command we have previously entered. We can see the actual file at **~/.bash_history**.\
You can scroll through the history one command at a time using the up and down arrows.\
We can also use **history** command to view the entire history, though it's generally easier to manage if we pipe the output to less.
```bash
history
history | less
```

## History Expansion:
We can easily re-run an earlier command if we have its line number from the history.\
For example, to run the 73rd command in the history, we could run
```bash
!73
```
So the syntax is
```bash
!somenumber
```

## Searching History:
Often it's easiest to find an earlier command by searching using a small portion of the command that you remember.\
Type **ctrl-r** to enter "reverse-i-search". As you start typing, bash will search the history and show you the best match.\
Hit ctrl-r to cycle through potential matches.