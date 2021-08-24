## Delete files (**rm**):
We use the remove (rm) command to remove files from our machine. Syntax of this command is
```bash
rm <filename>
```
For example, **rm app.js** would remove the app.js file. *Note: rm command deletes files, there is no undo or recycling bin to retrieve them from! They are gone!*\
You can remove multiple files and each of them should have to space separated.
```bash
rm file1 file2 file3
```
You can use relative path or absolute path to delete.\

## Delete Directories:
![delete directory](https://assets.telegraphindia.com/telegraph/2020/Sep/1600593720_1shutterstock_406413301.jpg)

To delete empty folders, we need to use the **-d** option with **rm**. For example, below command would remove the cats directory (only if it's a already empty)\
```bash
rm -d cats
```
To delete folders that are not empty, use the **-r** option.
```bash
rm -r chickens
```
The above command would delete the chickens directory whether it's empty or not. *You definitely want to be careful when deleting directories!*\
If you want to prompt before deleting the folders, add one extra option **-i**. For yes, type **y** and for no, type **n**.
```bash
rm -ri Chickens/
```

## Moving Files/Folders:
Use the move command (**md**) to move files and directories from one location to another. The *source* and *destination* should exist.\
```bash
mv <source> <destination>
```
When we specify a file or files as the source and a directory as the destination, we are moving the files into the directory.\
For example, below command will move the app.css file into the styles directory.
```bash
mv app.css styles/
```
You can also move multiple files at a time.
```bash
mv file1 file2 file3 file4 ~/Desktop/
```
Now let's assume there is a directory named *Cats* inside your current directory. Now you want to move into *Cleanup* directory (let's assume it's exits.)
```bash
mv Cats/ Cleanup/
```

## Rename files & folders using *mv*:
We can also use the move command to rename files and folders. We can move multiple files or folders at a time but can't change the name of multiple names at a time.
```bash
mv <current> <new_name>
```
If we specify a single file as the source and a single file as the destination, it will rename the file. For example, to rename the chickens.txt file to roosters.txt, we could run
```bash
mv chickens.txt roosters.txt
```
If we specify a single folder as the source and the destination doesn't yet exist, it will rename the folder. If the destination folder exist, it will move our source folder into the destination.

## Copying With **cp**:
We can use the copy command to create copies of files and folders.
```bash
cp <source> <destination>
```
To create a copy of sheep.txt called dolly.txt, we could run
```bash
cp sheep.txt dolly.txt
```
To copy multiple files into another directory, use
```bash
cp file1 file2 directory
```
