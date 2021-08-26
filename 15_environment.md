# Environment:
## Environment and Variables:
The shell maintains a set of information during a shell session, known as the **environment**. It's just a series of key-value pairs that define properties like:

- Your home directory
- Your working directory
- The name of your shell
- The name of the logged in user

## Viewing the Environment:
Use the **printenv** command to view the environment variables and their current values. Because there are quite a few values, it can be useful to pipe the output to less.

```bash
printenv
printenv | less
```

## Parameter Expansion:
If we write out the name of an environment variable prefixed with a dollar sign ($), the shell will replace it with the actual value. For example,

```bash
echo $USER
```

results in the USER variable's value.

## Define Variables:
To define a variable, use the syntax **variable=value**. Built-in variables are upper-cased, so it's a common convention to lowercase custom variables to pevent confusion.

```bash
color="purple"  # These are shell variables, not environment variables
num=821  # and only exists on current shell session
bash  # new session, previous shell variables are gone but not env vars
export animal=mandrill  # new environment variable, but other shell can't use for now
```

## Startup Files:
Usually the user and pwd as shown when to enter the new command like "sayan@ubuntu:-$". You can change this by

```bash
PS1="type something... "
bash # for new startup session, you will loose this customization
```
For non-login sessions (typical session when you launch the terminal via the GUI):
- **etc /bash.bashrc** - global config for all users
- **/.bashrc** - specific settings for each user. This is where we can define our own settings and configuration. 

When we log in, the shell reads information from startup files. First, the shell reads from global config files that effect the environment for all users. Then, the shell reads startup files for specific users. The specific files the shell reads from depends on the type of session: login vs non-login shell sessions.

For login sessions:
- /etc/profile - global config for all users
- ~/.bash_profile - user's personal config file
- ~/.bash_login - read if bash_profile isn't found
- ~/.profile - used if previous two aren't found.


## Customizing Your Prompt:
For details go to the manual page of bash.

```bash
man bash # search prompting
PS1='\u:\@:\w ->' # \u - username, \@ - current time, \w - pwd
```
For color and other customization test, can use this website --> https://ezprompt.net/

## Aliases:
We can define our own commands using the **alias** keyword.

```bash
alias ll='ls -al'
```

In the example to the right, we are defining an alias called **ll** which is equivalent to running **ls -al**. To execute it, we would simply run **ll**.

## Useful aliases & The .bash_aliases file:
1. https://www.digitalocean.com/community/questions/what-are-your-favorite-bash-aliases
2. https://dev.to/roelofjanelsinga/what-are-your-favorite-bash-aliases-2h26