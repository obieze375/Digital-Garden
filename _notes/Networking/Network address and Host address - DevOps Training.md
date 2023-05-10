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

An IP address is a unique identity of an interface in IP network. IP addresses are just like postal addresses. In order to send and receive packages through postal system, every house needs a unique postal address. Just like it, in order to send and receive IP packets in IP network, every interface needs a unique IP address.

An IP address consists 32 bits. These bits are divided in four equal sections. Sections are separated by periods and written in a sequence.

![](csg07-01-ip-address.png)

In measurement, 8 bits are equal to one byte or octet. So we can also say an IP address consists four bytes or octets separated by periods.

Two popular notations are used for writing an IP address, binary and decimal.Advertisements

In binary notation, all four octets are written in binary format. For example, few IP addresses in binary format are listed below.

00001010.00001010.00001010.00001010

10101100.10101000.00000001.00000001

11000000.10101000.00000001.00000001

In decimal notation, all four octets are written in decimal format. A decimal equivalent value of the octet is used in each section. For example, IP addresses from above example are listed below in decimal format.

In real life you rarely need to write an IP address in binary format. But if you are preparing for any Cisco exam, I highly recommend you to learn the binary format along with the decimal format. Nearly all Cisco exams include questions about IP addresses. Learning both binary and decimal notations will help you in solving IP addressing related questions more effectively.

This tutorial is the first part of the article “**IP Subnetting in Computer Network Step by Step Explained with Examples**”. Other parts of this article are following.

_This tutorial is the second part of the article. It explains what Subnetting is and why it is necessary in computer network along with the advantages of Subnetting._

_This tutorial is the third part of the article. It explains the Subnetting concepts and terms such as network id, broadcast id, total hosts, valid hosts, power of 2, block size and CIDR in detail._

_This tutorial is the fourth part of the article. It explains how to solve or answer any Subnetting related question in less than a minute with 50+ Subnetting examples._

_This tutorial is the fifth part of the article. It explains what VLSM Subnetting is and how it is done step by step including differences between FLSM Subnetting and VLSM Subnetting._

_This tutorial is the sixth part of the article. It explains VLSM Subnetting examples for Cisco exams and interviews._

_This tutorial is the last part of the article. It explains Supernetting in detail with examples._

As we discussed earlier, an IP address is just like a postal address. Whether it is a postal address or an IP address, it contains two addresses, group address and individual address. In a particular group, the group address is common for all members and the individual address is unique for each member.

In postal system, group address and individual addresses are known as area address and house addresses. While in IP network, these addresses are known as network address and host addresses respectively.

Following figure shows few examples of addresses from both postal system and IP network.

![](csg07-02-ip-address-vs-network-address.png)

IP address and subnet mask

In an IP address, how many bits are used in network address and how many bits are left for host address is determined by a subnet mask. Just like an IP address, subnet mask is also a 32 bits long address and can be written in both binary and decimal notations.

Examples of subnet mask in binary notation are following: -

11111111.00000000.00000000.00000000

11111111.11111111.00000000.00000000

11111111.11111111.11111111.00000000

Examples of subnet mask in decimal notation are following: -

IP address and subnet mask are always used together. Without IP address, subnet mask is just a number and vice versa. Few examples of writing IP address in correct way are listed below.

Examples of IP address with subnet mask in binary format

00001010.00001010.00001010.00001010

11111111.00000000.00000000.00000000

10101100.10101000.00000001.00000001

11111111.11111111.00000000.00000000

11000000.10101000.00000001.00000001

11111111.11111111.11111111.00000000

Examples of IP address with subnet mask in decimal format

There are 4,294,967,296 IP addresses. Based on following rules, IP addresses are categorized in five classes; A, B, C, D and E.Advertisements

-   In class A, first bit of the first byte always remains off (0).
    

-   In class B, first bit of first byte always remains on and the second bit of the first byte always remains off.
    

-   In class C, first two bits of first byte always remain on and the third bit of the first byte always remains off.
    

-   In class D, first three bits of first byte always remain on and the fourth bit of the first byte always remains off.
    

-   In class E, first four bits of first byte always remain on.
    

By turning all remaining bits of the first byte on and off, we can make first and last address of that class.

