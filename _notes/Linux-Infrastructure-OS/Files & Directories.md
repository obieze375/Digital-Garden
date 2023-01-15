[[Index]] 


  
  

## pwd command

  

• pwd : prints current working directory

~~~~  

Example:

paul@debian8:~$ pwd

/home/paul

~~~~

  

## cd

  

• cd -> changes your current directory + also return to your home dir

~~~~

Example:

paul@debian8$ cd /etc

paul@debian8$ pwd

/etc

~~~~

  
  

## cd – command continued

~~~~

paul@debian8$ cd

paul@debian8$ pwd

/home/paul

~~~~

  

## cd .. – Return to previous directory

~~~~

paul@debian8$ pwd

/usr/share/games

paul@debian8$ cd ..

paul@debian8$ pwd  

/usr/share

~~~~

  

## Path Completion

  
~~~~
The tab key can help you in typing a path without errors. Typing cd /et

followed by the tab key will expand the command line to cd /etc/.

When typing cd /Et followed by the tab key, nothing will happen

because you typed the wrong path (upper case E).

  

You will need fewer key strokes when using the tab key, and you will

be sure your typed path is correct!
~~~~  

## ls – command

  

## ls – lists contents of directory

  

~~~~

• Example:

stuff summer.txt

paul@debian8:~$ ls

allfiles.txt dmesg.txt services

paul@debian8:~

~~~~

  

## ls –a - Shows all files including hidden ones

  

~~~~

allfiles.txt .bash_profile dmesg.txt .lesshst stuff .. .bash_history

.bashrc services .ssh summer.txt

• Example:

• paul@debian8:~$ ls -a

paul@debian8:~$

~~~~

  

## ls -hal

  

## Shows all files with read and write permissions

~~~~

ls –ltr

~~~~

  

## ll – Lists contents of directory and gives date

~~~~

obi@eze:~$ ll

total 189456

drwxr-xr-x 21 obi  obi       4096 Jan 25 18:30 ./

drwxr-xr-x  3 root root      4096 Jan 10 15:03 ../

-rw-r--r--  1 obi  obi        220 Jan 10 15:03 .bash_logout

-rw-r--r--  1 obi  obi       3771 Jan 10 15:03 .bashrc

drwx------ 15 obi  obi       4096 Jan 10 15:57 .cache/

-rwxr-xr-x  1 obi  obi         42 Jan 10 17:40 command_sub.sh*

-rwxr-xr-x  1 obi  obi         42 Jan 10 17:41 command_substitution.sh*

drwxr-xr-x 17 obi  obi       4096 Jan 10 18:28 .config/

~~~~

  

## ls -R - List Ditrectory and subdirectory structure

  

~~~~
ls -R
~~~~

  
  
  

# Search for files in Directories

  

~~~~

 ll <*STRING_TO_SEARCH*>

~~~~

  

# Working with files

  

~~~~

file – determines file type of file

~~~~

  

~~~~

paul@laika:~$ file pic33.png

pic33.png: PNG image data, 3840 x 1200, 8-bit/color RGBA, noninterlaced

paul@laika:~$ file /etc/passwd

/etc/passwd: ASCII text

paul@laika:~$ file HelloWorld.c

HelloWorld.c: ASCII C program text

~~~~

  

# touch – creates empty files

  

~~~~

paul@debian7:~$ ls -l total 0

paul@debian7:~$ touch file42

paul@debian7:~$ touch file33

paul@debian7:~$ ls –l

total 0

-rw-r--r-- 1 paul paul 0 Oct 15 08:57 file33

-rw-r--r-- 1 paul paul 0 Oct 15 08:56 file42

~~~~

  

# File Creation Commands

~~~~

vim

  

nano

  

cat


The Ctrl d key combination will send an EOF (End of File) to the running

process ending the cat command
  
~~~~ 

  ## File Compression
 
 gzip -

  

# -f option :

  

Sometimes a file cannot be compressed. Perhaps you are

trying to compress a file called “myfile1” but there is already a file called

“myfile1.gz”. In this instance, the “gzip” command won’t ordinarily work.

  

To force the “gzip” command to do its stuff simply use -f option:

  

~~~~

  2.$ gzip -f myfile1.txt

~~~~

  



  

The above command would end up with a file called “mydoc.txt.gz” and



  

~~~~

  “mydoc.txt”.

~~~~

  

## 3. -L option : This option displays the gzip license.



~~~~

  
  $ gzip -L filename.gz

~~~~

  

## Unzip files

  

1) Extract a tar.gz archive

  

The following command shell helps to extract tar files out a tar.gz archive.


~~~~

tar -xvzf bigfile.tar.gz

  

x – Extract files

v – Verbose, print the file names as they are extracted one by one

z – The file is a “gzipped” file

