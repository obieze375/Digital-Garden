## Internet protocol

[[Index]] 
 
[[Basic of Networking - DevOps Training]]

[[Internet protocol - DevOps Training]] 

[[Basic of Networking - DevOps Training]]

[[OSI Model - DevOps Training]]

[[Network address and Host address - DevOps Training]] 

[[Subnetting Type - DevOps Training]]

[[Network Architecture - DevOps Training]] 

[[Networking Layers OSI Model - DevOps Training]] 

[[Internet protocol - DevOps Training]] 

[[CIDR and subnetting - DevOps Training]] 

[[AWS VPC - DevOps Training]] 

[[AWS VPC Subnets - DevOps Training]]

Each device connected to the internet has a unique identifier. Most networks today, including all computers on the internet, use the **TCP/IP a**s a standard to communicate on the network. In the TCP/IP protocol, this unique identifier is the **IP Address**. The two kinds of IP Addresses are **IPv4**and **IPv6**.

**IPv4** uses 32 binary bits to create a single unique address on the network. An IPv4 address is expressed by four numbers separated by dots. Each number is the decimal (base-10) representation for an eight-digit binary (base-2) number, also called an octet.

![](1_T-XFf3kOvko_are9ayCJKg.png)

**IPv6** uses 128 binary bits to create a single unique address on the network. An IPv6 address is expressed by eight groups of hexadecimal (base-16) numbers separated by colons. Groups of numbers that contain all zeros are often omitted to save space, leaving a colon separator to mark the gap .

![](1_ByM8gaytcWsdiSpOkzYuAA.png)

IPv6 space is much larger than the IPv4 space due the use of hexadecimals as well as having 8 groups. Most devices use IPv4. However, due to advent of IoT devices and the greater demand for IP Addresses, more and more devices are accepting IPv6.

IPv4 addresses are normally expressed in dot-notation `xxx.xxx.xxx.xxx`where `xxx` is a value from 0 to 255. But another way to express them is as a 4-tuple of _octets_, which is an 8-bit segment since 2⁸=256. Here is the same IPv4 address in both dot-notation and 4-tuple octet.

172.217.6.3610101100 11011001 00000110 00100100

IPv6 addresses are normally expressed in colon-notation as `xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx` where `xxxx` is a hexadecimal value. We can express them as an 8-tuple of 16-bit segments. Here is the same IPv6 address as an 8-tuple of 16 bits.

2001:0db8:0012:0001:3c5e:7354:0000:5db10010000000000001 0000110110111000 0000000000010010 0000000000000010

0011110001011110 0111001101010100 0000000000000000 0101110110110001

### 

Network Prefix and Host Identifier

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#9b15)

The Internet is not a single large network, but rather a collection of networks. One of these _networks_ may be a college campus network; another of these _networks_ may be a metro-wide ISP’s _network_, and they connect to each other through [internet exchange points](https://en.wikipedia.org/wiki/Internet_exchange_point).

IPv4 addresses are comprised of two parts. The first part is the _network prefix_, which identifies the network the address belongs to. The second part is the _host identifier_, which identifies the host within that network.

Where the _network prefix_ ends and where the _host identifier_ begins depends on the _class_ of the IPv4 address.

### 

IPv4 Address Classification

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#5e33)

There are 5 classes of IPv4 addresses, labeled _A_ through _E_. The class of the IP address is determined by the first 4 bits.

-   Class A — IP addresses are in this class if their first bit is a `0.` In dot-notation, this is the range `0.0.0.0` to `127.255.255.255` . The first 8 bits represent the _network prefix_ and the rest represents the _host identifier_. For example, `127.42.13.69` has _network prefix_ `127` and _host identifier_`42.13.69` .
    

-   Class B — IP addresses are in this class if their first two bits are `10` . In dot-notation, this is the range `128.0.0.0` to `191.255.255.255` . The first 16 bits represent the _network prefix_ and the rest represent the _host identifier_. For example, `129.42.13.69` has _network prefix_ `129.42` and _host identifier_ `13.69` .
    

-   Class C — IP addresses are in this class if their first three bits are `110` . In dot-notation, this is the range `192.0.0.0` to `223.255.255.255` . The first 24 bits represent the _network prefix_ and the rest represent the _host identifier_. For example, `196.13.42.69` has _network prefix_ `196.13.42` and _host identifier_ `69` .
    

-   Class D — IP addresses are in this class if their first four bits are `1110` . In dot-notation, this is the range `224.0.0.0` to `239.255.255.255` . These addresses are used for multi-casting protocols (ie. when a single packet can be sent to multiple hosts in one action)
    

-   Class E — IP addresses are in this class if their first four bits are `1111` . In dot-notation, this the range `240.0.0.0` to `255.255.255.255` . These addresses are reserved for future and experimental use.
    

Some IPv4 addresses are reserved for specific uses, namely l_oopback IPs_ and_Private IPs_.

The IPv4 address range `127.0.0.0` to `127.255.255.255` is reserved for _looping back_, which is when a host sends a network request to itself. Sometimes we want a program on a host to connect back to itself for debugging or development purposes.

The IP ranges `10.0.0.0 — 10.xxx.xxx.xxx` , `172.16.0.0 — 172.31.xxx.xxx` , and `192.168.0.0 — 192.168.xxx.xxx` are designated private network addresses, meaning they can be assigned to computers which must go through the [Network Address Translation (NAT) protocol](https://en.wikipedia.org/wiki/NAT_Port_Mapping_Protocol) to connect to the Internet. It’s _private IPs_ that make it possible for over 8 billion devices to connect with only about 4 billion IPv4 address (2³² =~ 4 billion).

A _subnetwork_ or _subnet_ is basically a smaller network within a larger network. The process of partitioning a network into _subnets_ is called _subnetting._ Each computer on the same _subnet_ can communicate directly with each other but not directly with computers on a different _subnet_. This is usually done for security or performance reasons.

As stated earlier, IPv4 addresses are comprised by a _network prefix_ and _host identifier_. _Subnetting_ is done by partitioning the _IP address_ into three parts, a _network prefix_, a _subnet number_, and _host identifier_. The specification of where these numbers start and end in the _IP address_ is done through a _net mask._

A _netmask_ is used to describe which segments of the _IP address_ are the _network prefix_ and _host identifier_. Namely, the _netmask_ is a 4-tuple of octets, that specify which segment of the _IP address_ as part of the _network prefix_ by using a `1` for every position that corresponds to a _network_ _prefix_, and `0`otherwise. In other words, we get the _network prefix_ through bit-wise multiplication of the _IP address_ and the _netmask_.

For example, the _default netmask_ for Class A _IP addresses_ would be `11111111 00000000 00000000 00000000` as binary or `255.0.0.0` in dot-notation.

The _default netmask_ for Class B _IP addresses_ would be `11111111 11111111 00000000 00000000` as binary or `255.255.0.0` in dot-notation.

The _default netmask_ for Class C _IP addresses_ would be `11111111 11111111 11111111 00000000` as binary or `255.255.255.0` in dot-notation. 

[[Index]] 
 
[[Basic of Networking - DevOps Training]]

[[Internet protocol - DevOps Training]] 

[[Basic of Networking - DevOps Training]]

[[OSI Model - DevOps Training]]

[[Network address and Host address - DevOps Training]] 

[[Subnetting Type - DevOps Training]]

[[Network Architecture - DevOps Training]] 

[[Networking Layers OSI Model - DevOps Training]] 

[[Internet protocol - DevOps Training]] 

[[CIDR and subnetting - DevOps Training]] 

[[AWS VPC - DevOps Training]] 

[[AWS VPC Subnets - DevOps Training]]