<table><tbody><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="ff9cf747db894cada0b303f8691f4a17" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="1356bc7b655b43f6ae1b91f871e842a6"><span data-offset-key="1356bc7b655b43f6ae1b91f871e842a6:0">Class</span></span></p></div></td><td><div data-key="36ae11f76d6e476cb17f6e11f6397f6d" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="6fe5d05f74d9443993f4c6ca00c54e52"><span data-offset-key="6fe5d05f74d9443993f4c6ca00c54e52:0">Starting bit(s) in binary</span></span></p></div></td><td><div data-key="00b58db5b87744aa9b9d069ab1ef1152" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="1cfda1665b57452b993cb09d6c194430"><span data-offset-key="1cfda1665b57452b993cb09d6c194430:0">Decimal Value of first octet in range</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="b0c828098e0a493496ba461afc77722b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="6383217fe3a8430a800cb354c33b336a"><span data-offset-key="6383217fe3a8430a800cb354c33b336a:0">A</span></span></p></div></td><td><div data-key="ed31120344184b79af81d4330f6e6560" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="e007d3807891462388802d7dc47365b4"><span data-offset-key="e007d3807891462388802d7dc47365b4:0">0</span></span></p></div></td><td><div data-key="e0c661bcb167496bba5bd37d38e07b9a" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="d845927578294fbfb30ca35af23dcafa"><span data-offset-key="d845927578294fbfb30ca35af23dcafa:0">0 to 127</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="7740795a3733491b8a575728e4657933" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="bec7e4f8e6704cd3a2d9a9315a40a4d3"><span data-offset-key="bec7e4f8e6704cd3a2d9a9315a40a4d3:0">B</span></span></p></div></td><td><div data-key="67ec5d75e57a4986be8deee520b54b24" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="48f6dc6b39324d84926abcdb06711771"><span data-offset-key="48f6dc6b39324d84926abcdb06711771:0">10</span></span></p></div></td><td><div data-key="bac0ef2ef3874fa1a32ad6d1844e383f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="2159b7498bdc43ecb3afd2997b523ed8"><span data-offset-key="2159b7498bdc43ecb3afd2997b523ed8:0">128 to 191</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="2ca0c08869e946ed91cbb21bddc622c7" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="0d56d44932854588acb70fdd0cf27b50"><span data-offset-key="0d56d44932854588acb70fdd0cf27b50:0">C</span></span></p></div></td><td><div data-key="a4a4476bb5e042788e679af14246f68f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c4562b1e24da4ad2bcbbfd4e8dd7218c"><span data-offset-key="c4562b1e24da4ad2bcbbfd4e8dd7218c:0">110</span></span></p></div></td><td><div data-key="5782083702584f32855b6a66f024bce6" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="7b310c68a269450eadcf3f5ca54420b5"><span data-offset-key="7b310c68a269450eadcf3f5ca54420b5:0">192 to 223</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="1ab07713b27d496a918f73627caf049a" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="942fec964ae0461fb82e2bd6a9653dcb"><span data-offset-key="942fec964ae0461fb82e2bd6a9653dcb:0">D</span></span></p></div></td><td><div data-key="247484db6fd84a94bd7c0df2818df5f0" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="db64de89e90b433f8f252de68c670f24"><span data-offset-key="db64de89e90b433f8f252de68c670f24:0">1110</span></span></p></div></td><td><div data-key="5f5ef4ee41e04748910290bd8a3d7b4f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="f3eeea1dd5c54ce8b6e1fe774e800fa5"><span data-offset-key="f3eeea1dd5c54ce8b6e1fe774e800fa5:0">224 to 239</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="c63f311fcbd24f4aa5c7ab416351f643" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="dfd905f2157a4857aef85765b35cedf4"><span data-offset-key="dfd905f2157a4857aef85765b35cedf4:0">E</span></span></p></div></td><td><div data-key="71fed8644a4e47ebbb5b2cf7b6b0d9ae" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="76bbf5aa194045e4aee33644f69bbdc9"><span data-offset-key="76bbf5aa194045e4aee33644f69bbdc9:0">1111</span></span></p></div></td><td><div data-key="43f7c10f127f4b5fbc4d47186e4cc127" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="99585753b7084a40879dad641b879418"><span data-offset-key="99585753b7084a40879dad641b879418:0">240 to 255</span></span></p></div></td></tr></tbody></table>

Class of an IP address is determined by the value of first byte or octet.

-   If value in first byte is in range **0 to 127**, it is a Class **A** address.
    

-   If value in first byte is in range **128 to 191**, it is a Class **B** address.
    

-   If value in first byte is in range **192 to 223**, it is a Class **C** address.
    

-   If value in first byte is in range **224 to 239**, it is a Class **D** address.
    

