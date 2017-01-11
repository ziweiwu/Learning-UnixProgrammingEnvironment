## Chapter2: THE FILE SYSTEM 

### overview
1. everything in unix is based on file
2. keep it simple philosophy
3. power can be achieved by careful implememntation of a few well-chosen ideas. 

### The basics of files 
1. file is a sequence of bytes (you can imagine one byte being a char)
2. od: prints a visible representation of the all the bytes of a file. 
    * 7 digit number on the left are position in the file
3. cat: shows what a file look like
4. Special characters:
    * \n: resulted from pressing RETURN key.
    * \t: tab
    * \r: carriage return, also is triggered by pressing RETURN key
    * \b: BACKSPACE, when you press backspace in terminal, the kernel interprets that you can want to delete an char, so that both the \r and previous char are deleted, however \b is echoed in terminal so the cursor moved one position backward
5. file ends when the system finds there's no more data in a file

### What's in a file 
* Four typical files:
    1. directory where it resides (eg./bin)
    2. the binary or runnable program itself (eg. /bin/wc)
    3. the source code that defines the program (eg. /user/src/cmd/ed.c)
    4. the manual page (eg. /user/man/man1/wc.1)
* file reads the first few hundred bytes of a file and looks for clues to the file type. 
* None-text files are harder to maintain and required specialized software to process them. 
* Text files may be less efficient in machine cycles, but can be easily accessed and maintained

### Directories and filename
* process operate in its current directory; if child of process would have the same current directory as the parent, if children process changes its currently directory, parent working directionary is unaffected.
* the login directionary of bash is /user/you
    * /user/src contains the source for system programs
    * /user/src/cmd contains the source for UNIX commands
    * /user/src/cmd/sh contains the source files for the shell
* mkdir: making a new directory
* pwd: print the working directory
* du: display the disk usage for each sub-directories in WD
* junk and ./junk are names for the same file, because if you don't assume directory, system assumes '.' - the WD
* directories sits in system as ordinary files, combination of binary and textual data. 
* each directory files begins with two entries '.' and '..'
* / is root of the file system, every file in the system is in the root directory or one of its subdirectories, and root is its own parent

### Persmissions
* Super-user/root  has the right to make changes or view any file on the file system 
* sudo commands give anyone who knows the root password root user priviledge
* each user has a numeric id called USERID and also is assigned a GROUPID (eg. originary users are assigned as group others)
* three types of permission:
    1. read (examine its content)
    2. write (change its content)
    3. execute (run it as a program)
* passwd: program can be used to set user password
* chmod: changes the permission on files
* inodes: stores the administrative information of a file, three types of information
    1. time that the contents of the file were last modified(written)
    2. time that the file was last used (read or execute)
    3. time that the inode itself was last changed 
    * ls -i: display the inode number of the file
    * the system's internal name for a file is the its i-number
    * therefore a filename in a directory is therefore called a link, because it links a name in the directory hierarchy to the inode, and hence the data
    * an inode can have multiple links, rm only remove one link to inode, only when the last link to inode has been removed, the system removes inode and hence the file. 
    * ln: makes link to an existing file with synatx "ln old-file new-file"
    * li -li: display the files in the wd, and number of links each file has, all links points to the inode of file. 

### removing a file
    * once the last link to a file is removed, the file is destroyed from the system, and no way to restore the file unless you can make a copy of the file. 

### copying a file 
    * cp: copy a file (eg. cp junk copyofjunk)
    * this is useful to turn off write permission to protect the copy of file (chmod -w copyofjunk)
    * if a file has write permission turned off, rm this file would require a permission 

### rename/move a file 
    * mv: rename a file (mv junk sameoldjunk), or move a file to another directory (mv junk /newfolder)
    * the file has been renamed would have the same i-number

### directory hiearchy 
    * enter ls / 
        1. /bin is the directory where basic programs resides
        2. /dev 
        3. /etc various admin files such as password and system programs
        4. /lib contains primarily parts of C compiler such as /lib/cpp, and lib/lib/libc.a 
        5. /tmp temporary files, cleaned when system is restarted 
        6. /user user file system

### devices
    * /dev contains device files
    * each dev is either block or character devices represents as files under /dev
    * discs and tapes are block devices
    * everything else: terminals, printer, phone lines are character device 
    * eg. /dev/rp10 (1 represents the physical drive, 0 represents the portion of drive)
    * df: disk free command reports the available space on the mounted file subsystem.
    * tty: tells you which terminal you are using. terminal file is stored at dev/tty
    * /dev/null: data written to dev/null is thrown away, while the programs that read from /dev/null get end of file immediately. This is useful to know when you do not care what output the program is producing, you can direct the output to /dev/null
        
