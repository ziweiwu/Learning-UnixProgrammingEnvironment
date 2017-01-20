## chapter 3: USING THE SHELL 

### Command line structure
- ; is an alternative command terminator, other than newline
- sending two commands to pipeline use (date;who)|wc, data send to pipline can be redirect or saved eg. (date;who)| tee save | wc.
- & is another command terminator, but it allows the command to run in the background eg. long-running-command &
- various special characters such as >, <, |, ; and & are not arguments to the programs the shell runs. They instead control how the shell runs them 
- eg. echo hello > junk (echo with hello, > junk is not an argument of echo so never seen by echo)

### Metacharacters
- characters like * is a meta character for shell. eg. echo * (tells shell to list every filename in the directory expect for filename that stars with .filename)
- to prevent metacharacters from being recognized by the shell, use "" to protect it
- a backslash at the end of a line causes the line to be continue.
    - eg. $ echo abc\
    -  def\
    -  ghi
    - abcdefghi

- metacharacter # is used for shell comments

### Creating new commands
- you can add your own commands by create a command and save it to a text file eg. echo "ls -ltu' > lsu.
- you can execute the new command by sh newcommand 
- mv the newcommand file to home/user/bin would make the newcommand directly available for the shell, eg. $ lsu can be used directly

### Shell Variables
- The shell has variables, like those in most programming languages, which in shell jargon are sometimes called parameters.
- set: the shell built in command displays the value of all your defined variables. 
- to view just a few define variables, echo is a better option
- You can assign variable in the shell. eg x=hello, however this variable is only available in the current shell. if you create a subshell using sh, the x is no longer available 
- export: this command make a variable available from parent shell to its sub shell eg. export x
- don't export temporary variables set for short-term convenience, but always export variable you want set in all your shells and sub-shells. Therefore variables special to the shell, such as PATH and HOME, should be exported

### I/O redirection
- Every program has three default files established when it starts, numbered by small integers called file descriptors. 
    1. standard input, 0
    2. standard ouput, 1
    3. standard error output, 2
- time: run a command and then reports on the standard error how much it took. 
- shell I/O redirection:
    1. >file: direct standard output to file
    2. >>file: append standard output to file
- shell supports control flow such as for loop 
- eg: for i in list; do commands; done

### Overview
- Unix Shell is programmable, the power of shell derives from UNIX kernel
- Shell sets up pipes, the kernel actually moves the data through them. 
- Shell is a program itself, not part of the kernel, so it can be tuned, extended and used like any other program. - So whatever you are doing with shell, you are programming it. 