-   If value in first byte is in range **240 to 255**, it is a Class **E** address.
    

<table><tbody><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="bf99929754044af08734a4f9978d1aa0" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="72bfd65f201141b49928202629ba36a8"><span data-offset-key="72bfd65f201141b49928202629ba36a8:0">Class</span></span></p></div></td><td><div data-key="2dd7d419286f4d8090c3782e09a2c827" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="6c10e4a449714e8d9b652b9912f70636"><span data-offset-key="6c10e4a449714e8d9b652b9912f70636:0">Starting Address</span></span></p></div></td><td><div data-key="b7928d606a44481884d7670ec92d674c" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c3d590b7884e4b6a89097307c0445f9a"><span data-offset-key="c3d590b7884e4b6a89097307c0445f9a:0">Ending Address</span></span></p></div></td><td><div data-key="25f6bacd5b9448029d4b1e8b82cc806e" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="caa42332d2af45c0af18e2c580bc4385"><span data-offset-key="caa42332d2af45c0af18e2c580bc4385:0">Subnet mask</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="6adcae3d0b424c8a9684e69c77569393" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="06f4166f1386416d9733f49be8a027ca"><span data-offset-key="06f4166f1386416d9733f49be8a027ca:0">A</span></span></p></div></td><td><div data-key="94daee3c854d4c8e9f7fc451759ee9d5" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="ffba678aaa774c2a89cbb6cb281741a9"><span data-offset-key="ffba678aaa774c2a89cbb6cb281741a9:0">0.0.0.0</span></span></p></div></td><td><div data-key="2e711918f1654304bace10b5eec2bc5a" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="6bb8a7d164b44fe7aec1add952014752"><span data-offset-key="6bb8a7d164b44fe7aec1add952014752:0">127.255.255.255</span></span></p></div></td><td><div data-key="4ec7cf2269e74805859f778b40a2ed36" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="661cec0de4184d948d034443536d117e"><span data-offset-key="661cec0de4184d948d034443536d117e:0">255.0.0.0</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="44a921a31bf048cf9be30596f201b9f1" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="3e6a218266b443c98c0be0c5614ecfb0"><span data-offset-key="3e6a218266b443c98c0be0c5614ecfb0:0">B</span></span></p></div></td><td><div data-key="0ecd535f36a044f4960351299bdc6de5" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="d749b4682fed45bca889034457892b3a"><span data-offset-key="d749b4682fed45bca889034457892b3a:0">128.0.0.0</span></span></p></div></td><td><div data-key="29ee7f4902b94b389c333e442ef1292c" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="e9890cc466914a10be3fb8b9907313bf"><span data-offset-key="e9890cc466914a10be3fb8b9907313bf:0">191.255.255.255</span></span></p></div></td><td><div data-key="df3d3786e9d140ad8fc42155e0b025e5" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="54bca90a064a4a72a4bd9a12f2434603"><span data-offset-key="54bca90a064a4a72a4bd9a12f2434603:0">255.255.0.0</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="562e914331c4490cb298a6b297eda9ee" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="4e52a67493a943b18a69669df4c9601f"><span data-offset-key="4e52a67493a943b18a69669df4c9601f:0">C</span></span></p></div></td><td><div data-key="53f5b53a939646d88f6294d67818f677" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="93e5871ec3b44db3b0e10bbe9dcea444"><span data-offset-key="93e5871ec3b44db3b0e10bbe9dcea444:0">192.0.0.0</span></span></p></div></td><td><div data-key="11d9e2111bd64c179817e7158d835102" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="71d67c0549054ee4bc547ec362e7a0ee"><span data-offset-key="71d67c0549054ee4bc547ec362e7a0ee:0">223.255.255.255</span></span></p></div></td><td><div data-key="7416d9523a594fb89709054806eb67ab" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="25b3b14619364106acd81d762aded780"><span data-offset-key="25b3b14619364106acd81d762aded780:0">255.255.255.0</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="b2ac1f4833cc474b909d607077f52cfe" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c6d35129ab7b41c49ab5e400afe236ef"><span data-offset-key="c6d35129ab7b41c49ab5e400afe236ef:0">D</span></span></p></div></td><td><div data-key="700d8b928217473a9907e519823aacca" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="0d23484670674f2a9ddb0282d98f0326"><span data-offset-key="0d23484670674f2a9ddb0282d98f0326:0">224.0.0.0</span></span></p></div></td><td><div data-key="b75b2d1ee3654c31b52ad292a4fef268" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="ea9b75c261e94b978544c1df3b258d23"><span data-offset-key="ea9b75c261e94b978544c1df3b258d23:0">239.255.255.255</span></span></p></div></td><td><div data-key="db6ffe08fc5e4ab580afad9216bcca95" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="f968a0402bc7487f84e858ae63248917"><span data-offset-key="f968a0402bc7487f84e858ae63248917:0">Not applicable</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="2f51a4ca8d0e4e558f331dbf4f61e487" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="bb8e68da95764855ba78738e5d2b00c5"><span data-offset-key="bb8e68da95764855ba78738e5d2b00c5:0">E</span></span></p></div></td><td><div data-key="7abe947fc903445e97f15db72773a295" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="a4e1c2dfcb574bbfa58df6e48f99a139"><span data-offset-key="a4e1c2dfcb574bbfa58df6e48f99a139:0">240.0.0.0</span></span></p></div></td><td><div data-key="6cfd03dd7d2048c4880e09248ec3ce4c" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="03f552355b3448f8938222dafd22f83c"><span data-offset-key="03f552355b3448f8938222dafd22f83c:0">255.255.255.255</span></span></p></div></td><td><div data-key="031790ae027d46d8a329e51b98276158" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="4064582971954933b5b22b85184d2fc3"><span data-offset-key="4064582971954933b5b22b85184d2fc3:0">Not applicable</span></span></p></div></td></tr></tbody></table>

