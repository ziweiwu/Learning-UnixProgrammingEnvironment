## chapter 1: Unix For Beginners

### some simple commands
* date - show today's date
* who - show which users are logged on
* who am i- show who is current user
* man -show a manual eg. man sudo (a manual of sudo command)

### basic editor in Unix -ed
* a (add text)
* w (save text file, eg. save junk - save text with name junk)
* q (quit ed) 	

### ls command
* -t: files to list in time order
* -l: a more detail list

### cat/print
* cat: print files, catenated print of multiple files if (eg. cat text1 text2)
* pr: similar to cat, but print in a format suitable for line printer

### Moving, copying, removing files -mv, cp, rm
* mv: moving file or renaming (eg. mv junk precious -rename file junk to precious)
* cp: make a copy of a file (eg. cp precious precious.save - make a duplicated copy of precious in precious.save)
* rm: remove a file, note there is not warning message for this command

### What's in a filename
* filename are limited to 14 characters, you should avoid using special characters such as -
* case distinction matters in unix file system 

### Some useful commands 
* wc: word count (eg. wc junk -> 1 6 19, 1 line, 6 words, 19 characters)
* grep: search files for lines that match a pattern (eg. grep be junk - searches for lines containing 'be' in file junk)
* grep -v: search files for lines that does not match the criteria
* sort: sort input into a;phabetical order line by line. (order is blank>upper case>lower case)
    * -r reverse normal order
    * -n sort in numeric order
    * -nr sort in reverse numeric order
    * -f fold upper and lower case together
    * *n sort starting at n+1st field
* tail: print the last 8 lines of a file
    * tail -1: print the last line of a file 
    * tail +3: print from the 3rd line of a file 
* cmp: cmp file1 file2 - compare the difference between two files
* diff: reports on all lines that are changed, added or deleted, more detail than cmp

### Working with directory
* mkdir: making a directory
* rmdir: remove an empty directory
* cd: go to a directory
    * cd..(go to the above directory)
    * cd (go to home directory)
* pwd: print the working directory

### Shell
* *: * is a pattern matching notation that do the action on all files
* []: pr ch[123457] - print ch1 to ch7 but not 6
* ?: matches any single character eg. ls ? (list any single character names)
* >: output to a file eg. ls >filenames (instead of display all the filename, output the list into file filenames)

### Pipes
* pipe is a way to connect the output of one program into the inpput of another program without any temporary file; a pipline is a connection of two or more programs through pipeline
* any program that reads from the terminal can read from a pipe instead; any program that writes on the terminal can write to a pipe
* eg: who | grep mary | wc -1 (counts how many times Mary is logged in)

### Processes  
* an instance of a running program is called a process. 
* the number printed by the shell for a command initiated with & is called the process-id.
* program vs process: wc is a program; each time you run the program wc, that creates a new process. if several instances of the same program are running at the same time, each is a seperate process with a different process-id.
* pid is the process id
* TTY is the terminal associated with the process
* TIME is the processor time used in minutes and seconds
* CMD is the command being run
* nohup command &: allow the commnad continue to run even after turn off your terminal 
* nice expensive-command &: make the command runs with lower priority; nohup automatically calls nice
* at(l): tell the system to start your process at some wee hour of the morning when normal people are asleep, not computing.

### Tailoring the environment
* the default profile for bash in located in ~/.profile and can be edited using editor
  



