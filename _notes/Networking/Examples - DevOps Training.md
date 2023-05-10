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

Given the CIDR representation 20.10.30.35 / 27. Find the range of IP Addresses in the CIDR block.

Given CIDR representation is 20.10.30.35 / 27.

-   27 bits are used for the identification of network.
    

-   Remaining 5 bits are used for the identification of hosts in the network.
    

Given CIDR IP Address may be represented as-

00010100.00001010.00011110.00100011 / 27

-   First IP Address = 00010100.00001010.00011110.001**00000** = 20.10.30.32
    

-   Last IP Address = 00010100.00001010.00011110.001**11111** = 20.10.30.63
    

Thus, Range of IP Addresses = \[ 20.10.30.32 , 20.10.30.63\]

Given the CIDR representation 100.1.2.35 / 20. Find the range of IP Addresses in the CIDR block.

Given CIDR representation is 100.1.2.35 / 20.

-   20 bits are used for the identification of network.
    

-   Remaining 12 bits are used for the identification of hosts in the network.
    

Given CIDR IP Address may be represented as-

01100100.00000001.00000010.00100011 / 20

-   First IP Address = 01100100.00000001.0000**0000.00000000** = 100.1.0.0
    

-   Last IP Address = 01100100.00000001.0000**1111.11111111** = 100.1.15.255
    

Thus, Range of IP Addresses = \[ 100.1.0.0 , 100.1.15.255\]

Consider a block of IP Addresses ranging from 100.1.2.32 to 100.1.2.47.

-   2.
    
    If yes, give the CIDR representation.
    

For any given block to be a CIDR block, 3 rules must be satisfied-

-   According to Rule-01, all the IP Addresses must be contiguous.
    

-   Clearly, all the given IP Addresses are contiguous.
    

-   So, Rule-01 is satisfied.
    

-   According to Rule-02, size of the block must be presentable as 2n.
    

-   Number of IP Addresses in the given block = 47 – 32 + 1 = 16.
    

-   Size of the block = 16 which can be represented as 24.
    

-   So, Rule-02 is satisfied.
    

-   According to Rule-03, first IP Address must be divisible by size of the block.
    

-   So, 100.1.2.32 must be divisible by 24.
    

-   100.1.2.32 = 100.1.2.0010**0000** is divisible by 24 since its 4 least significant bits are zero.
    

-   So, Rule-03 is satisfied.
    

Since all the rules are satisfied, therefore given block is a CIDR block.

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