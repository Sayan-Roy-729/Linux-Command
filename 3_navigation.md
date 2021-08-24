---
title: 'Navigate Between Folders'
date: '2022-10-16'
image: basic-command-nomenclatures.jpg
excerpt: We will learn all about command structures look like as well as arguments and options. We also learn combining options and long form options and when what have to use! Also learn some commands.
category: linux-commands
isFeatured: false
---

This is all about the navigating the file system and folder structure on your machine using terminal.

## Root Directory:
The starting point for the file system is the root folder or directory. We can call it the root, but its actually directory name is "/". All other folders are inside this directory.\

![root directory](https://www.lifewire.com/thmb/t6yngduVCuJAbeGHTZFa2DQIWNI=/2200x1237/smart/filters:no_upscale()/What-is-a-root-folder-or-root-directory-2625989-aafb8d25a54146879a236236ab8ea6c0.png)
\
Confusingly, there is a sub-directory named **root**. These are not the same! You can't open the root / directory directly using the graphical user interface but can do using the command.

```bash
xdg-open /
```

Here many folders you can see with which you don't need any interaction. But in mac os, there is a folder / and you can navigate to that folder.

## Home Directory:
**/home** contains a home folder for each user on the system. For example, if there is an user named *user1* then inside the home folder, there will be another folder named *user1*. If your computer has 3 users, then there will be 3 folders and if not, only one folder for the one user. Inside that user folder, all other stuffs and files will be stored related to that user.\

Open the home directory using command line:
```bash
xdg-open ~
```

## **pwd** command:
This is out first command for navigation. The **pwd** or **print working directory** command is super simple but very useful. Think of it as a "where am I" command.\

It will print the path of your current working directory, starting from the root /.
For example, if I were on my desktop and I ran pwd, I would see */home/user1/Desktop*.
```bash
pdw
```

## **ls** command:
The list command will list the contents of a directory. When used with no options or arguments, it prints a list of the files and folders located in the current directory. 
```bash
ls
```
We can also list the contents of a specific directory using **ls path**. For example, below command will print the contents of the /bin directory.
```bash
ls /bin
```
You can see the folder names in bolder as well as in different color other than the files names.

## ls options:
The ls command accepts a ton of options. Two of the more commonly used are **-l** and **-a**\
**-l** (lowercase L) prints in long linting format. It shows far more information about each file/folder.
```bash
ls -l
```
The **-a** option will also list any hidden files that begin with. These are normally not listed.
```bash
ls -a
```
We can combine these two options! This example prints detailed information for all files, including hidden files. All the hidden folders are started with a dot (.) at the beginning of that folder name.
```bash
ls -la
```
You can read more about the **ls** command using
```bash
man ls
```

## Changing Directories With **cd**:
The **cd** command is used to change the current working directory, "moving" into another directory.\
For example... **cd chickens** would change into the chickens directory (assuming it exits). The command is
```bash
cd <directory>
```
The below command would take me my home directory.
```bash
cd ~
```
Another example, from your /home/user directory, execute below command
```bash
cd Desktop
```
Thus you can navigator to any directory to your machine. Sometimes you can get *permission denied* error. That will learn later.\
In Unix-like operating systems, a single dot (.) is used to represent the current directory. Two dots (..) represent the parent directory.\
So we can use below command to move up one level, from our current directory into the parent directory.
```bash
cd ..
```

## Relative vs Absolute Path:
![relative vs absolute path](https://linuxhandbook.com/content/images/2021/04/absolute-vs-relative-path-linux.png)
When providing paths to commands like cd or ls, we have the option of using relative or absolute paths.\
Relative paths are paths that specify a directory/file relative to the current directory. For example, if our current directory is **/home/user1** and we want to cd into animals folder (let's assume, it exits), we can simply run 
```bash
cd animals
```
However, **cd animals** does not work if we are located in another directory like **/bin**. The relative path from /bin is **../home/user1/animals**.\
Absolute paths are paths that start from the root directory (they start with a /). The absolute path to the animals directory is /home/user1/animals. We can absolute paths to specify a location no matter our current location.\
For example, from the /bin directory I could use below command to change into the animals directory from any location.
```bash
cd /home/user1/animals
```
or
```bash
cd ~/animals
```