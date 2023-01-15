[[Index]] 

## Configuration for remote server being accessed

~~~~

eze@ubuntu:~$ sudo apt install openssh-server

eze@ubuntu:~$ sudo systemctl status ssh

eze@ubuntu:~$ sudo ufw allow ssh

root@ubuntu:~# ufw status

~~~~

## Key Generation:

~~~~

eze@ubuntu:~$ sudo apt install openssh-server

  

eze@ubuntu:~$ sudo apt-get update / yum update (redhat)

  

eze@ubuntu:~$ sudo apt-get upgrade /yum update (redhat)

  

systemctl start sshd  

  

systemctl status sshd

  

eze@ubuntu:~$ sudo systemctl status ssh

  

eze@ubuntu:~$ sudo ufw allow ssh

  

eze@ubuntu:~$ sudo ufw enable

  

eze@ubuntu:~$ ssh-keygen -t rsa

  

eze@ubuntu:~$ cd .ssh

  

eze@ubuntu:~/.ssh$ ssh-keygen

  

eze@ubuntu:~/.ssh$ ls

key1 key1.pub

eze@ubuntu:~/.ssh$ ls –ltr

total 8

-rw-r--r-- 1 eze eze 392 Dec 19 16:11 key1.pub

-rw------- 1 eze eze 1679 Dec 19 16:11 key1

  

eze@ubuntu:~/.ssh$ ssh-copy-id -i ~/.ssh/key1.pub 192.168.142.136

  

eze@ubuntu:~/.ssh$ ssh 192.168.142.136

~~~~

  

~~~~  

 chmod 600 or 700 for ssh key to work

~~~~

  

## Copy SSH credentials

~~~~
cat id_rsa.pub | pbcopy

~~~~  
  

# SSH File Config

  Used for multiple users trying to access a box

~~~~

  1. Create new user using adduser command on the box you want them to have access

~~~~


~~~~
2) use this command to copy the public key to the server you're trying to access:  

   ssh-copy-id -i ~/.ssh/obi_rsa.pub ezeaka01@10.61.240.244 (username@ip_addr)

~~~~

  
~~~~

3) nano config in /.ssh directory

Edit config file like below:

Config file:

Host *

   IdentityFile ~/.ssh/obi_rsa

   User ezeaka01

Example:

ssh ezeaka01@10.61.240.244

~~~~

## How to create ssh config

~~~~

  ssh 10.61.240.244 -v

  ssh ezeaka01@10.61.240.244

  ll

  ssh-copy-id -i ~/.ssh/obi_rsa.pub ezeaka01@10.61.240.244  

  nano config

  Config file:

Host *

   IdentityFile ~/.ssh/obi_rsa

   User ezeaka01

  ssh 10.61.240.244

  history

~~~~

  

# Config for extending SSH timeout

  

~~~~

~/.ssh/config

  

Host *

  ServerAliveInterval 120

~~~~

  

# File Transfer

  

~~~~

/usr/bin/scp <app node name>:<filepath> <db node>:<filepath>

~~~~

[[Index]] 