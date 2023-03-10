[[Index]] 

# Streams

Streams networking was invented for Unix Version 8 (1985) by Dennis Ritchie. A re-implementation called STREAMS (yes, it is all-capitals in the documentation) first became available in the 3.0 release of System V Unix (1986). The STREAMS facility provided a full-duplex interface (functionally not unlike a BSD socket, and like sockets, accessible through normal read(2) and write(2) operations after initial setup) between a user process and a specified device driver in the kernel. The device driver might be hardware such as a serial or network card, or it might be a software-only pseudo device set up to pass data between user processes.

An interesting feature of both streams and STREAMS76 is that it is possible to push protocol- translation modules into the kernel’s processing path, so that the device the user process ‘sees’ through the full-duplex channel is actually filtered. This capability could be used, for example, to implement a line-editing protocol for a terminal device. Or one could implement protocols such as IP or TCP without wiring them directly into the kernel.

Streams originated as an attempt to clean up a messy feature of the kernel called ‘line disciplines’ — alternative modes of processing character streams coming from serial terminals and early local-area networks. But as serial terminals faded from view, Ethernet LANs became ubiquitous, andTCP/IP drove out other protocol stacks and migrated into Unix kernels, the extra flexibility provided by STREAM Shadless and less utility. In 2003,System V Unix still supports STREAMS,as do some System V/BSD hybrids such as Digital Unix and Sun Microsystems’ Solaris.

Linux and other open-source Unixes have effectively discarded STREAMS. Linux kernel modules and libraries are available from the LiS [http://www.gcom.com/home/linux/lis/] project, but (as of mid-2003) are not integrated into the stock Linux kernel. They will not be supported under non- Unix operating systems.

[[Index]] 

