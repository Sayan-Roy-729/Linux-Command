## **ncal**:
Try typing ncal into your prompt and hit enter. You should see the current month's calender printed out.\
ncal stands for "new cal". There is also "cal" command that does the same exact thing, but ncal adds some fancier functionality.

## Command Structure:
```bash
command -options arguments
```
Most commands support multiple options that modify their behavior. We can decide which options to include, if any, when we execute a command.\
Similarly, many commands accept arguments (the things that the command acts upon or user.)

### Arguments:
The term "arguments" and "parameter" are often used interchangeably to refer to values that we provide to commands.\
The *echo* command is extremely simple. It takes the arguments we provide to it and prints them out. It echoes them back at us.
```bash
echo speedkode
```
The ncal command accepts values to control the specific month(s) and year it displays.\
If we specify only a year, ncal will print out the calendar for that entire year.
```bash
ncal 2021
```
If we specify a month and a year, ncal will print only that month's calender.
```bash
ncal july 1999
```
Here, the order matters. If you first give the value of the year and then the month, you will get an error.\
The **sort** command, which we will cover in depth later, accepts a filename. It prints out the sorted contents of that file. For example, *sort colors.txt* prints out each line of the colors.txt file, sorted in alphabetical order.

### Options:
Each command typically supports a host of options that we can choose to use when executing the command. These options modify the behavior of the command in predefined ways. Options are prefixed by a dash, as -h or -3.\
Example: By-default, the ncal command highlights today's date in the output. We can provide the -h option to turn off the highlighting of today's date.
```bash
ncal -h
```
The **-j** option tells ncal to display a calender using Julian days (days are numbered staring from jan 1st).
```bash
ncal -j
```
The options are cate sensitive, some commands lower case options and some does upper case.\
We can provide the **-M** option to tell ncal to use Monday as the first day of the week instead of Sunday.
```bash
ncal -M
```
The **-3** option tells ncal to display the previous, current and next month.
```bash
ncal -3
```
### Combining Options:
We can provide multiple options at once. This example uses the **-3** option to display the previous, current and next month & the **-h** option to turn off the highlighting of the current date.
```bash
ncal -3 -h
```
When we provide multiple options to a single command, we can use a shorted syntax where we only need a single dash (-) character.
```bash
ncal -3hMj
```

### Long Form Options:
All these short one-character options can get confusion! Some options also support equivalent long format options that are usually full words and are prefixed with two dashes instead of just one.\
For example, the **date -u** option is used to print the date in Coordinated Universal Time (UTC). We can instead use **date --universal** to accomplish the same end result.
```bash
date -u
date --universal
```
Here's another example using the sort command. The **sort -r** option will sort a file contents in reverse. If we prefer, we can use the longer form **sort --reverse** to accomplish the same thing.
```bash
sort -r colors.txt
sort --reverse colors.txt
```
To use multiple long-form options in a single command, we must write them out separately with their own dashes (--). We cannot combine long-form options in the same way we can with single character options.
```bash
sort --reverse --unique colors.txt
```

### Options With Parameters:
Some options require us to pass an additional value. For example, ncal's **-A** option is used to display a certain number of months after a specific date. We need to tell it how many months to display.\
In this example, **ncal -A 1** prints out the current month with one month afterwards.
```bash
ncal -A 1
```
Note: this can also be written as **ncal -A1** (no space between A and 1).\
There is also a -B option to print a number of months before the specific date. We need to pass it a number of months. In this example, **ncal -B2** prints out the current month with the two previous months.
```bash
ncal -B2
```
This example uses both -A and -B options to print out 1 month before the current month and one month after.
```bash
ncal -A1 -B1
```

### All Together Now:
This example prints out the calendar for July 1969, with one month before (june) and two months after (august and september).
```bash
ncal -B1 -A2 july 1969
```