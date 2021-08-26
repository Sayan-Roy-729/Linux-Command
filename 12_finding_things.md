# Finding Things:
## **locate** command:
The **locate** command performs a search of pathnames across our machine that match a given substring and then prints out matching names. It is nice and speedy because it uses a pre-gererated database file rather than searching the entire machine. For example

```bash
locate chick
locate Planner/Mon
```

will perform a search for all files that contain "chick" in their name.

```bash
locate bin/less???
```

The "-e" option will only print entries that actually exist at the time locate is run. The "-i" option tells locate to ignore casing. The "-l" or "--limit" option will limit the number of entries that locate retrieves.

```bash
locate -il10 /PLANNER/
```

To update the database of the machine, execute

```bash
sudo updatedb
```

## **find** command:
The locate command is nice and easy, but it can only do so much! The **find** command is far more powerful! Unlike locate, find does not use a database file. By default, **find** on its own will list every single file and directory nested in our current working directory. We can also provide a specific folder.

```bash
find friends/
```

would print all the files and directories inside the "friends" directory (including nested folders.)

```bash
find | wc -l
```

### finding by type:
We can tell find to only find by file type: only print files, directories, symbolic links etc using the **-type** option.

- **find -type f** will limit the search to files.
- **find -type d** will limit the search to directories.

### finding by name
We can provide a specific pattern for find to use when matching filenames and directories with the **-name** option. We need to enclose our pattern in quotes.To find all files on our Desktop that end in the .txt extension, we could run

```bash
find ~/Desktop -type f -name "*.txt"
```

Use the **-iname** option for a case insensitive search.

```bash
find ~ -type f -iname "*chick*"
find ~ .name "*[0-9]*"
```

### finding by size
We can use the **-size** option to find files of a specific size. For example, to find all files larger than 1GB we could run

```bash
find -size +1G
```

To find all files under 50MB, we could run

```bash
find -size -50M
```

To find all files that are exactly 20KB, we could run

```bash
find -size 20k
```

### finding by owner:
We can use the **-user** option to match files and directories that belong to a particular user.

```bash
find -user sayan
```

### find empty files or folders:
```bash
find -empty
```

### Timestamps:
- **mtime** or modification time, is when a file was last modified AKA when its contents last changed.
- **ctime** or change time, is when a file was last changed. This occurs anytime mtime changes but also when we rename a file, move it or alter permissions.
- **atime** or access time is updated when a file is read by an application or a command like cat.

```bash
ls -l  # shows mtime
ls -lc  # shows ctime
ls -lu  # shows atime, not -la, -a shows hidden files
```

```bash
touch last_week -d "1 week ago"  # check by ls -l
touch last_month -d "1 month ago"  # check by ls -l
touch three_days_ago -d "3 days ago"  # check by ls -l
touch 10_mins_ago -d "10 minutes ago"
touch 30_mins_ago -d "30 minutes age"
```

```bash
find -mmin +30  # + means greater than 30mins mtime changed
find -mmin -30  # - means less than 30mins ago mtime changed
find -amin -10  # find atime ago file
find -cmin 60
find -atime 4   # File was accessed 4*24 hours ago
find -mtime -5
find -mtime +10
find -ctime +10
```

### Logical Operators:
We can also use the **-and**, **-or** and **-not** operators to create more complex queries.

```bash
find -name "*chick*" -or -name "*kitty*"
find -type -f -not -name "*.html"
```

### User- Defined Actions:
We can provide **find** with our own action to perform using each matching pathname. The syntax is

```bash
find -exec command {} ;
```

The {} are a placeholder for the current pathname (each match), and the semicolon is required to indicate the end of the command.

```bash
find ~ -type f -empty -exec ls {} ;
find -name "*broken*" -exec rm '{}' ';'
```

To delete every file that starts with contains "broken" in its file name, we could run the above last command. Note that we need to wrap the {} and ; in quotes because those characters have special meaning otherwise. To delete the files in this way have to be very careful. For that can use **-ok** option.

```bash
find ~ -type f -empty -ok ls -l '{}' ';'
```

```bash
find -type f -user sayan -exec ls -l '{}' ';'
```

The above example finds all files that are owned by the user 
"sayan", and then it lists out the full details for each match using ls -l. Note that we need to wrap the {} and ; in quotes because those characters have special meaning otherwise.

```bash
find -type f -name "*.html" -exec cp '{}' '{}_COPY' ';'
```

The above example finds all files that end with .html. It then creates a copy of each one using cp command. Each of the copies ends with "_COPY" so we end up with files like "index.html_COPY" and "navbar.html_COPY". Note that we need to wrap the {} and ; in quotes because those characters have special meanings otherwise.

### **xargs** command:
When we provide a command via **-exec**, that command is executed separately for every single element. We can instead use a special command called **xargs** to build up the input into a bundle that will be provided as an argument list to the next command.

```bash
find -name "*.txt" -exec ls '{}' ';'
find -name "*.txt" | xargs ls
echo hello world | xargs mkdir
```

This example finds four individual chapter files (chapter1, chapter2, chapter3 and chapter4) and then passes them to the cat command, which then outputs the combined contents to a file called fullbook.txt.

```bash
find -name "chapter[1-4].txt" | xargs cat > fullbook.txt
```