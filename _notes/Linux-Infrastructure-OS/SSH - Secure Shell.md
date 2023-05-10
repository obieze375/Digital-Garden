[[Index]] 

## Configuration for remote server being accessed 

** Make sure ssh is installed on both sides as in the servers and either the firewall is down or it allows ssh via s pecific port to both Ip's of the servers

```bash 

eze@ubuntu:~$ sudo apt install openssh-server

eze@ubuntu:~$ sudo systemctl status ssh

eze@ubuntu:~$ sudo ufw allow ssh

root@ubuntu:~# ufw status

``` 

## Key Generation:

```bash 

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

``` 

  

```bash   

 chmod 600 or 700 for ssh key to work

``` 

  

## Copy SSH credentials

```bash 
cat id_rsa.pub | pbcopy

```   
  

## SSH File Config

  Used for multiple users trying to access a box

```bash 

  1. Create new user using adduser command on the box you want them to have access

``` 


```bash 
2) use this command to copy the public key to the server you're trying to access:  

   ssh-copy-id -i ~/.ssh/obi_rsa.pub ezeaka01@10.61.240.244 (username@ip_addr)

``` 

  
```bash 

3) nano config in /.ssh directory

Edit config file like below:

Config file:

Host *

   IdentityFile ~/.ssh/obi_rsa

   User ezeaka01

Example:

ssh ezeaka01@10.61.240.244

``` 

## How to create ssh config

```bash 

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

``` 

  

## Config for extending SSH timeout

  

```bash 

~/.ssh/config

  

Host *

  ServerAliveInterval 120

``` 

  

## File Transfer

  
## Transfer Remote Files with the Secure File Transfer Program
The OpenSSH suite is useful for securely running shell commands on remote systems. Use the
Secure File Transfer Program (SFTP) to interactively upload to or download files from an SSH
server. This program is part of the OpenSSH suite. A session with the sftp command uses the
secure authentication mechanism and encrypted data transfer to and from the SSH server.
Specify a remote location for the source or destination of the files to copy. For the format of the
remote location, use [user@]host:/path. The user@ portion of the argument is optional. If this
portion is missing, then the sftp command uses your current local username. When you run the
sftp command, your terminal provides an sftp> prompt. 

```bash
[user@host ~]$ sftp remoteuser@remotehost
remoteuser@remotehost's password: password
Connected to remotehost.
sftp>

```


The interactive sftp session accepts various commands that work the same way on the remote
file system as in the local file system, such as the ls, cd, mkdir, rmdir, and pwd commands. The
put command uploads a file to the remote system. The get command downloads a file from the
remote system. The exit command exits the sftp session.
List the available sftp commands by using the help command in the sftp session: 

```bash
sftp> help
Available commands:
bye Quit sftp
cd path Change remote directory to 'path'
chgrp [-h] grp path Change group of file 'path' to 'grp'
chmod [-h] mode path Change permissions of file 'path' to 'mode'
chown [-h] own path Change owner of file 'path' to 'own'
...output omitted...

```

In an sftp session, you might want to run some commands on your local host. For most available
commands, add the l character before the command. For example, the pwd command prints the
current working directory on the remote host. To print the current working directory on your local
host, use the lpwd command.

```bash
sftp> pwd
Remote working directory: /home/remoteuser
sftp> lpwd

```

Local working directory: /home/user
The next example uploads the /etc/hosts file on the local system to the newly created /home/
remoteuser/hostbackup directory on the remotehost machine. The sftp session expects
that the put command is followed by a local file in the connecting user's home directory, in this
case the /home/remoteuser directory: 

```bash
sftp> mkdir hostbackup
sftp> cd hostbackup
sftp> put /etc/hosts

```


Uploading /etc/hosts to /home/remoteuser/hostbackup/hosts
/etc/hosts 100% 227 0.2KB/s 00:00
To copy a whole directory tree recursively, use the sftp command -r option. The following
example recursively copies the /home/user/directory local directory to the remotehost
machine. 

```bash
sftp> put -r directory
Uploading directory/ to /home/remoteuser/directory
Entering directory/
file1 100% 0 0.0KB/s 00:00
file2 100% 0 0.0KB/s 00:00
sftp> ls -l
drwxr-xr-x 2 student student 32 Mar 21 07:51 directory

```

To download the /etc/yum.conf file from the remote host to the current directory on the local
system, execute the get /etc/yum.conf command, then exit the sftp session. 

```bash
sftp> get /etc/yum.conf
Fetching /etc/yum.conf to yum.conf
/etc/yum.conf 100% 813 0.8KB/s 00:00
sftp> exit 
```

```bash
[user@host ~]$ 

To get a remote file with the sftp command on a single command line, without opening an
interactive session, use the following syntax. You cannot use single command line syntax to put
files on a remote host. 

[user@host ~]$ sftp remoteuser@remotehost:/home/remoteuser/remotefile
Connected to remotehost.
Fetching /home/remoteuser/remotefile to remotefile
remotefile 100% 7
 15.7KB/s 00:00

```


---
created: 2023-04-24T14:14:46 (UTC +01:00)
tags: []
source: https://comtechies.com/password-authentication-aws-ec2.html
author: byBibin Wilson
---