Although we have nearly 4.3 billion IP addresses but not all are available for end devices. From these addresses, following addresses are reserved and cannot be assigned to end devices.

-   **0.0.0.0**:- This address represents all networks.
    

-   **127.0.0.0 to 127.255.255.255**: - This IP range is reserved for loopback testing.
    

-   **224.0.0.0 to 239.255.255.255 (Class D)**: - This IP class is reserved for multicast.
    

-   **240.0.0.0 to 255.255.255.254 (Class E)**: - This IP class is reserved for future use.
    

-   **255.255.255.255**: - This address represents all hosts.
    

Besides these reserved address, we also cannot use the first and the last IP address of each network. First IP address is reserved for the network address and last IP address is reserved for the broadcast address. We can use only the addresses available between the network address and the broadcast address for end devices.

#### 

IP address vs Network Address

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#ip-address-vs-network-address)

As discussed, an IP address is the combination of two separate addresses, network address and host address. If we exclude host address from IP address, we will get network address. In simple term, a network address is an IP address without host address. In technical term, a network address is an IP address in which all host bits are turned off.

We can only turn on or off host bits. We cannot turn on or off reserved network bits. In class A, B and C first 8, 16 and 24 bits are reserved respectively for network addresses.

![](csg07-03-ip-class.png)

network bits and host bits

#### 

IP address vs Host Address

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#ip-address-vs-host-address)

Any IP operation such as building a network address or host address and Subnetting are always performed in the host portion of an IP address. We can turn on and off host bits as per our requirement. In class A, B and C last 24 bits, 16 bits and 8 bits are defined as host bits respectively.

#### 

Private IP addresses vs Public IP addresses

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#private-ip-addresses-vs-public-ip-addresses)

In class A, B and C following IP addresses are defined as private IP addresses:-

-   In class A: - 10.0.0.0 to 10.255.255.255
    

-   In class B: - 172.16.0.0 to 172.31.255.255
    

-   In class C: - 192.168.0.0 to 192.168.255.255
    

Except private IP addresses and reserved IP addresses, all remaining IP addresses of Class A, B and C are considered as public IP addresses.

Public IP addresses are used in public network such as Internet. Public IP addresses are maintained and regulated by ICANN (Internet Corporation for Assigned Names and Numbers).

Private IP addresses are used in private network. Private IP addresses are locally significant and not routable in public network.

There are three types of network address; unicast, multicast and broadcast.

Unicast address represents an individual end device. If an IP packet is sent on a unicast address, it is intended only for that particular recipient. Unicast addresses are usually used by end devices for end to end communication.

![](csg07-04-unicast-address.jpg)

Multicast address represents a group of devices. If an IP packet is sent on a multicast address, it is intended for all members of that group. Multicast addresses are usually used by networking devices for running their own services.

![](csg07-05-multicast-address.jpg)

Broadcast address represents all devices of the network. If an IP packet is sent on a broadcast address, it is intended for all devices of that network. Broadcast addresses are usually used to locate hosts or services in network.

![](csg07-06-broadcast-address.jpg)

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