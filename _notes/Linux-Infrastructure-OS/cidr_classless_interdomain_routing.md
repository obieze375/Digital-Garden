[[Index]] 

The most critical component of networking is the IP address. Every time you surf the internet, your browser is connected to its remote server using an IP address. You cannot use the internet or network without one.

An IP address is a 32-bit number divided into four 8-bit sections called octets. It can be represented in both decimal and binary formats. An IP address may contain a subnetwork that’s different from the host. The address comes with a subnet mask that distinguishes the part of the IP address that is the network and the part that is the host address.

For example, given an IP address of 192.168.12.20 with the subnet mask of 255.255.255.0, 192.168.12 represents a network address and .20 represents a host address. The concept of a netmask leads us to the idea of classful addressing, which divides the 32-bit IP address into 5 sub-classes.

In classful addressing, all IP addresses have an 8-bit, 16-bit. or 24-bit network prefix. Class A has an 8-bit long network ID and a 24-bit host ID. There are over 16 million class A addresses. Class B has network and host IDs of 16 bits each—there are 65,535 class B addresses. Class C holds the smallest networks—254 addresses. Each Class C network ID is 24 bits long with an 8-bit long host.

When ordering IP addresses, you want to keep in mind the size of your network and order a class that fits your needs. It’s conceptually easy to do this when you have very large or small networks. But problems arise in the middle when you’re in between Class B and C: you need more than 254 addresses but less than 65,535.

Let’s use an example. Let’s assume that you need 1000 addresses in your network. It’s more than 254, so you have to go with the next largest class—Class B. But now you’re only occupying 1,000 addresses and left with 65,000 unused ones. It doesn’t make sense. One solution to this could be to use multiple class C ranges. But having a huge number of small networks makes routing overly complicated! In our search for a new solution to this IP trolley problem, we’ve started to break networks using Classless Inter-Domain Routing.

Instead of having network classes with fixed sizes, network administrators are allowed to move the subnet boundary to anywhere inside the parent network. In other words, we are no longer limited by 8-bit, 16-bit, or 24-bit netmasks.

Let’s go back to our example. Imagine that we have an address that gives us 254 hosts..but we want 300 hosts. Using the old solution, you could get two Class C ranges (making your life more complicated). Now with Classless Interdomain Routing, instead of getting an additional Class C network, we can simply decrease our netmask bits by one and get a network that has 510 hosts. That’s much more reasonable!

The table below outlines the most common combination of addresses and netmasks and important details about them.

<table><tbody><tr><td><strong>Prefix</strong></td><td><strong>Netmask</strong></td><td><strong>Number of addresses</strong></td><td><strong>Relation to class</strong></td><td><strong>Comment</strong></td></tr><tr><td>/32</td><td>255.255.255.255<br></td><td>1</td><td>Class C/256</td><td>Single host in a network</td></tr><tr><td>/25</td><td>255.255.255.128<br></td><td>128</td><td>Class C/2</td><td><br></td></tr><tr><td>/24</td><td>255.255.255.0<br></td><td>256<br></td><td>Class C</td><td><br></td></tr><tr><td>/23</td><td>255.255.254.0<br></td><td>512</td><td>Class C*2</td><td><br></td></tr><tr><td>/16</td><td>255.255.0.0<br></td><td>65,536<br></td><td>Class C*256 = Class B</td><td><br></td></tr><tr><td>/15</td><td>255.254.0.0<br></td><td>131,072<br></td><td>Class B*2</td><td><br></td></tr><tr><td>/8</td><td>255.0.0.0</td><td>16,777,216<br></td><td>Class B*256 = Class A</td><td><br></td></tr><tr><td>/0</td><td>0.0.0.0</td><td>4,294,967,296<br></td><td>Class A*256</td><td>0.0.0.0/0 means entire internet. Often used in public firewall rules</td></tr></tbody></table>



# CIDR (Classless InterDomain Routing)

CIDR (Classless Inter-Domain Routing) was introduced in 1993 (RCF 1517) replacing the previous generation of IP address syntax - classful networks. CIDR allowed for more efficient use of IPv4 address space and prefix aggregation, known as route summarization or supernetting.

CIDR introduction allowed for:

* More efficient use of IPv4 address space
* Prefix aggregation, which reduced the size of routing tables

CIDR allows routers to group routes together to reduce the bulk of routing information carried by the core routers. With CIDR, several IP networks appear to networks outside the group as a single, larger entity. With CIDR, IP addresses and their subnet masks are written as four octets, separated by periods, followed by a forward slash and a two-digit number that represents the subnet mask e.g.

**10.1.1.0/30**

**172.16.1.16/28**

**192.168.1.32/27** etc.

CIDR / VLSM Network addressing topology example

![](cidr.png)

CIDR uses VLSM (Variable Lenght Subnet Masks) to allocate IP addresses to subnetworks according to need rather than class. VLSM allows for subnets to be further divided or subnetted into even smaller subnets. Simply, VLSM is just subnetting a subnet.

With CIDR, address classes (Class A,  B, and C) became meaningless. The network address was no longer determined by the value of the first octet, but assigned prefix length (subnet mask) address space. The number of hosts on a network, could now be assigned a specific prefix depending upon the number of hosts needed for that network.

Propagating CIDR supernets or VLSM subnets require a classless Routing Protocols – . A classless routing protocol includes the subnet mask along with the network address in the routing update.


**Summary routes determination**

Determining the summary route and subnet mask for a group of networks can be done in three easy steps:

1. To list the networks in binary format.
2. To count the number of left-most matching bits. This will give you the prefix length or subnet mask for the      summarized route.
3. To copy the matching bits and then add zero bits to the rest of the address to determine the          summarized network address.
 
The summarized network address and subnet mask can now be used as the summary route for this group of networks. Summary routes can be used by both static routes and classless routing protocols. Classful routing protocols can only summarize routes to the default classful mask.

ISPs could now more efficiently allocate address space using any prefix length, ISPs were no longer limited to a- 255.0.0.0 or /8,  255.255.0.0 or /16, or 255.255.255.0 or /24 subnet mask which before the advent of CIDR is known as classful network addresses.  Blocks of IP addresses could be assigned to a network based on the requirements of the customer, ranging from a few hosts to hundreds or thousands of hosts.

### CIDR Advantages

With the introduction of CIDR and VLSM, ISPs could now assign one part of a classful network to one customer and different part to another customer. With the introduction of VLSM and CIDR, network administrators had to use additional subnetting skills. 

The table below  shows allowed subnet and Hosts IP address for all The Classes

|Subnet mask bits|Number of /24 subnets|Number of addresses|Bits stolen
|--|--|--|--
|/24|1|256|0
|/25|2|128|1
|/26|4|64|2
|/27|8|32|3
|/28|16|16|4
|/29|32|8|5
|/30|64|4|6
|/31|128|2|7

|Subnet Number|Network Address|First IP|Last IP|Broadcast Address
|--|--|--|--|--
|1|2.2.2.0|2.2.2.1|2.2.2.6|2.2.2.7
|2|2.2.2.8|2.2.2.9|2.2.2.14|2.2.2.15
|3|2.2.2.16|2.2.2.17|2.2.2.22|2.2.2.23
|32|2.2.2.249|2.2.2.250|2.2.2.254|2.2.2.255


![](CIDR_desktop.jpg)

![](800px-IP_Address_Match.svg.png)

![](CIDR_Address.svg.png)