# How to Setup Password Authentication For AWS ec2 Instances

> ## Excerpt
> In this tutorial, I have added the configurations and steps required for password authentication for ec2 instances. You can setup password for root as well.

---
In this tutorial, I have added the configurations required for ec2 user password authentication for AWS ec2 Linux instances.

## What is the default password for ec2?

**By default, ec2 instances don’t have password authentication**. You have to use the private key to connect to the instances.

However, you might have situations to use ec2 password-based authentication for your ec2 instances. So **it is possible to set up an ec2 user password manually**.

I assume that you have an instance up and running. Follow the steps given below for the ec2 password authentication setup.

Note: I highly discourage using ec2 user password authentication on cloud instances unless required. It is always safe to use private key-based authentication.

Let’s get started with the setup.

**Step 1:** Log in to the server using ssh client of your choice using the private key. For Windows machines, you can use putty for connecting to the instance. If you want the steps, you can follow this article. [Connecting ec2 instance using putty](https://comtechies.com/how-to-connect-an-amazon-ec2-ubuntu-linux-instances-using-putty.html).

If you are using Mac or Linux, you can use the following command to connect to the instance.

```
ssh -i your-key.pem username@(public-ip-address)
```

**Step 2:**  Open the `sshd_config` file.

```
sudo vi /etc/ssh/sshd_config
```

**Step 3:**  Find the line containing “**`PasswordAuthentication`**” parameter and change its value from “**`no`**” to “**`yes`**“

```
PasswordAuthentication yes
```

![image/sshd.png](sshd.png)

If you want to set up “**`root`**” ec2 user password, find  “**`PermitRootLogin`**” parameter and change its value from “**`prohibit-password`**” to “**`yes`**“

After the changes, save the file and exit.

> **Note**: If you are looking for a managed cloud hosting solution using AWS cloud, check out [Cloudways Hosting](https://comtechies.com/recommends/cloudways-hosting). It makes your AWS cloud hosting easy with less administrative overhead.

**Step 4:** Setup ec2 user password using the “**`passwd`**” command along with the username.  

You need to enter the password twice. For example, if you want to set up a password for “**`ubuntu`**” user, use the following command.

```
sudo passwd ubuntu
```

In AWS, different ec2 instances have different user names. Following are the default usernames of common ec2 instances.

<table><tbody><tr><td><strong>Instance</strong></td><td><strong>Username</strong></td></tr><tr><td>Ubuntu</td><td>ubuntu</td></tr><tr><td>Redhat Linux</td><td>ec2-user</td></tr><tr><td>Amazon Linux</td><td>ec2-user</td></tr><tr><td>CentOS</td><td>centos</td></tr><tr><td>Debian</td><td>admin or root</td></tr></tbody></table>

Default ec2 usernames to set password

**Step 5:** Now, restart the “**sshd**” service using the following command.

```
sudo service sshd restart
```

**Step 6:** Now you can log out and log in using the password you set for the user. For example,

```
ssh ubuntu@35.162.225.240
```

I hope this ec2 user password setup article helps. Let me know in the comment section if you face any errors.

##### Also Read

[! Instance Password FAQ’s

### How do I find my EC2 instance password?

By default, the password authentication for ec2 Linux instances is disabled. Therefore, you need to allow PasswordAuthentication and manually create a password for the user. However, for windows ec2 instances, you will get the option to create an admin password while creating the ec2 windows instance.


# Passwordless ssh between two AWS instances – 

  

> ## Excerpt

> Hadoop clusters require passwordless shh between nodes for proper communication. This is all done on the instance you wish to connect FROM! The recipe how I made paswordless shh work between two in…

  

---

Hadoop clusters require passwordless shh between nodes for proper communication.

  

This is all done on the instance you wish to connect FROM!

  

The recipe how I made paswordless shh work between two instances is the following:

  

-   **create ec2 instances** – they should be in the same subnet and have the same security group

-   **Open ports between them** – make sure instances can communicate to each other. Use the default security group which has one rule relevant for this case:

    -   **Type**: All Traffic

    -   **Source**: Custom – id of the security group

-   **Log in** to the instance you want to connect from to the other instance

-   **Run**:

    <table><tbody><tr><td><p>1</p></td><td><div><p><code>ssh</code><code>-keygen -t rsa -N </code><code>""</code> <code>-f </code><code>/home/ubuntu/</code><code>.</code><code>ssh</code><code>/id_rsa</code></p></div></td></tr></tbody></table>

    to generate a new rsa key.

-   Copy your private AWS key as ~/.ssh/my.key (or whatever name you want to use)

-   Make sure you change the permission to 600

  

-   Copy the public key to the instance you wish to connect to passwordless

  

<table><tbody><tr><td><p>1</p></td><td><div><p><code>cat</code> <code>~/.</code><code>ssh</code><code>/id_rsa</code><code>.pub | </code><code>ssh</code> <code>-i ~/.</code><code>ssh</code><code>/my</code><code>.key ubuntu@10.0.0.X </code><code>"cat &gt;&gt; ~/.ssh/authorized_keys"</code></p></div></td></tr></tbody></table>

  

If you test the passwordless ssh to the other machine, it should work.

  

## Post navigation



[[Index]] 