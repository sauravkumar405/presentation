# Basic commands in Linux

## tree

***

```
$ tree 
```

* This commmand will display the tree heirarchy of our current directory

## pwd

***

```
$ pwd
```

* pwd stands for print working directry, it gives us the addresss of our current directory

## cd

***
> cd command in linux known as change directory command. It is used to change current working directory.


```
$ cd /
```
* This command is used to change directory to the root directory, The root directory is the first directory in your filesystem hierarchy.



```
$ cd dir_1/dir_2/dir_3
```
* This command is used to move inside a directory from a directory


```
$ cd ~
``` 
* This command is use to change the directory to home directory


```
$ cd ..
```
* This command is use to the parent directory

``` 
$ cd dir_name
```

* This command is used to navigate to navigate to a directory dir_name

## mkdir
***

> mkdir command in Linux allows the user to create directories. This command can create multiple directories at once as well as set the permissions for the directories. 

```
$ mkdir dir_name
```
* This command is used to create a new directory in the current path

```
$ mkdir -m a=rwx [directories]
```
* The above syntax specifies that the directories created give access to all the users to read from, write to and execute the contents of the created directories.


## touch
***
> The touch command is a standard command used in UNIX/Linux operating system which is used to create a file.

```
touch file1.txt
```
* Creating a text file with name file1.txt
```
touch file1.txt file2.txt file3.txt
```
* Creating multiple files with single command

## ls
***
> The Linux ls command allows you to view a list of the files and folders in a given directory. 
```
$ ls -a
```
* In Linux, hidden files start with . (dot) symbol and they are not visible in the regular directory. The (ls -a) command will enlist the whole list of the current directory including the hidden files.

```
$ ls -l
```
* It will show the list in a long list format.
```
$ ls -r
```
* It is used to print the list in reverse order

```
$ ls -R
```
* It will list the content of the subdirectories also.

```
$ ls -t
```
* Sorts the list in according to modification time (newest first) 




## chmod 
***
> In Unix-like operating systems, the chmod command is used to change the access mode of a file.
The name is an abbreviation of change mode.

Syntax : 
```
$ chmod [reference][operator][mode] file... 
```

References : 
```
Reference   Class     Description

u          owner      file's owner

g          group      users who are members of
                      the file's group

o          others     users who are neither the
                      file's owner nor members of 
                      the file's group

a          all       All three of the above
```

Operators : 
```
Operator  Description

+         Adds the specified modes to the
          specified classes

-         Removes the specified modes from 
          the specified classes

=         The modes specified are to be made
          the exact modes for the specified 
          classes
```
Modes : 
```
r       Permission to read the file.

w       Permission to write (or delete) the file.

x       Permission to execute the file, or, in
        the case of a directory, search it.
```
Changing permissions:

```
$ chmod u+x file.txt
```
* This commaand is used to add the execute permission to user

```
$ chmod o+r file.txt
```
* this command will add the read permission to other users.

```
$ chmod g-w file.txt
```
* This command will remove the write permission from group. 

Changing permissions using binaries : 

```
4 - read

2 - write

1 - execute

0 - none
```
Combination of these helps uss generate code for permission\
 ```
 4 + 2 means rw-
 2 + 0 means -w-
 4 + 1 means r-w
 ...and so on
 ```
 Examples : 

```
$ chmod 700 file.txt
```
* This command will change the user permission to all rwx whereas for groups and other users it will be none (---).
```
$ chmod 420 file.txt
```
* This command gives user, group and other users read, write and none permission respectively.

```
$ chmod 777 file.txt
```
* This command will give all three permission to all the users

## cp
***

Syntax : 
```
$ cp [OPTION] Source Destination
$ cp [OPTION] Source-1 Source-2 Source-3 Source-n Directory
```
Example : 
```
$ ls
a.txt  b.txt  new

Initially new is empty
$ ls new

$ cp a.txt b.txt new

$ ls new
a.txt  b.txt
```
* In this we can see that multiplee files can be copied to a directory

```
$ cp -R Src_directory Dest_directory
```
* This command copies all the files and directories from source directory to destination directory. Here -R flag  is needed to recursively copy all subdirectories and files from the source directory to destination directory.

```
Initially Folder1 is empty

$ ls

a.txt  b.txt  c.txt  d.txt  e.txt  Folder1

$ cp *.txt Folder1

$ ls Folder1

a.txt  b.txt  c.txt  d.txt  e.txt
```

* If we want to select all the files of one type than we can use a wild card (*) to specify the type of file.


## mv
***
> mv stands for move. mv is used to move one or more files or directories from one place to another in a file system like UNIX. It has two distinct functions: 
(i) It renames a file or folder. 
(ii) It moves a group of files to a different directory. 

Syntax : 
```
mv [Option] source destination
```

```
$ ls

a.txt  b.txt  c.txt  d.txt

$ mv a.txt geek.txt

$ ls

b.txt  c.txt  d.txt  geek.txt
```
* In the above example a new file is created named geek.txt and the contents of a.txt has been moved to geek.txt

