---
layout: post
author: aishwarya
---

# Linux Commands

This blog post covers some basic Linux commands and how to use them.

#### Basic Linux Commands
- pwd
This stands for present working directory. Running this command tells you the absolute (i.e. complete) path of where you are on the server.
```
user1@server1:~$ pwd
/home/user1
```
- cd
This stands for change directory. If you would like to move from one directory to another, use this command. Running ```pwd``` after this reflects the changed working directory.
```
user1@server1:~$ cd Music/
user1@server1:~$ pwd
/home/user1/Music
```
```cd ../``` takes you back up one directory. For example, doing ```cd ../``` from ```/home/user1/Music``` takes you to ```/home/user1``` while ```cd ../../``` would have taken you to ```/home/```.
```cd -``` takes you to the last directory you were working on. For example, if you run ```cd /home/``` followed by ```cd /home/user1/Music/```, running ```cd -``` takes you to ```/home/``` which was the previous directory you were working on.
```cd``` takes you to your home directory, i.e. where your user's folder reside.
- mkdir
This stands for make directory. If you want to create a directory, or a subdirectory, use this command.
```
user1@server1:~$ cd Music/
user1@server1:~$ mkdir MyFavorites
user1@server1:~$ cd MyFavorites
```
If you wish to create a whole directory structure path in one go, for example ```/home/user1/Music/MyFavorites/Fav1/Song1/``` without creating the intermediate folders one at a time, use the ```-p``` flag. If this flag is not used, the OS expects the intermediate directories to exist.
```
user1@server1:~$ cd Music/
user1@server1:~$ mkdir -p MyFavorites/Fav1/Song1/
user1@server1:~$ cd MyFavorites/Fav1/Song1/
```
- ls
This stands for list. Running this command lists all the files and directories available in the path you are at.
```
user1@server1:~$ cd
user1@server1:~$ pwd
/home/user1
user1@server1:~$ ls
Desktop    Downloads  Music Pictures  Templates
Documents  Public    Videos
```
To sort the files/folders by date, use ```ls -ltr```.
```
user1@server1:~$ cd
user1@server1:~$ pwd
/home/user1
user1@server1:~$ ls -ltr
total 541628
drwxr-xr-x  2 user1 user1      4096 Feb  3  2021 Videos
drwxr-xr-x  2 user1 user1      4096 Feb  3  2021 Templates
drwxr-xr-x  2 user1 user1      4096 Feb  3  2021 Public
drwxr-xr-x  2 user1 user1      4096 Feb  3  2021 Pictures
drwxr-xr-x  2 user1 user1      4096 Feb  3  2021 Music
drwxr-xr-x  2 user1 user1      4096 Feb  3  2021 Downloads
drwxr-xr-x  2 user1 user1      4096 Feb  3  2021 Documents
drwxr-xr-x  2 user1 user1      4096 Feb  3  2021 Desktop
drwxrwxr-x  4 user1 user1      4096 Oct 27  2021 my_testfile
```
- mv
This stands for move. It can be used to move a directory or a file, within another directory or to rename it. If the destination folder already exists, the source file/directory is moved within the destination folder. If the destination does not exist, it is treated as a rename operation.
```
user1@server1:~$ cd /home/user1
user1@server1:~$ mv Music Music_folder
```
- cp
This stands for copy. To copy a folder/file from one path to another. It is also possible to preserve the file and folder permissions, mode and timestamp using ```-p``` flag, and a forceful copy using ```-f``` flag. To copy the contents of a folder recursively, the ```-r``` flag is used.
```
user1@server1:~$ cd /home/user1
user1@server1:~$ cp -rpf Music Music_copy
```
- grep
This can be used to search for a string in a file, or to search for a string in a directory.
To search for a string("server") in a specific file("textfile.txt")
```
user1@server1:~$ cd /home/user1/
user1@server1:~$ grep server textfile.txt
This line has the word server.
```
To search for all files in a directory(/home/user1/Music) containing a specific search string("server"). Add the flag ```-i``` to ignore case in the search.
```
user1@server1:~$ cd /home/user1/
user1@server1:~$ grep -rl "server" /home/user1/Music/
./Music/textfile2
```
To search for the exact lines in the files in the directory,
```
user1@server1:~$ cd /home/user1/
user1@server1:~$ grep -r "server" /home/user1/Music/
./Music/textfile2: This is another line with the word server.
```
- touch
- echo
- >
- >>
- |
- rm
- cat

#### Some Advanced Commands
- ps
This command is used to list all running processes on the server and their process IDs. You can also combine commands using the ```|``` operator.
For example, if you wish to check if a java process is running and you know that the process would have been started with a command that would have the word "java" in it, you could run
```
ps -ef | grep java
```
- awk
This command operates on the basis of patterns, and can be used to filter out certain parts/columns of the output of another command, using ```|```.
```
user1@server1:~$ date
Mon Aug 29 22:38:16 +08 2022
user1@server1:~$ date | awk '{print $1, $2, $3}'
Mon Aug 29
user1@server1:~$ date | awk '{print $1, $2, $3, $4}'
Mon Aug 29 22:40:08
```
- screen
- nohup

#### VIM
This is a very powerful text editor available on Linux. Some very basic tips on using vim are listed below:
- To open/create a new file called mytext.txt
```
user1@server1:~$ vim mytext.txt
```
- Once the file opens, you insert content/text after pressing the ```i``` key on your keyboard, which stands for insert.
- Type in your content and to save the file, type the sequence of keys ```Esc```, ```:wq```, which writes and quits the file. If ```Esc```, ```:q``` is typed, it will not write in anything, just retains what was already there (quick exit strategy when you accidentally insert something you did not intend to). Adding an ```!``` at the end of ```:wq``` or ```:q``` forces the operation. Likewise, ```:w``` writes but does not quit the file.
- If you wish to delete a line, press ```Esc```, ```dd```. To delete say 100 lines, key in ```Esc```, ```100dd```.
- If you wish to insert a blank line after the line your cursor is currently at, press ```Esc``````o```.
- Undo can be done with ```Esc``````u```.
- To search for a string("hello"), type ```Esc``` followed by ```/hello``` and hit Enter. This takes you to the nearest occurrence of the string, after the current cursor position. To search further down, type ```n``` and to search for the previous occurrence type ```N```.
- To go to the start of the file, key in ```Esc``` followed by ```gg``` and to go to the end type ```Esc```, ```G```.

Please note that some more advanced features like Visual mode are not covered here. To try some vim commands and to practice using vim in an interactive mode, you can explore go to [link](https://www.openvim.com/).