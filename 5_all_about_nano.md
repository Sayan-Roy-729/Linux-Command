---
title: 'Navigate Between Folders'
date: '2022-10-16'
image: basic-command-nomenclatures.jpg
excerpt: We will learn all about command structures look like as well as arguments and options. We also learn combining options and long form options and when what have to use! Also learn some commands.
category: linux-commands
isFeatured: false
---

## nano
![nano text editor](https://tecnstuff.net/wp-content/uploads/2019/08/install-use-nano-text-editor.jpg)\
nano is a simple text editor that we can access right from terminal. it's far accessible than other popular command-line editors like vim and emacs.\
nano includes all the basic text editing functionality you would expect: search, spellcheck, syntax highlighting ect.
Learn all about the nano from the commands manual page.
```bash
man nano
```

## Basics of Nano:
To open up a file using nano, run **nano FILE**. For example, to open up the file book.txt using nano, we would run
```bash
nano book.txt
```
We can also use the same command to edit a file that doesn't yet exit (we can then save it and create the file).\
Edit some text inside the file. After changing, the contents have to save. To save, watch out bellow section where some instructions are there. From there, one is **Write Out** and the short cut is **^O**. **^** means commands or ctrl key in keyboard. If you press those together, you can modify the name of the file. Simply press enter and the documents will be saved. You can also save the file using **ctrl + S**\
To exit from the editor, press **ctrl + X**.

## Editing With Nano:
Some editors like vim require us to enter "write mode" before we can start editing f file, but with nano we can make changes right away.\
We can move the cursor using the arrow keys.\
At the very bottom, we'll see a **list of shortcuts** that we can use inside of nano. These are super useful!\
- press **esp** and then **/** (forward slash) to go to the last line of the content.
- press **esp** and then **\** (back slash) to go to the first line of the content.
[Note: For my case, **esc** is my meta key of my machine. If you have different one, use that!]

## Searching & Replacing in Nano:
In this nano editor, the long text lines is not auto-wrapped by-default. To enable this press **esc** (**esc** is the meta key. Iy you have different, then press that.) key and press **shift-4** or **$** and the soft wrapping mode will be on.\

Use **ctrl-W** and then enter a search phrase to search forward in the file from your current cursor location. Enter what you want and press enter. The first match will be highlighted. If you hit enter again, you can found next one and so on.\

This is not case sensitive. To toggle the case sensitive, below of the editor there is a short cut you can see **Case Sens**. The short cut of this is **M-C** and **M** stands for meta key. Press that and can toggle case sensitiveness.\

To search and replace, use **ctrl** and **back slash** together and then enter the word you want to replace. Then enter the replacement and decide where to replace specific matches or all matches.

## Configuring Nano & Spellchecking:
We can use spellchecking inside of Nano, but we have to enable it first in the Nano config located at **/etc/nanorc**. Open the file using nano but you can't change the content because **permission denied**. We will learn about the permissions later. For now execute below command
```bash
sudo nano /etc/nanorc
```
Now search the words **spell** and you can find the part of the spell check. Now change to the below settings
```bash
set speller "aspell -x -c"
set suspend
```
After that save the file and exit. Now below there are many short cuts and one of them is **To Spell** and the short cut is **^T**. After that you can check the spellings. You can use this spell checker though it is not best spell checker though.