# Permissions:
## Multi-User Systems & Permissions Intro:
Unix and unix-like systems are **multiuser** operating systems. More than one person can be using the same computer at the same time (though this is tough logistically with only one display and keyboard!) Way back when, computers were crazy expensive, massive machines. A university might only have one computer, but dozens of terminals sprinkled across campus.

### Permission Denied?!
As regular users, we do not have permission to write or even read every file on the machine. For example, if I try to read the file "/etc/sudoers" using "cat /etc/sudoers" I get a "permission denied" message.

## Groups:
On unix systems, a single user may be owner of files and directories, meaning that they have control over their access. Additionally, users can belong to groups which are given access to particular files and folders by their owners.

When printing out by the command "ls -l", the first (actually the 3rd column) is the owner of that files or folders and the second (actuall the 4th column) is the group owner.

## File Attributes:
The weired looking 10 characters we see printed out first are the file attributes.

```bash
-rw-rw-r--
```

These characters tell us the type of the file, the read, write and execute permissions for the file's owner, the fiel's group owner, and everyone else.

### File Type:
The very first character (**-rw-rw-r--** or **drwxr-xr-x**) indicates the type of the file. Some of the common types and their corresponding attributes are:

- "-" for regular file
- "d" for directory
- "c" for character special file
- "l" for symbolic link
- "b" for block special files

### Understanding Permissions:
We saw first character of the 10 characters. And rest 9 characters represent the permission. 

![permission](https://cdn.thegeekdiary.com/wp-content/uploads/2017/11/Files-permissions-and-ownership-basics-in-Linux.png)

The first 3 chunk tells the permissions of the owner. Next second 3 chuck tells the permissions of the group owner and last 3 chunk characters tell the premissions for world (every-one else).

The first letter of the 3 chunk letters are always **read permission**. Then 2nd and 3rd character is always **write permission** and **execute permission** respectively.

| Character | Effect on Fiels | Effect on Directories |
| :-- | :-- | :-- |
| r | file can be read | directory's contents can be listed |
| w | file can be modified | directory's contents can be modified (create new files, rename files/folders) but only if the executable attribute is also set |
| x | file can be treated as a program to be executed | allows a directory to be entered or "ed"ed into |
| - | file cannot be read, modified, or executed depending on the location of the - character | directory contents cannot be shown, modified or cd'ed into depending on the location of the - character |

## Change Permissions:
### **chmod** command (Symbolic Notation):

| Type | Owner | Group | World |
| :-- | :-- | :-- | :-- |
| d | rwx | --x | --- |

In the above example, we see that the directory's owner can enter the directory, rename and remove files from within the directory. Members of the owner group can enter the directory but cannot create, delete or rename files. To change the permissions of a file or directory, we can use the **chmod** command (change mode). To use chmod to alter permissions, we need to tell it:

- **Who** we are changing permissions for
- **What** change are we making? Adding? Removing?
- **Which** permissions are we setting?

```bash
chmod mode file
```

When specifing permissions with chmod, we use a special syntax to write permission statements. First, we specify the "who" using the following values:
- **u** - user (the owner of the file)
- **g** - group (members of the group the file belongs to)
- **o** - others (the "world")
- **a** - all of the above

Next, we tell chmod "what" we are doing using the following characters:
- **-** (minus sign) removes the permission
- **+** (plus sign) grants the permission
- **=** (equals sign) set a permission and removes others

Finally, the "which" values are:
- **r** - the read permission
- **w** - the write permission
- **x** - the execute permission

| Before | After | Command | Description |
| :-- | :-- | :-- | :-- |
| -rw-r--r-- | -rw-rw-r-- | chmod g+w file.txt | Add write permissions to the group |
| -rw-rw-r-- | -r--r--r-- | chmod a-w file.txt | Remove write permissions from all | 
| -rw-rw-r-- | -rwxrw-r-- | chmod u+x file.txt | Add executable permissions for owner |
| -rwxrwxr-- | -r--r--r-- | chmod a=r file.txt | Set permissions to read only for all |

### Octal Notation with **chmod**:
**chmod** also supports another way of representing premission patterns: octal numbers (base 8). Each digit in an octal number represents 3 binary digits.

| Octal | Binary | File Mode |
| :-- | :-- | :-- |
| 0 | 000 | --- |
| 1 | 001 | --x |
| 2 | 010 | -w- |
| 3 | 011 | -wx |
| 4 | 100 | r-- |
| 5 | 101 | r-x |
| 6 | 110 | rw- |
| 7 | 111 | rwx |

| Binary | Permission | Command |
| :-- | :-- | :-- |
| 111101101 | rwxr-xr-x | chmod 755 file.txt |

### **su** command (Substitude user):
There may be times we want to start a shell as another user, from within our own shell session. We can use the **su** command to do just that.

```bash
su - hermione
```

For example, the above command would create a new login shell for the user hermione. We would need to enter Hermione's password. To leave the session, type **exit**.

### Super special **root** user:
In Linux systems, there is a super user called **root**. The root user can run any command and access any file on the machine, regardless of the file's actual owner. The root user has tons of power and could easily damage or even destroy the system by running the wrong commands! For this reason, Ubuntu locks the root user by default.

#### **sudo** command:
Even if the root user is locked by default, we can still run specific commands as the root user by using **sudo** command. Individual users are granted an "allowed" list of commands they can run as the super user.

```bash
sudo -l
```

By default, Ubuntu disables logins to the root account. Instead, the initial user is granted full access to all superuser priveleges: "User sayan may run the following commands: (ALL : ALL) ALL". Subsequent users won't have full sudo privileges by default, but the original user can grant them.

Run the above command to see the permitted commands for your particular user. To run a command as the root user, prefix it with sudo. You will then need to enter the password for **your account**. For example to update Ubuntu, I would need to run **apt update**. However, I can't do this as my "regular" user, as it's something that impact all users. Instead, I need to run the command as the root user using

```bash
sudo apt update
```

### **chown** command:
The **chown** command is used to change the owner and/or the group owner of a specific file or directory.

```bash
chown USER[:GROUP] FILE(s)
```

To make bojack the owner of the file.txt, we would run

```bash
chown bojack file.txt
sudo chown kitty PropertyOfKitty.txt
```

To only change the group owner of a file, we can run **chown :GROUP FILE**. For example,

```bash
chown :horses file.txt
```

 will change the file group owner of file.txt to the group named hourses.

 To change the owner of a file and the file group owner at once we can provide both using **chown USER:GROUP FILE**. For example

 ```bash
 chown bojack:horses file.txt
 ```

 will change the owner of file.txt to bojack and changes the file group owner to the group named horses.

 ### groups:
 To view the groups that a given user belongs to, run **groups USERNAME**. For example, to see which groups hermione is part of, run

```bash
groups hermione
```

We can create new groups using the addgroup command. To create a new group called friends, we would run

```bash
sudo addgroup friends
```

To add a user to a group, use the **adduser** command. To add hermione to friends, we would run 

```bash
sudo adduser hermione friends
```

[Note: Don't screw around with groups unless you know what you are doing!]