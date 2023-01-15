[[Index]] 


# Groups & Users

  
  

~~~~

groupadd group_name  

  

  

Example:  

  

  

groupadd friends  

~~~~

  

## usermod

~~~~

usermod [ options ] username  

  

  

-c "COMMENT"

  

-g GROUP

  

Comments account.

  

Specify the default group.

  

-G GROUP1,GROUPN Additional groups.

  

-s /shell/path Path to the user's shell.

~~~~

  

## Usermod  

~~~~

grep mysql /etc/passwd

~~~~

~~~~

mysql:x:97:1003:MySQL Server:
  
~~~~



~~~~
/opt/mysql:/usr/sbin/nologin
~~~~

usermod -c "MySQL User" mysql

~~~~  

 

grep mysql /etc/passwd

  

mysql:x:97:1003:MySQL User:

 

   

/opt/mysql:/usr/sbin/nologin

  

~~~~

  

~~~~

/etc/group

  

root:x:0:

  

sales:x:1001:john,mary

  

The format of the /etc/group file:

  

group_name:password:GID:account1,accountN

~~~~

~~~~

groups [username]

  

groups root

  

  

root

  

~~~~

  

## groupadd [ options ]group_name

  

~~~~

groupadd web

  

tail -1 /etc/group

  

web:x:1003:

  

groupadd -g 2500 db

  

tail -1 /etc/group

  

db:x:2500:

  

~~~~

  

  

## Groupmod  

~~~~

groupmod [options] group_name

  

-g GID

  

-n GROUP

  

Change the group ID to GID.

~~~~

  

# Rename the group to GROUP.

  

~~~~

groupmod

~~~~

~~~~

grep web /etc/group

  

web:x:1003:

~~~~

~~~~

groupmod -g 1234 web

  

grep web /etc/group

  

web:x:1234:

~~~~

~~~~

groupmod -n http web

  

grep http /etc/group

  

http:x:1234:  

~~~~

  

## Group Deletion  

  

~~~~

groupdel <group_name>

  

groupdel db  

~~~~

  

## cat and grep file for particular expression:

~~~~  

cat /etc/group | grep <part_group_name>  

~~~~ 

# Troubleshooting User accounts:

  

The issue was the client didn't have access to the BE of the Prod domain so they couldn't use winscp to login

  

  

# Create BE and check if they can login  

  
~~~~ 
If they can't, try and login into their account from another Linux box  e.g. ssh <theiruserid>@<targetserver>  

  

If you can login, then check their if their user permissions are correct via lslogins <username> compare the results to their other BE accounts in other domains  

  

Check if the client can telnet to port 22 on the server (This rules out any network issues on their side)  

  
~~~~ 

## Create new user with Useradd  

  

  

useradd[options] username  

  

  

-c "COMMENT"

  

-m

  

-s /shell/path

  

Comments for the account.

  

Create the home directory.

  

The path to the user's shell.

  

  

## Useradd  

  

~~~~

useradd –c "Grant Stewart" –m –s /bin/bash grant

~~~~

  

Note:This is one command line. It's displayed on

  

multiple lines for readability.

  

~~~~

useradd –c "Grant Stewart" –m –s /bin/bash grant

~~~~

  

## SECONDARY USER ACCOUNT Creation:  

  

~~~~

adduser jbloggs <Create user>

~~~~

~~~~

passwd jbloggs  <Set Password>

~~~~

~~~~

chage -d 0 jbloggs  Triggers user to change it when they log in

~~~~

~~~~

chage -E 6 jbloggs - 6 month expiry date

~~~~

~~~~

id cpearson

~~~~

~~~~

usermod -a -G <group_name> jbloggs - add to group  

~~~~

  

## Create a password using passwd  

  

~~~~

passwd grant

  

  

Enter new UNIX password:

  

Retype new UNIX password:

  

passwd: password updated

  

successfully

~~~~

~~~~

tail -1 /etc/passwd

  

  

grant:x:1000:1000:Grant Stewart:/home/grant

  

:/bin/bash

  

~~~~

  

~~~~

tail -1 /etc/shadow

grant:66iDDsgsPYtR8c2Uc.:16507:0:99999:7:::

~~~~

Account information for "grant"

  

  

## More useradd options  

  

~~~~

  

-g GROUP Specify the default group.

  

-G GROUP1,GROUPN Additional groups.

~~~~

~~~~

useradd –c "Eddie Harris" –m –s

~~~~

~~~~

/bin/bash –g sales –G projectx

  

eharris

~~~~

~~~~

useradd

  

passwd eharris

  

  

Enter new UNIX password:

  

Retype new UNIX password:

  

passwd: password updated successfully

~~~~

  

## System or ApplicationAccounts

  

~~~~

useradd –c "Apache Web Server

~~~~

~~~~

User" –d /opt/apache –r –s

  

/usr/sbin/nologin apache

~~~~

~~~~

tail -1 /etc/passwd

~~~~

~~~~

apache:x:999:999:Apache Web Server

  

User:/opt/apache:/usr/sbin/nologin

~~~~

~~~~

/etc/skel

  

  

● When using -m the home directory for the

  

account is created.

  

● The contents of /etc/skel are copied into the

  

home directory.

  

● /etc/skel typically contains shell configuration

  

files. (.profile, .bashrc,etc)

~~~~

  

## More user adoptions II

  
~~~~

-r Create a system account.

  

-d /home/dir Specify the home directory.

~~~~

~~~~

Use -u to specify the UID

useradd –c "MySQL Server" –d  

~~~~

  

~~~~

/opt/mysql -u 97 –s /usr/sbin/nologin

  

mysql

~~~~

~~~~

tail -1 /etc/passwd

  

  

mysql:x:97:1003:MySQL Server:

  

/opt/mysql:/usr/sbin/nologin  

~~~~

  

# Delete user account:  

  
~~~~

userdel [-r]username

  

ls /home

  

  

eharris grant

  

  

userdel eharris

  

  

ls /home

  

  

eharris grant

  

  

userdel -r grant

  

  

ls /home

  

  

eharris  

  

lslogins <user_account_name>  

~~~~

~~~~

$ id

uid=503(tclark) gid=506(authors)

groups=504(tclark),506(authors)  

~~~~

# Logging into new group

  

~~~~

$ id

uid=503(tclark) gid=504(tclark)

groups=504(tclark),506(authors) 

$ newgrp authors

  

~~~~

~~~~
$ id

uid=503(tclark) gid=506(authors)

groups=504(tclark),506(authors)  

~~~~

[[Index]] 