f – Use the following tar archive for the operation!
  

~~~~

  

2) Extract files to a specific directory or path

  

We can extract the files into a specified directory by using the parameter “-C”.

  



The tar command doesn’t create any files or folders.


~~~~

  
  tar -xvzf bigfile.tar.gz -C /folder/subfolder/

~~~~

  

## Extract a single file

  

To extract a single file out of an archive just add the file name after the command like this

~~~~
tar -xz -f Music.tar.gz “./new/one.mp3”
~~~~


To extract more than one file out of an archive


~~~~
tar -xv -f Music.tar.gz “./new/two.mp3” “./new/three.mp3”
~~~~

  

## Use unzip command to unzip a zip file

The syntax is:

  
~~~~

unzip {file.zip}

~~~~
  

Use the following syntax if you want to extract/unzip to a particular destination directory:

  
  
~~~~

unzip -d /dest/directory/ {file.zip}
~~~~

  
  



  
  

# Check contents of File


~~~~

cat /etc/passwd

root:x:0:0:root:/root:/bin/bash

bin:x:1:1:bin:/bin:/sbin/nologin

narad:x:500:500::/home/narad:/bin/bash

~~~~

  

# Check difference between 2 files

~~~~

  

diff filename1 filename2

  

~~~~

  

# rm – Deletes file forever

~~~~

paul@debian7:~$ ls

BigBattle.txt file33 file42 SinkoDeMayo

paul@debian7:~$ rm BigBattle.txt

paul@debian7:~$ ls

file33 file42 SinkoDeMayo

paul@debian7:~

~~~~

  

# rm –i – Deleting file with a check

  

~~~~

paul@debian7:~$ rm -i file33

rm: remove regular empty file `file33'? Yes

 ~~~~


  


# rm-f – Delete files

~~~~
 • VERY STRONG WAY TO DELETE FILES:

rm -f /* - Deletes all files in directory

~~~~
  

  

# cp – Copy One file

  

~~~~

paul@debian7:~$ ls

file42 SinkoDeMayo

paul@debian7:~$ cp file42 file42.copy

paul@debian7:~$ ls

file42 file42.copy SinkoDeMayo

~~~~

  

# Copy to another Directory

  

~~~~

paul@debian7:~$ mkdir dir42

paul@debian7:~$ cp SinkoDeMayo dir42

paul@debian7:~$ ls dir42/

SinkoDeMay
~~~~

 

  

# cp –r – Copy complete Directories

~~~~
paul@debian7:~$ ls

dir42 file42 file42.copy SinkoDeMayo

paul@debian7:~$ cp -r dir42/ dir33

paul@debian7:~$ ls

dir33 dir42 file42 file42.copy SinkoDeMayo

paul@debian7:~$ ls dir33/

SinkoDeMayo
~~~~
 


# copy multiple files to directory

~~~~

paul@debian7:~$ cp file42 file42.copy SinkoDeMayo dir42/

paul@debian7:~$ ls

dir42/ file42 file42.copy SinkoDeMay

cp – i – To prevent overwriting of files

paul@debian7:~$ cp -i SinkoDeMayo file42

cp: overwrite `file42’? N

paul@debian7:~$
  
~~~~

  

# More Copy notes

~~~~
cp filename/directory - copy file and directory

cp filename directory/directory - copy and move file

cp filename directory/directory/filename.bak - creates backup file
 

~~~~


 

  

# mv - Rename files with mv

~~~~

paul@debian7:~$ mv file42 file33

paul@debian7:~$ ls

dir33 dir42 file33 file42.copy SinkoDeMayo

paul@debian7:~$

~~~~

  
  

# Running bash script

~~~~

paul@debian7~$

./ - to run bash script

~~~~

  

# figlet

  

~~~~

• sudo apt-get install figlet

~~~~

  

# mkdir – Makes new directory

  

# Creates Directory

  

~~~~

paul@debian8:~/mydir$ mkdir otherstuff

paul@debian8:~/mydir$ ls -l

total 8 drwxr-xr-x 2 paul paul 4096 Sep 17 00:08 otherstuff

drwxr-xr-x 2 paul paul 4096 Sep 17 00:08 stuff

~~~~

  

# mkdir –p – Creates Parent with new directory

  

~~~~

paul@debian8:~$ mkdir -p mydir2/mysubdir2/threedirsdeep

paul@debian8:~$ cd mydir2

paul@debian8:~/mydir2$ ls -l

total 4 drwxr-xr-x 3 paul paul 4096 Sep 17 00:11 mysubdir2

paul@debian8:~/mydir2$ cd mysubdir2

paul@debian8:~/mydir2/mysubdir2$

~~~~

  

# Search through Directory -  

  

~~~~

sudo du -a /dir/ | sort -n -r | head -n 20

