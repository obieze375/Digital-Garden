[[Index]] 

## clear – Clear the terminal window

~~~~

• clear

~~~~

  

## echo $? - Check if previous bash command run was successful 0 means yes and 1 means no

 ~~~~  

 • echo $?

 ~~~~

  

## reset – Resets the terminal

~~~~

• reset

~~~~

  

## history – Lists all recent commands

~~~~

• history

  

history | grep - Search for a specific command from the history

  

• 3. Delete a line from the history with history -d line_number

• 4. If you want your commands not to remain in the history, run them

with a space before them after you will have set

HISTCONTROL=ignorespace

  

• ! e.g. !357 -> re-runs command if entered into terminal

~~~~

  

## xkill – Close a frozen window/application

~~~~

• xkill

~~~~

  

## Tab Completion

~~~~

• Use TAB key for completion of characters on CLI

  

• ctrl + u = Clear everything before the cursor

  

• ctrl + a = To beginning of line

  

• ctrl + e = To end of line

  

• ctrl + b = Back one word

  

• ctrl + f = Forward one word

  

• ctrl + w = Cut last word

  

• ctrl + k = Clear everything after the cursor

  

• ctrl + _ = Undo

~~~~

  

## Alter Screen Resolution

~~~~

• xrandr --output --mode 1920x1200

~~~~

  

## Ctrl + r - Reverse search

~~~~

Type Ctrl+r to open the reverse search tool.

Search for any command from the history and press Ctrl+r again for

the previous one that contain the string you’re looking for.

~~~~

## General commands

~~~~

• ./ - Runs file as executable

  

• -- version – Checks version of installation

  

• wget – Download file over internet

  

• reboot – Restarts the system

  

• Shutdown – shuts down server  

  

shutdown -r -> Shutdowns and reboots the node

  

General commands continued…

• -- help – use to get information on command e.g. ls --help

~~~~

  
  

# tmux

  
  

## To install : yum install tmux

  

## start new:

~~~~

• tmux

~~~~

  

## start new with session name:

  

~~~~

• tmux new -s myname  

~~~~

## Attach:

  

#tmux a  #  (or at, or attach)

  

Attach to named:  

  

~~~~

• tmux a -t myname

~~~~

  

## list sessions:

       ~~~~

  • tmux ls

       ~~~~

## kill session:

~~~~

• tmux kill-session -t myname

~~~~

  

## Kill all the tmux sessions:

  

~~~~

tmux ls | grep : | cut -d. -f1 | awk '{print substr($1, 0, length($1)-1)}' | xargs kill

~~~~

In tmux, hit the prefix ctrl+b (my modified prefix is ctrl+a) and then:

  

From <https://gist.github.com/MohamedAlaa/2961058>

  
  
  

## 4 pane window:

~~~~

tmux new-window \; split-window -p 66 \; split-window -d \; split-window -h

~~~~

  

The flow is:

~~~~

  1. tmux new-window: create a window (ok, you wanted a new-session, that does create a window upon startup)

  2. split-window -p 66: allocate bottom two thirds of the vertical space to a secondary pane and focus it

  3. split-window -d: split bottom pane in half, vertically, without focusing the new pane (i.e. focus stays on second – now center – pane)

  4. split-window -h: split center pane in half, horizontally

~~~~

  

From <https://superuser.com/questions/1155771/tmux-split-into-4-panes>

  
  

~~~~

:new<CR>  new session

s  list sessions

$  name session

~~~~

From <https://gist.github.com/MohamedAlaa/2961058>

~~~~

Panes (splits)

%  vertical split

"  horizontal split

o  swap panes

q  show pane numbers

x  kill pane

+  break pane into window (e.g. to select text by mouse to copy)

-  restore pane from window

⍽  space - toggle between layouts

<prefix> q (Show pane numbers, when the numbers show up type the key to goto that pane)

<prefix> { (Move the current pane left)

<prefix> } (Move the current pane right)

<prefix> z toggle pane zoom

  

From <https://gist.github.com/MohamedAlaa/2961058>

~~~~

~~~~

Windows (tabs)

c  create window

w  list windows

n  next window

p  previous window

f  find window

,  name window

&  kill window

~~~~

From <https://gist.github.com/MohamedAlaa/2961058>

  

## Sync Panes

You can do this by switching to the appropriate window, typing your Tmux prefix (commonly Ctrl-B or Ctrl-A) and then a colon to bring up a Tmux command line, and typing:  

~~~~  

:setw synchronize-panes

~~~~

~~~~

You can optionally add on or off to specify which state you want; otherwise the option is simply toggled. This option is specific to one window, so it won’t change the way your other sessions or windows operate. When you’re done, toggle it off again by repeating the command.

  

From <https://gist.github.com/MohamedAlaa/2961058>

  

d  detach

t  big clock

?  list shortcuts

:  prompt

~~~~

From <https://gist.github.com/MohamedAlaa/2961058>  

  
  
  

# Crontab

  

~~~~

[Crontab schedule]

+---------------- minute (0 - 59)

|  +------------- hour (0 - 23)

|  |  +---------- day of month (1 - 31)

|  |  |  +------- month (1 - 12)

|  |  |  |  +---- day of week (0 - 6) (Sunday=0)

|  |  |  |  |

*  *  *  *  * command to be executed <script>

-- -- -- -- - ---------------------------------

~~~~


~~~~

crontab  -e  

  

crontab -l | grep <script_name>

  
 ~~~~
 

# Check Version

  

~~~~

cat /etc/oracle-release

~~~~

  

# Diagnostics

  

## RAM

~~~~

  • free -th

~~~~

  

## RAM & CPU

  

~~~~

top

  

top –c - Filtering

~~~~

## OS:

  

~~~~  

hostnamectl

~~~~

  

## SAR:

  

## Basic Output:

~~~~

sar  

~~~~

## CPU Usage per Core:

~~~~

sar -P ALL

~~~~

## Memory Usage:

~~~~

sar -r  

~~~~

## Swap Usage:

~~~~

sar -S

~~~~

  

From <https://www.gxd88.cn/sar>  

  

## I/O

~~~~

sar -b

~~~~

  

## I/O by Block Device:

~~~~

sar -d -p

~~~~

## Check Run queue and Load Average:

~~~~

sar -q

~~~~

  

## Network Stats:

~~~~

 sar -n DEV

  

Where DEV can be one of the following

  

DEV – Displays network devices vital statistics for eth0, eth1, etc.,

  

EDEV – Display network device failure statistics

  

NFS – Displays NFS client activities

  

NFSD – Displays NFS server activities

  

SOCK – Displays sockets in use for IPv4

  

IP – Displays IPv4 network traffic

  

EIP – Displays IPv4 network errors

  

ICMP – Displays ICMPv4 network traffic

  

EICMP – Displays ICMPv4 network errors

  

TCP – Displays TCPv4 network traffic

  

ETCP – Displays TCPv4 network errors

  

UDP – Displays UDPv4 network traffic

  

SOCK6, IP6, EIP6, ICMP6, UDP6 are for IPv6

  

ALL – This displays all of the above information. The output will be very long.

~~~~

  

## Historic Information:

~~~~

 sar -f /var/log/sa/sa15 -n DEV

~~~~

  

## Uptime:

  

~~~~

 w

~~~~

## Windows Shortcut Notes

~~~~

 

~~~~


# nohup & disown command usage

~~~~

  

nohup <bash_command> & disown

  

 -> If you use all three together, the process is running in the background, is removed from the shell's job control and is effectively disconnected from the terminal

~~~~




[[Index]] 