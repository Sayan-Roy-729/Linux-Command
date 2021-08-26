# Grep
## **grep** command:
The **grep** command searches for patterns in each file's contents. Grep will print each line that matches a pettern we provide.

```bash
grep PATTERN FILE
```

For example, 

```bash
grep "chicken" animals.txt
```

will print each line from the animals.txt file that contains the pattern "chicken".

### Case Insensitive:
Use the **-i** option with grep to make the search case insensitive.

```bash
grep -i "Chapter" book.txt
```

will print all matching lines from the book.txt file that contain the word "chapter" in any case.

### Word Serach:
Use the **-w** option to ensure that grep only matches words, rather than fragments located inside of other words. A word is defined by non-word characters on either side (start of the line, spaces, end of line, punctuation etc.)

```bash
grep -w "mail" book.txt
```

would match "cat" word but not "email"!

### Recursive Search:
Use the **-r** option to perform a recursive search which will include all files under a directory, subdirectories and their files and so on. If we don't specify a starting directory, grep will search the current working directory.

```bash
grep -r "chicken"
```

will search the current working directory and any nested directories for lines that contain "chicken".

```bash
grep -ri "eggplant" MealDiary/
grep -ri "parm[ae]san" MealDiary/
grep -ri "indigo" ~
```

### Other Options:
```bash
grep "myself" -ic SongOfMyself.txt  # -c counts of total matches
grep "I" -cw SongOfMyself.txt  # Used I word in the file
grep "grass" SongOfMyself.txt -iB1 # -B 1 returns the 1 before line also of matched line
grep "wagon" SongOfMyself.txt -iA1 # -A 1 returns the 1 after line also of matched line
grep "wagon" SongOfMyself.txt -A1 -B1 # Can replace -A1 -B1 with -C1 instead
grep "wagon" SongOfMyself.txt -C1 # Can replace -A1 -B1 with -C1 instead
grep "6" SongOfMyself.txt -wn # -n is for line number
grep "wagon" SongOfMyself.txt -nC1
grep "wagon" SOngOfMyself.txt -m1  # return first match, 1 for first match
grep "wagon" SOngOfMyself.txt -m5  # return 5 matches
```

## Regex:
We can provide regular expressions to **grep**. Regular expression helps us match complex patterns, but the syntax does differ from what we've seen so far.

- . - matches any single character
- ^ - matches the start of a line
- $ - matches the end of a line
- [abc] - matches any character in the set
- [^abc] - matches any char not in set
- [A-Z] - matches characters in a range
- * - repeat previous expression 0 or more times
- \ - escape meta-characters

```bash
grep "p...." SongOfMyself.txt -w
grep "^I" SongOfMyself.txt -wn
grep ")$" SongOfMyself.txt -c
grep "2[1-6]" SongOfMyself.txt -A8
grep "2[^1-6]" SongOfMyself.txt -A3
```

### Grep Extended Regex:
```bash
grep "bird" -w SongOfMyself.txt
grep "birds?" -wE SongOfMyself.txt  # -E for extended and ? will represent that "s" is optional
grep "[aeiou]{2}" -E SongOfMyself.txt
grep "[aeiou]{2,4}" -E SongOfMyself.txt
```

### Piping to Grep:
A common use case is to use **grep** to whittle down or filter a large chuck of data. In this example

```bash
ps -aux | grep hermonione
```

the **ps -aux** command will output a huge list of all processes running on our machine. We pipe that data to grep, and then filter it down to only the processes that include "hermonione". In effect, this command lets us see what hermione is up to!

```bash
man grep | grep "count"
```

In this example, we are getting the man page for grep and then piping that to the actual grep command, where we search for the string "count". Basically, it's a weired way of searching the man page.

```bash
find ~ -name "*.txt" ! -empty -type f -exec grep -l "purple" '{}' ';' # ! -empty means not empty
```