~~~~

  

# rmdir – Deletes Directory

  

~~~~

• paul@debian8:~/mydir$ rmdir otherstuff

• paul@debian8:~/mydir$ cd ..  

~~~~

# rmdir –p – Deletes Directory

  

~~~~  

• paul@debian8:~$ rmdir -p test42/subdir

• @debian8:~

~~~~

  

# move file to another location

  

~~~~

mv directory directory - moves file to another location

~~~~

  

# cat - Check contents of file

  

~~~~

• cat /etc/hosts

  

• cat /etc/hosts | grep <string_your're_looking_for>  (To search for a value through a file)
  
~~~~
  

# Pattern searching

~~~~
grep -v pattern file.txt
~~~~

## Search for string and line number in file

~~~~

grep -inr 'string' filename/dir

~~~~

## Find command

  

## Find Files Using Name in Current Directory

~~~~
  

find . -name tecmint.txt

./tecmint.txt

  

~~~~

  

# Find Files Under Home Directory

~~~~

find /home -name tecmint.txt

/home/tecmint.txt!

~~~~

  
  

# Editing Files with Vi

  

Vi Command Mode and Navigation

  

~~~~    

k  - Up one line.  

j -  Down one line.    

h  - Left one character.      

l  - Right one character.  

w  - Right one word.

b  - Left one word.

^  - Go to the beginning of the line.

$  - Go to the end of the line.

~~~~

  

## Vi Insert Mode

  

~~~~    

i Insert at the cursor position.

I Insert at the beginning of the line.  

a Append after the cursor position.  

A Append at the end of the line.

~~~~

## Vi Line Mode

  

~~~~

:w Writes (saves) the file.    

:w! Forces the file to be saved.  

:q Quit.  

:q! Quit without saving changes.  

:wq! Write and quit.  

:x Same as :wq.

~~~~

## Vi Line Mode

  

~~~~

:n Positions the cursor at line n.

:$ Positions the cursor on the last line.

:set nu Turn on line numbering.

:set nonu Turn off line numbering.

:help [subcommand] Get help.

~~~~

## Vi Modes

~~~~

Mode Key

Command Esc

Insert i I a A

~~~~

Line :

  

## Vi - Repeating Commands

  

● Repeat a command by preceding it with a

number.

  

~~~~  

○ 5k = Move up a line 5 times

○ 80i = Insert 80 times

○ 80i_ = Insert 80 "_" characters

~~~~   

## Vi - Deleting Text

~~~~
x Delete a character.

dw Delete a word.

dd Delete a line.  

D Delete from the current position.
~~~~





## Vi - Changing Text

~~~~

r Replace the current character.  

cw Change the current word.      

cc Change the current line.

c$ Change the text from the current position.  

C Same as c$.  

~ Reverses the case of a character.

~~~~

## Vi - Copying and Pasting

  

~~~~    

yy Yank (copy) the current line.  

y Yank the .  

p Paste the most recent deleted or yanked text.

  

To set paste if having formatting issues - (:set paste + shift I ) and then paste

4yy - Pastes 4 lines down page

  

~~~~

## Vi - Undo / Redo  

~~~~

u Undo

~~~~    

Ctrl-R Redo  

~~~~  

~~~~

## Vi - Searching  

~~~~    

/ Start a forward search.  

? Start a reverse search.

~~~~

  

## Vi - Recover swap file  

~~~~    

vim -r

~~~~

  
  

## Demo - vi

  

~~~~

---TODO: Overlay with characters that I'm

using.---- (Might be hard, maybe come back and

do that later????)

key-mon --nomouse --scale=2.1

~~~~

## Substitution Command

  

~~~~

• :%s/NEW VALUE TO INPUT/g  

• :%s/NEW VALUE TO INPUT/gic

~~~~

  

## Substitution Command II

  
~~~~
 :s/first value at beginning of line/

~~~~  
  
  

## Mass Delete and move to the bottom of file

  

~~~~

• dG

~~~~

  

## Move to the bottom of the file:  

~~~~

Shift + g

~~~~

## To reclaim previous command used

  

~~~~            

press shift key + ‘:’ and press the up arrow key

~~~~


## Set Numbering:

~~~~


set nu

~~~~

## Check for tabs:

~~~~

:set list - for yamls there should be no tabs or whitespaces between $ signs

~~~~

  

## Remove tab checker:

  

~~~~

:set nolist

~~~~

  

## Go to line:

  

~~~~

:644

~~~~

  

## Create new Blank line

  

~~~~

'o'

~~~~

  

## Undo changes

  

~~~~

u

~~~~

  
  

## Paste from particular line number to another line number

~~~~

:6,12 co .

  

6 is the 1st line, 12 is the endding line and place the cursor at the location you want to paste

~~~~


[[Index]] 



