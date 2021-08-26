# Writing Our Own Commands:
## Bash Scripting:
The basic Steps:
- Write a script in a file and save it
- Make the script executable using chmod
- Verify that shell can find your script

### Shebang!
The first line of our script should read **#!/bin/bash**. The **#!** is called the shebang, and it's used to tell the OS which interpreter it should use when parshing this file. We want ours to say "use bash to interpret this file!". After the shebang, we need to include the path to the Bash binary. This is not Bash specific. If we wanted to write a python script, we would include the path to the python binary.

### Comments
Lines that begin with # will not be read by the shell. Write comments to explain particularly tricky bits of code or to leave notes for yourself.
**# my first script**

### The good stuff:
We can write any of the commands that we normally run from the command line. When we execute the script, these commands will run! **echo "hello there!"**

If we put together, then

```bash
#!/bin/bash
# my first script
echo "hello there, $USER"
echo "Today is $(date)"
echo "last ran at $(date)" >> file.log
```
