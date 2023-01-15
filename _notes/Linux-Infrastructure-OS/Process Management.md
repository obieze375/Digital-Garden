[[Index]] 

~~~~

Run CPU intensive process on System with nice value of -5 to give more CPU attention than default.  

  

• Adjust the niceness value to 5 so that CPU pays less attention to this process  

  

  

Note : nice value can be between -20 to 19. Lesser the NICE value, more CPU resources will be used. Higher the nice value, less  

  

CPU attention will be given.  

  

  

Never run process with nice value of -20 ,CPU will give highest priority and no other jobs will be able to run.

~~~~

  

Command Action/Description  

  

~~~~

To start process with nice value -5 - nice -n -5 dd if=/dev/zero of=/dev/null  

  

  

To adjust nice value                - renice -n 5 -p PID              

  

  

To verify changes                   - top  

~~~~

  

Run below command in back ground with nice value of 10.

  

~~~~

sleep 3600

~~~~

  

Command Action/Description  

  

~~~~

To start a process with pre-defined nice value -  nice -n 10 sleep 3600 &  

~~~~

~~~~

To verify results -  top  

~~~~

  

# What to do if a process is locked

  
  

# STEP 1:  

  

~~~~

ps aux | grep -i apt  

  

  

sudo kill –9  

  

  

sudo killall apt apt-get

  

~~~~

  

# STEP2:  

  

~~~~

lsof /var/lib/dpkg/lock  

  

  

lsof /var/lib/apt/lists/lock  

  

  

lsof /var/cache/apt/archives/lock  

  

  

sudo kill -9 PID  

  

  

sudo rm /var/lib/apt/lists/lock  

  

  

sudo rm /var/cache/apt/archives/lock  

  

  

sudo rm /var/lib/dpkg/lock    

  

  

sudo dpkg --configure -a

~~~~

# STEP3:  

  

Troubleshoot: dpkg: error: dpkg frontend is locked by another process

If you see the error “dpkg frontend is locked by another process” while running the above described method, you’ll have to do an additional step.

~~~~

First, find out the id of the process that is holding the lock file.

  

  

lsof /var/lib/dpkg/lock-frontend

  

  

The above command will give you the PID of the processes using the lock files. Use this PID to kill the process.

  

sudo kill -9 PID

  

  

Now you can remove the lock and reconfigure dpkg:

  

sudo rm /var/lib/dpkg/lock-frontend sudo dpkg --configure -a  

~~~~