```
$ ls
b.txt  c.txt  d.txt  geek.txt

$ cat geek.txt
India

$ cat b.txt
geeksforgeeks

$ mv -i geek.txt b.txt
mv: overwrite 'b.txt'? y

$ ls
b.txt  c.txt  d.txt

$ cat b.txt
India
```
* The -i option makes the command ask the user for confirmation before moving a file that would overwrite an existing file, you have to press y for confirm moving, any other key leaves the file as it is. This option doesn’t work if the file doesn’t exist, it simply rename it or move it to new location.


```
$ ls
b.txt  c.txt  d.txt  geek.txt

$ cat b.txt
geeksforgeeks

$ ls -l b.txt
-r--r--r--+ 1 User User 13 Jan  9 13:37 b.txt

$ mv geek.txt b.txt
mv: replace 'b.txt', overriding mode 0444 (r--r--r--)? n

$ ls
b.txt  c.txt  d.txt  geek.txt

$ mv -f geek.txt b.txt

$ ls
b.txt  c.txt  d.txt

$ cat b.txt
India
```

* mv prompts for confirmation overwriting the destination file if a file is write-protected. The -f option overrides this minor protection and overwrites the destination file forcefully and deletes the source file. 


## rm 
***
> rm stands for remove here. rm command is used to remove objects such as files, directories, symbolic links and so on from the file system like UNIX. To be more precise, rm removes references to objects from the filesystem, where those objects might have had multiple references (for example, a file with two different names). By default, it does not remove directories.


Syntax : 
```
rm [OPTION]... FILE...
```
Examples : 
```
$ ls
a.txt  b.txt  c.txt  d.txt  e.txt

Removing one file at a time
$ rm a.txt

$ ls
b.txt  c.txt  d.txt  e.txt

Removing more than one file at a time
$ rm b.txt c.txt

$ ls
d.txt  e.txt

```
* We can use rm to delete a file or multiple files with a single command

```
$ rm -r dir_name
```
* rm can delete a directory using -r flag only

## cat
***
> cat commant is used to view the contents of a file

```
$ cat file.txt
```
* This command will show us the contents of the file

```
$ cat -n file.txt
```
* -n flag will also add line numbers to the output

```
$ cat file1.txt file2.txt file3.txt
```
* we can open multiple files with a single command

## less
***
> Less command is a Linux utility that can be used to read the contents of a text file one page(one screen) at a time. It has faster access because if file is large it doesn’t access the complete file, but accesses it page by page. 

```
$ less file.txt
```
* This command will show us the briefly the contents of the file.txt

## head and tail
***
> The head and tail commands are used to display the first and the last n lines 

 Examples : 
 ```
 head -n 10 file.txt
 ```
 * This command is used to display first 10 lines of the files

 ```
 $ tail -n 10 file.txt
 ```
 * Displays the last 10 lines of the file

```
$ head -n 20 file.txt | tail -10
```
* Displays the contents of the file from line number 10 to 20.

## rsync
***
> rsync or remote synchronization is a software utility for Unix-Like systems that efficiently sync files and directories between two hosts or machines. 

Syntax : 
```
rsync [options] source [destination]
```
Examples : 

```
$ rsync dir1/file1.txt dir2/
```
* Using this command file1.txt will be copied to the dir2 directory and will be in sync with file1.txt in the dir1 directory.

## grep
***
> The grep filter searches a file for a particular pattern of characters, and displays all lines that contain that pattern. The pattern that is searched in the file is referred to as the regular expression.

```
grep "pattern" file.txt
```
* This command returns all the mathching pattern in the file whether it is a work or a substring.

```
grep -w "pattern" file.txt
```
* This commands return only the perfect match and not the substring

```
grep -i "pattern" file.txt
```
* Disables case sensitivity

```
grep -n "pattern" file.txt
```
* Returns the line number along with the match

```
grep -B 10 "pattern" 
```
* Displays 10 lines before every match in the file 

```
grep -A 10 "pattern" 
```
* Displays 10 lines after every match in the file

```
grep -C 10 "pattern" 
```
* Displays 10 lines before and after every match in the file 

## find
***
> The find command in UNIX is a command line utility for walking a file hierarchy. It can be used to find files and directories and perform subsequent operations on them. 

```
$ find . -type d
```
* In this command . represents the current path and -type is used to specify the type of entity we want to search

```
find . -type f
```
* This command will search for all the files inside our current directory

```
$ find . -type f -name "test.txt"
```
* lists all the files with the name test.txt

```
$ find . -type f -name "*.txt"
```
* lists all the files with .txt extension

```
$ find . -perm 777
```
* list all the files and directories whose permission is 777
```
$ find . -type f -name "test.txt" -exec rm {} +
```
* -exec is used to execute commands on certain files. Here in this example all the files whose name is test.txt will be removed.

# References

<https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners>
<https://blcklstdbb.gitbooks.io/hackmd/content/linux-commands.html>
<https://www.geeksforgeeks.org/find-command-in-linux-with-examples/>
<https://www.geeksforgeeks.org/grep-command-in-unixlinux/>
<https://www.geeksforgeeks.org/practical-applications-ls-command-linux/>