# Expansion:
## Pathname expansion:
The echo command is very simple. It simply displays text that we pass to it. We'll be using it to demonstrate some concepts in this section.

```bash
echo "hello"
```

It's particularly useful in shell scripts (we cover them later), when we want to output something to the screen from within a file.

### Wildcard Characters (aks globbing patterns) (*):
We can use special wildcard characters to build patterns that can match multiple filenames at once. The asterisk (*) character represents zero or more characters in a filename. For example

```bash
ls *.html
```

will match any files that end with .html like index.html and navbar.html.

```bash
cat blue*
```

will match any files that start with "blue" like "blue.html" or "bluesteel.js". We can use multiple times

```bash
ls -l *at*
```

### The ? Wildcard:
The question mark (?) character represents any single character.

```bash
ls app.??
```

will match any files named "app" that end with two character file extensions like "app.js" or "app.py" but not "app.css".

```bash
ls pic?.png
```

will match pic1.png, pic2.png, pic3.png but also picA.png or picx.png.

```bash
echo *.???
mv app?.css Styles/
```

## Range Wildcards ([]):
Inside of square brackets ([]) we can specify a range of characters to match.

```bash
ls pic[123].png
```

will only match pic1.png, pic2.png and pic3.png.

```bash
ls file[0-9]
```

will match file1, file2, file3 upto file9.

```bash
ls [A-F]*
```

will match any files that begin with a capital A, B, C, D, E or F.

### Negating Ranges:
Inside of square brackets ([]) we can specify a range of characters to not match, using a caret (^)

```bash
ls [^a]*
```

will match any files that do not start with "a"

```bash
ls [^0-9]*
```

will match any files that do not start a numeric digit (0-9)

## Tildy Expression:

```bash
echo ~sayan
```

## Magic of Brace Expansion:
Brace expansion is used to generate arbitrary strings. Basically, it will generate multiple strings for us based on a pattern. We provide a set of strings inside of curly braces ({}), as well as optional suttounding prefixes and suffixes.

The specific strings are used to generate all possible combinations with the optional prefixes and suffixes.

```bash
touch page{1, 2, 3}.txt
touch {Mon,Tue,Wed,Thu,Fri}_{AM,PM}.txt
```

For example, the above command will generate three new files: page1.txt, page2.txt and page3.txt.

We can provide a numeric range, which will be used to generate a sequence. In this example,

```bash
mkdir jan{1..31}
```

will be expanded to jan1, jan2, jan3 etc until jan31.

We can provide a third value which defines the interval for the range. In this example,

```bash
echo {2..10..2}
```

will print out the numbers 2, 4, 6, 8 and 10.

We can even specify alphabeticval ranges. This example

```bash
touch group-{a..e}.txt
```

generate the files group-a.txt, group-b.txt, group-c.txt, group-d.txt and group-e.txt. We can also use nested braces as well.

```bash
echo {x, y{1..5}, z}
```

## Arithmatic Expansion:
The shell will perform arithmetic via expansion using the 

```bash
$((expression))
```
syntax, inside the parathenses, we can right arithmetic expressions using:

- + addition
- - subtraction
- * multiplication
- / division
- ** exponentiation
- % modulo (remainder operator)

```bash
echo $((10+7))  # 17
echo $((3*13))  # 39
echo $((10/3))  # 3
```

[Note: The shell only performs integer arithmetic, so the result is always a whole number]

## Quoting:
In this example, our large whitespace is ignored because the shell performs something called word splitting.

```bash
echo look at                  me
```

In this example, we only see "holy" printed out because the shell thinks we are referencing a variable called hit. It can't find a value of hit, so it substitutes an empty string instead.

```bash
echo holy $hit
```

If we wrap text in double quotes, the shell will respect our spacing and will ignore special characters except for dollar sign ($), backslash (\) and backtick (`). Pathname expansion, brace expansion and word splitting will be ignored. However, command substitution and arithmetic expansion is still performed because dollar signs still have meaning inside double quotes.

```bash
echo "look at                me"
echo "{1..9"}
```

Use single quotes to suppress all forms of substitution.

```bash
echo "$((2+2)) is 4"  # 4 is 4
echo '$((2+2)) is 4'  # $((2+2)) is 4
```

## Command Substitution:
We can use the $(command) syntax to display the output of another command. For example,

```bash
echo "today is $(date)"
```

will print "today is Wednesday 25 August 2021 11:12:36 AM IST".

```bash
echo today is `date`  # today is Wednesday 25 August 2021 11:15:46 AM IST
```
