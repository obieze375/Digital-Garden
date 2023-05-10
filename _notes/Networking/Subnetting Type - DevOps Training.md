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

IP Subnetting is a process of dividing a large IP network in smaller IP networks. In Subnetting we create multiple small manageable networks from a single large IP network.

To best utilize available addresses if we put more than 16000000 hosts in a single network, due to broadcast and collision, that network will never work. If we put less hosts then remaining addresses will be wasted.

Subnetting provides a better way to deal with this situation. Subnetting allows us to create smaller networks from a single large network which not only fulfill our hosts’ requirement but also offer several other networking benefits.

I have already explained the advantages of Subnetting along with why Subnetting is necessary in previous parts of this tutorial. In this part, I will mainly focus on Subnetting components and terminology.

This tutorial is the third part of the article “**IP Subnetting in Computer Network Step by Step Explained with Examples**”. Other parts of this article are following.

_This tutorial is the last part of the article. It explains Supernetting in detail with examples._

#### 

Network portion vs Host portion

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#network-portion-vs-host-portion)

Identifying network portion and host portion in an IP address is the first step of Subnetting. Subnetting can only be done in host portion. Subnet mask is used to distinguish the network portion from host portion in an IP address.

An IP address and a subnet mask both collectively provide a numeric identity to an interface. Both addresses are always used together. Without subnet mask, an IP address is an ambiguous address and without IP address a subnet mask is just a number.

Both addresses are 32 bits in length. These bits are divided in four parts. Each part is known as octet and contains 8 bits. Octets are separated by periods and written in a sequence.

![](csg09-01-ip-address.png)

Subnet mask assigns an individual bit for each bit of IP address. If IP bit belongs to network portion, assigned subnet mask bit will be turned on. If IP bit belongs to host portion, assigned subnet mask bit will be turned off.

There are two popular notations to write the IP address and Subnet mask; Decimal notation and Binary notation.

In decimal notation, a value range 1 to 255 represents a turned on bit while a value 0 (zero) represents a turned off bit.

![](csg09-02-ip-address-example.png)

IP address with subnet mask decimal notation

In binary notation, 1 (one) represents a turned on bit while 0 (zero) represents a turned off bit.

![](csg09-03-subnetmask.jpg)

ip address in binary notation

Examples of IP address with subnet mask in binary format

00001010.00001010.00001010.00001010

11111111.00000000.00000000.00000000

10101100.10101000.00000001.00000001

11111111.11111111.00000000.00000000

11000000.10101000.00000001.00000001

11111111.11111111.11111111.00000000

Examples of IP address with subnet mask in decimal format

In above examples network portion is formatted in bold text.

#### 

Reserve IP classes, network bits and host bits

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#reserve-ip-classes-network-bits-and-host-bits)

Each IP address belongs to a predefined IP class. There are five predefined IP classes; A, B, C, D and E. From these classes, class D and E are reserved and cannot be used in Subnetting.

To learn more about IP address and its classes, you can see this tutorial.

_It explains IP address, IP classes, Types of IP address, Private IP address, Public IP address and much more in detail._

-   First 8, 16 and 24 bits are reserved for network portion respectively.
    

-   Last 2 bits (31 & 32) are reserved for host portion.
    

![](csg09-04-ip-class.png)

Reserved network bits and host bits cannot be used in Subnetting.

<table><tbody><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="2eaa9ac5d5a04e46bcca6a8f0e9948fe" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="dabc05e3bc8548d09f20cc41da6891db"><span data-offset-key="dabc05e3bc8548d09f20cc41da6891db:0">IP Class</span></span></p></div></td><td><div data-key="d3a42a0162864657b346953f8b3c8cca" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="e2eabf6765224827a1055a249c712e2f"><span data-offset-key="e2eabf6765224827a1055a249c712e2f:0">First IP Address of class</span></span></p></div></td><td><div data-key="332007c3654f4464ab991cebd625732b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="da1e06e32f7f46aea84c5c0ee0f7f847"><span data-offset-key="da1e06e32f7f46aea84c5c0ee0f7f847:0">Last IP Address of class</span></span></p></div></td><td><div data-key="b555d94178a9487ca7e1565d3318707a" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="6386d45c642740afb3897bc7e1a43496"><span data-offset-key="6386d45c642740afb3897bc7e1a43496:0">Default Subnet Mask</span></span></p></div></td><td><div data-key="93649500418349158c1346e2f19335be" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="15d790c2bdd848418150ec9ac1c91d30"><span data-offset-key="15d790c2bdd848418150ec9ac1c91d30:0">Default Network bits</span></span></p></div></td><td><div data-key="457dbc2b4cf744eaa012b39421bf7ec7" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="0a1516073e324bb3b7de50b350961738"><span data-offset-key="0a1516073e324bb3b7de50b350961738:0">Host bits</span></span></p></div></td><td><div data-key="83445d7b84e047c784abd05b9a62a785" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="e8a9360e223246f3a23d2adf9c5ac309"><span data-offset-key="e8a9360e223246f3a23d2adf9c5ac309:0">Reserved host bits</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="d5a6214c60174a5ab4fade0017377b5e" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="4d197df997564e0faa24f0d32dc3bcb1"><span data-offset-key="4d197df997564e0faa24f0d32dc3bcb1:0">A</span></span></p></div></td><td><div data-key="0cd056f99adb46fe94553bee6f0d029d" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="33e45c1c6e48409587518d9a0d69f396"><span data-offset-key="33e45c1c6e48409587518d9a0d69f396:0">0.0.0.0</span></span></p></div></td><td><div data-key="c9d20996d851411c8ffd94004db55bbc" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="3fb7af25201e43e09fae0c49598526df"><span data-offset-key="3fb7af25201e43e09fae0c49598526df:0">127.255.255.255</span></span></p></div></td><td><div data-key="d95c0432cfc24469a6ce9308769aa56d" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="0fee2e98f2864dababc79df4ccbe37b0"><span data-offset-key="0fee2e98f2864dababc79df4ccbe37b0:0">255.0.0.0</span></span></p></div></td><td><div data-key="a866f50e5078406fb90560ac78578b3b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="59d42af9a92849d5a3871544f4a5caad"><span data-offset-key="59d42af9a92849d5a3871544f4a5caad:0">First 8 bits</span></span></p></div></td><td><div data-key="1b0dad4fba8a47db8b2fc753e565543c" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="851a46793ef94d95adf37ad9acef6fe1"><span data-offset-key="851a46793ef94d95adf37ad9acef6fe1:0">9 to 30</span></span></p></div></td><td><div data-key="04789fbfc00841958271ef2f143bdebd" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="63375a606454463ba6a1f67b38bd7c4e"><span data-offset-key="63375a606454463ba6a1f67b38bd7c4e:0">31, 32</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="b1c88768236b4f599e7c11d69ed163eb" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="0edadaf87f7d4c06adfc0a898f19d06a"><span data-offset-key="0edadaf87f7d4c06adfc0a898f19d06a:0">B</span></span></p></div></td><td><div data-key="719aa3176269441096934fb277aad487" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="234b6700eaf24582a127a7951e829753"><span data-offset-key="234b6700eaf24582a127a7951e829753:0">128.0.0.0</span></span></p></div></td><td><div data-key="144e2a0e3e8840398772d0b5192cfc73" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="548265077ef4493484797bdb7875138d"><span data-offset-key="548265077ef4493484797bdb7875138d:0">191.255.255.255</span></span></p></div></td><td><div data-key="f5f002a7e83245c48e1ad5ac93590481" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="db94457a57ae4db7904eee430edefa5c"><span data-offset-key="db94457a57ae4db7904eee430edefa5c:0">255.255.0.0</span></span></p></div></td><td><div data-key="521ffa58d49b441499ecb3242a837a2b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="2675c568267e46a38867769ace1d0fb0"><span data-offset-key="2675c568267e46a38867769ace1d0fb0:0">First 16 bits</span></span></p></div></td><td><div data-key="59bb3ea32e294e36adecb4e1881ed6b8" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="a4f7f768d779465d80d57b96f9327135"><span data-offset-key="a4f7f768d779465d80d57b96f9327135:0">17 to 30</span></span></p></div></td><td><div data-key="b0a106c2eaba4ff798d778b4a2511f65" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="964ce620019a432c96844694a60640fe"><span data-offset-key="964ce620019a432c96844694a60640fe:0">31, 32</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="ac52ac6ff7204ed0b85f383b530efd98" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="9c05cdc431d3463db009e1d33872a074"><span data-offset-key="9c05cdc431d3463db009e1d33872a074:0">C</span></span></p></div></td><td><div data-key="08f58a54a7954d70ad7bb39525216087" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="99971dc82e1a4592b0e849a85bd05c91"><span data-offset-key="99971dc82e1a4592b0e849a85bd05c91:0">192.0.0.0</span></span></p></div></td><td><div data-key="9192fb03ab8040e696ab13ef7c9f607f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="04a7e93292b44c21a37b2fd20881e526"><span data-offset-key="04a7e93292b44c21a37b2fd20881e526:0">223.255.255.255</span></span></p></div></td><td><div data-key="eecc3ac16b754da7a7c63ffc20a217b5" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="f8019e05d75b415badf22dbe90975ef2"><span data-offset-key="f8019e05d75b415badf22dbe90975ef2:0">255.255.255.0</span></span></p></div></td><td><div data-key="333f5296218049ce84d7b46ccff5ee8b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="785ec60b50454055acfcaff5eaeaa29e"><span data-offset-key="785ec60b50454055acfcaff5eaeaa29e:0">First 24 bits</span></span></p></div></td><td><div data-key="aa75d810dc614da49877fef77ae6f80b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="d4f42e230d174f918e6caa0e9692f44e"><span data-offset-key="d4f42e230d174f918e6caa0e9692f44e:0">25 to 30</span></span></p></div></td><td><div data-key="0b67c2c1cc5640de854572ee24b1a8ca" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="839c8f6b10a64868b2738435c43b04ff"><span data-offset-key="839c8f6b10a64868b2738435c43b04ff:0">31, 32</span></span></p></div></td></tr></tbody></table>

#### 

Subnetting eligible host bits

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#subnetting-eligible-host-bits)

After excluding reserved network bits and host bits, remaining bits are considered as Subnetting eligible host bits.

![](csg09-05-ip-bits.png)

Subnetting can be done only in Subnetting eligible bits.

A subnet is a single small network created from a large network. In Subnetting we break a single large network in multiple small networks. These networks are known as subnets.

#### 

Network address and Broadcast address

[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#network-address-and-broadcast-address)

In each network there are two special addresses; network address and broadcast address. Network address represents the network itself while broadcast address represents all the hosts which belong to it. These two addresses can’t be assigned to any individual host in network. Since each subnet represents an individual network, it also uses these two addresses.

In simple language, in a single network only two IP addresses will be used for these addresses. But if we breaks this network in two small networks then four IP addressed will be used for these addresses.

![](csg09-06-subnet.png)

network address broadcast address

Network address and broadcast address are also known as Network ID and broadcast ID respectively.

All addresses between Network address and Broadcast address are known as valid host addresses. Only valid host addresses can be assigned to the devices in a network. These devices include end user devices such as computes, laptops, tablets, smartphones, IP phones, servers, printers, terminals, IP camera and networking devices such switches, routers, firewalls and proxy servers. In short, any device that uses IP protocol for data transferring needs a valid host address.

Block size is the sum of network address, valid host addresses and broadcast address. For example, if in a network there are 6 valid hosts than block size of that network is 8 (1 network address + 6 valid hosts + 1 broadcast address).

An IP address is built from the various combinations of IP bits. Understanding how many combinations the number of bits provides or to get the number of combinations how many bits we need is the second essential step of Subnetting.

-   A combination of all 32 represents a unique IP address.
    

-   A combination of network bits in IP address represents the number of networks or subnets.
    

-   A combination of host bits in IP address represents the number of total hosts.
    

To know how many combinations the number of bits provides or to get the number of combinations how many bits are required, we use the power of 2.

For example, to break a single large network in 4 subnets, we need 2 (22 = 4) Subnetting bits. This way if we have 3 Subnetting bits, we can make 8 (23 = 8) additional networks.

Following table lists the power of 2 till 32.

<table><tbody><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="d6a14f0a04a14563937aef5c0b8acaee" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="cbb0f75174454f7c930715631845292b"><span data-offset-key="cbb0f75174454f7c930715631845292b:0">2X</span></span></p></div></td><td><div data-key="e11464cacfe54ddfb8b00f70e5123fa2" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="8d7b6430977b4066bc7554e3469ab7bb"><span data-offset-key="8d7b6430977b4066bc7554e3469ab7bb:0">Value</span></span></p></div></td><td><div data-key="f05cd7d2d68149f3a72356bfc583758b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="30dbb93c550d4ae085fbed6ba73ad15c"><span data-offset-key="30dbb93c550d4ae085fbed6ba73ad15c:0">2X</span></span></p></div></td><td><div data-key="981fbaf48b6543058869465288d0fd6a" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="43d58a9d7c32497b9fa30afa43c3fc24"><span data-offset-key="43d58a9d7c32497b9fa30afa43c3fc24:0">Value</span></span></p></div></td><td><div data-key="834e55fc91784725a6da57889c859ec3" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="b7ef4a29490a485ca0ae111354262707"><span data-offset-key="b7ef4a29490a485ca0ae111354262707:0">2X</span></span></p></div></td><td><div data-key="6c670690fcc74eda8c8df3b8e4c3d518" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="7a2543cbb78642d0996ba3527263cc0c"><span data-offset-key="7a2543cbb78642d0996ba3527263cc0c:0">Value</span></span></p></div></td><td><div data-key="b01d8a2ae0584da399d60d65aaa66fcf" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="26be6ec606884f4bb8acc90a17df0a3d"><span data-offset-key="26be6ec606884f4bb8acc90a17df0a3d:0">2X</span></span></p></div></td><td><div data-key="644b31cc64634c14b17dd8145382f225" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="35b86b0d13734149b2575dde716019fd"><span data-offset-key="35b86b0d13734149b2575dde716019fd:0">Value</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="56b714d52e754f47bb935a6ec2975c97" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="7c1ebf8f1c1a4b3d946e229511d3b1c8"><span data-offset-key="7c1ebf8f1c1a4b3d946e229511d3b1c8:0">1</span></span></p></div></td><td><div data-key="8ac375df91d54e3aa80d76cb31cd3b90" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="560e7a9d728b4cf09b01138c1a2459b6"><span data-offset-key="560e7a9d728b4cf09b01138c1a2459b6:0">2</span></span></p></div></td><td><div data-key="bad0a87e9bf84b798c08acb50e801f3c" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="f614f308485246c0a53534ebce607a07"><span data-offset-key="f614f308485246c0a53534ebce607a07:0">9</span></span></p></div></td><td><div data-key="a7586047c8234a5b9b95411f61848540" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="4fee167595424ee98c34bd5d4c6c34d1"><span data-offset-key="4fee167595424ee98c34bd5d4c6c34d1:0">512</span></span></p></div></td><td><div data-key="38580038487a4a2b96cc6529720f7a5b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c0b6a6c2c5484feca167b21894d105b4"><span data-offset-key="c0b6a6c2c5484feca167b21894d105b4:0">17</span></span></p></div></td><td><div data-key="55127265b9444b64a8ec7e71e2a7cfd8" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="465a7b7841494a93a476c1251d7efdd2"><span data-offset-key="465a7b7841494a93a476c1251d7efdd2:0">131072</span></span></p></div></td><td><div data-key="a48e7b207bd5482eacdf2999f58b6244" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="4bccdd0bb6e34dfa923df96c9acb66a9"><span data-offset-key="4bccdd0bb6e34dfa923df96c9acb66a9:0">25</span></span></p></div></td><td><div data-key="9fa45d6901974af6886c723c0d3d8109" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="88c105596d3c46529d91350b9cb5d885"><span data-offset-key="88c105596d3c46529d91350b9cb5d885:0">33554432</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="8a866217bc584a8780e57bbe5b252090" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="f265a548b5584519a46a5f619e2853e6"><span data-offset-key="f265a548b5584519a46a5f619e2853e6:0">2</span></span></p></div></td><td><div data-key="54558dd15ebf4ea3bd29a74374308232" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="0ce8f888964443a4a49627b3302c4578"><span data-offset-key="0ce8f888964443a4a49627b3302c4578:0">4</span></span></p></div></td><td><div data-key="0e06c54a5f854b2c8d6a6b8524fe11e5" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="a00ef37c140147b6818aea565d3c651b"><span data-offset-key="a00ef37c140147b6818aea565d3c651b:0">10</span></span></p></div></td><td><div data-key="579e6dc9d15e49018a328e5347f17445" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="d3b101e655da49ee86bb41889afc2a57"><span data-offset-key="d3b101e655da49ee86bb41889afc2a57:0">1024</span></span></p></div></td><td><div data-key="df3db2b901c44b00a74beb29f1082b6f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c475050e48bd40029ce197213f17c80c"><span data-offset-key="c475050e48bd40029ce197213f17c80c:0">18</span></span></p></div></td><td><div data-key="58fddb7bc33145b9bd8d1e792f677341" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="d6c179584b66403b98ca6691da0ff350"><span data-offset-key="d6c179584b66403b98ca6691da0ff350:0">262144</span></span></p></div></td><td><div data-key="91169f475dab45f7a4a97cc86f54904e" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="60d8b02bf8f8468b8c7e73a40bb86bcf"><span data-offset-key="60d8b02bf8f8468b8c7e73a40bb86bcf:0">26</span></span></p></div></td><td><div data-key="a6f74bbd08db4ad5bd692124d7c0c91c" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="fec774a59a2541ebbc2c01edd4b7b8d8"><span data-offset-key="fec774a59a2541ebbc2c01edd4b7b8d8:0">67108864</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="a58f36c3c89f41768f3030770793dfbf" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="32f09385684e4e0584ebbb502c20cdb5"><span data-offset-key="32f09385684e4e0584ebbb502c20cdb5:0">3</span></span></p></div></td><td><div data-key="ce7dccfe91f347fba1c86189747a0aa0" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="aa866029b3dc4859962223dd82bafba1"><span data-offset-key="aa866029b3dc4859962223dd82bafba1:0">8</span></span></p></div></td><td><div data-key="76b8654bdf344f6d8f1ad787b98aaddb" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="f4bc92e8cae7407c8bdc3f51b61f6f6c"><span data-offset-key="f4bc92e8cae7407c8bdc3f51b61f6f6c:0">11</span></span></p></div></td><td><div data-key="a4ad31a1a74c4b338792a4659826cc7c" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="6dd20a1686814c5e9eef20eaacc1bcd7"><span data-offset-key="6dd20a1686814c5e9eef20eaacc1bcd7:0">2048</span></span></p></div></td><td><div data-key="8d266460b3ca4965845eed419ab97cfb" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="973c87ec640f4fc7a9739a7ce731b7cf"><span data-offset-key="973c87ec640f4fc7a9739a7ce731b7cf:0">19</span></span></p></div></td><td><div data-key="d4ee8ede705d44219a4b1c7a3c346931" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="e1bda20f3e364bf88dfe2bd7e74bc601"><span data-offset-key="e1bda20f3e364bf88dfe2bd7e74bc601:0">524288</span></span></p></div></td><td><div data-key="3688ed37b14a4025b44bbbf42c9a5348" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c4d4c8296bb6401a9008bc53ba649fbe"><span data-offset-key="c4d4c8296bb6401a9008bc53ba649fbe:0">27</span></span></p></div></td><td><div data-key="fc5dd9092e3a4c3e91ea9d256569764c" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="f1226ac58cc64f0d9c0918cac99231bd"><span data-offset-key="f1226ac58cc64f0d9c0918cac99231bd:0">134217728</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="079ee4a2e7d84e83bf614149f7903e5b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="26b03af12505458db1d899148dde9262"><span data-offset-key="26b03af12505458db1d899148dde9262:0">4</span></span></p></div></td><td><div data-key="761d89c24a5f410aa9b2b76fd87c93e9" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="cb781a1b07134b0fbbd8181e3060e471"><span data-offset-key="cb781a1b07134b0fbbd8181e3060e471:0">16</span></span></p></div></td><td><div data-key="bc2932808fc04d7f969f13963a35e90a" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="4019982ae22b4575834f5e7089917e2e"><span data-offset-key="4019982ae22b4575834f5e7089917e2e:0">12</span></span></p></div></td><td><div data-key="6059d861cf814f6c852cc84754d52004" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="16cce9a16d504655863550b7c8a878fa"><span data-offset-key="16cce9a16d504655863550b7c8a878fa:0">4096</span></span></p></div></td><td><div data-key="335f47ba79394abe9a0671de669bf218" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="61185e593d904bca94cf032ad96bcb38"><span data-offset-key="61185e593d904bca94cf032ad96bcb38:0">20</span></span></p></div></td><td><div data-key="6dd067cd16ea4427ba057c7aa6984c4a" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="b188ece0031c47a88efef5b512544a69"><span data-offset-key="b188ece0031c47a88efef5b512544a69:0">1048576</span></span></p></div></td><td><div data-key="c1cce353aa43414f8d0d819eaaabdaff" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="0c59bc14e0904a8ebe260c761b36107b"><span data-offset-key="0c59bc14e0904a8ebe260c761b36107b:0">28</span></span></p></div></td><td><div data-key="9b898330e79647daba0bddca20b5122f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="62e936a333474efba770c4cd6f02b756"><span data-offset-key="62e936a333474efba770c4cd6f02b756:0">268435456</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="59df884eb401431b860b0c2c33c5b331" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="ced5eb6be308402ea05be23b7c9db5dd"><span data-offset-key="ced5eb6be308402ea05be23b7c9db5dd:0">5</span></span></p></div></td><td><div data-key="2a03890db05b49da894ebd894f1ae417" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="5da8f9bbd04a43cab18a691e1b89e7d1"><span data-offset-key="5da8f9bbd04a43cab18a691e1b89e7d1:0">32</span></span></p></div></td><td><div data-key="3e59eb256cc641a99dd8921704525dd3" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c6a19a25705c423cbb262df2328b46e8"><span data-offset-key="c6a19a25705c423cbb262df2328b46e8:0">13</span></span></p></div></td><td><div data-key="fbb853e7c0074446adb6daa0ffa0c3a9" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="b6eefe024eec4dedb5558d20a37f1dc0"><span data-offset-key="b6eefe024eec4dedb5558d20a37f1dc0:0">8192</span></span></p></div></td><td><div data-key="9855befd29034756a4056cafccc1ba29" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="2299b95667484ca3a11be8147c757cdf"><span data-offset-key="2299b95667484ca3a11be8147c757cdf:0">21</span></span></p></div></td><td><div data-key="b4ca12947c7a4980bffe4b39654f42d7" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="62f74037fa9e4ffb9df9d0c1d4686826"><span data-offset-key="62f74037fa9e4ffb9df9d0c1d4686826:0">2097152</span></span></p></div></td><td><div data-key="d9eda803fb374e39b3cd805384742ae9" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="a192a5d79105445fa6918fa50f8a89a4"><span data-offset-key="a192a5d79105445fa6918fa50f8a89a4:0">29</span></span></p></div></td><td><div data-key="397cada7852a48959518df8e487b9db1" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c263686a936d4fb38697f749c8bd36dc"><span data-offset-key="c263686a936d4fb38697f749c8bd36dc:0">536870912</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="efeb78d4041e4936a6b21da95f0cabdd" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="f35124e29ba3495e9a842df2e8b2b9eb"><span data-offset-key="f35124e29ba3495e9a842df2e8b2b9eb:0">6</span></span></p></div></td><td><div data-key="de45b2969ea648c98c40878a2e91ea31" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="028eb33d196a4501be15c30c507ebb94"><span data-offset-key="028eb33d196a4501be15c30c507ebb94:0">64</span></span></p></div></td><td><div data-key="34fd480c57ed4527bfd7b91169d3ba78" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="1b6f7cb15308458fa34e0ea9ecf76091"><span data-offset-key="1b6f7cb15308458fa34e0ea9ecf76091:0">14</span></span></p></div></td><td><div data-key="35dbb6d2e9e04529999eff3a49ca8099" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="10d5e03bf7c24012af32eeb65a0e7599"><span data-offset-key="10d5e03bf7c24012af32eeb65a0e7599:0">16384</span></span></p></div></td><td><div data-key="1bcb30932c7748c0b184eb07692c262f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="c310a7d096c94ac589f93b6e9e2fa46f"><span data-offset-key="c310a7d096c94ac589f93b6e9e2fa46f:0">22</span></span></p></div></td><td><div data-key="aac2603de6484726897ea9374a092809" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="172a8f58f7184528aa9f3f8cf58db81b"><span data-offset-key="172a8f58f7184528aa9f3f8cf58db81b:0">4194304</span></span></p></div></td><td><div data-key="1a9460f38a374eb28cc1c1d08bd70724" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="078b5e4b4b04473e88efdb76bcfa8b83"><span data-offset-key="078b5e4b4b04473e88efdb76bcfa8b83:0">30</span></span></p></div></td><td><div data-key="06e92accd2f145a99c932182f7c12582" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="4b52c1ddcc1b451bbf8b91e1e53c80d0"><span data-offset-key="4b52c1ddcc1b451bbf8b91e1e53c80d0:0">1073741824</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="028b257190d24034aac429ccadd07f81" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="3678b39fb5c34365b3b03a844afabc92"><span data-offset-key="3678b39fb5c34365b3b03a844afabc92:0">7</span></span></p></div></td><td><div data-key="6ca5614361804d809a9ab9c94272ce2f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="237fd6bece374c5bb5558c6bb1035111"><span data-offset-key="237fd6bece374c5bb5558c6bb1035111:0">128</span></span></p></div></td><td><div data-key="482305c338ca4081a3a5cdd37852e25b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="badef323a7e54007b91bcb9f8eeded79"><span data-offset-key="badef323a7e54007b91bcb9f8eeded79:0">15</span></span></p></div></td><td><div data-key="7422bb258556412db3c179c5a25e7718" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="04b3e91a514e4c5bb2e4155630e8fc2a"><span data-offset-key="04b3e91a514e4c5bb2e4155630e8fc2a:0">32768</span></span></p></div></td><td><div data-key="e368d53fa2254b1f8a68506f4aa466ba" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="7b5c0826384e4f3a94c602c3a7b7b736"><span data-offset-key="7b5c0826384e4f3a94c602c3a7b7b736:0">23</span></span></p></div></td><td><div data-key="ee622d51abfe4752b65bebde29add29d" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="af011033a3634eaf937868f954f877a9"><span data-offset-key="af011033a3634eaf937868f954f877a9:0">8388608</span></span></p></div></td><td><div data-key="bbeecc6b2c184ed3ae45b96befe84cfc" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="64daccb98faf43a28b25e7ffef8be6a4"><span data-offset-key="64daccb98faf43a28b25e7ffef8be6a4:0">31</span></span></p></div></td><td><div data-key="2e2b113e93fd44ac9649bab81e81a188" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="8e0f12b32c69450f93148b817d9d42f1"><span data-offset-key="8e0f12b32c69450f93148b817d9d42f1:0">2147483648</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="067d5d5c53c54ead9af13bb58aeef6b0" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="484b50e46a2a46479b617f7f73f5a48f"><span data-offset-key="484b50e46a2a46479b617f7f73f5a48f:0">8</span></span></p></div></td><td><div data-key="37603ed68f5845208770c74037e6c073" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="0c51ed01a2a44be9ac8d65d1ebed7157"><span data-offset-key="0c51ed01a2a44be9ac8d65d1ebed7157:0">256</span></span></p></div></td><td><div data-key="38e933efc89f481990e2d8682198fc24" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="2e37cfdbb2584d7e8b009c7c4e897d7f"><span data-offset-key="2e37cfdbb2584d7e8b009c7c4e897d7f:0">16</span></span></p></div></td><td><div data-key="c056c9011f0d4ce1b37feea3dbddbf11" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="2b0251c670a2483a8832398076292e33"><span data-offset-key="2b0251c670a2483a8832398076292e33:0">65536</span></span></p></div></td><td><div data-key="53fb4facdfa14aca943bb0b2b83d8959" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="b122703f740740b2be439f39df449941"><span data-offset-key="b122703f740740b2be439f39df449941:0">24</span></span></p></div></td><td><div data-key="33573097aacf4a479bbb213afbb1ce89" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="6ecf1f2f19ec4a62a0b66c9bebaf376f"><span data-offset-key="6ecf1f2f19ec4a62a0b66c9bebaf376f:0">16777216</span></span></p></div></td><td><div data-key="663c8576bb1b44dbb351de4ac35276b6" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="661f29283d714328a068f7ddd8565dde"><span data-offset-key="661f29283d714328a068f7ddd8565dde:0">32</span></span></p></div></td><td><div data-key="13dc939bf02b4e6d8e02f3d25915f559" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="2ad96e6947f34e9d94c1f4e1bc3a4997"><span data-offset-key="2ad96e6947f34e9d94c1f4e1bc3a4997:0">4294967296</span></span></p></div></td></tr></tbody></table>

In 2X the X is the number of bits.

Subnetting always flows in single direction (left to right) without skipping any bit. This simple rule gives us the exact location of Subnetting bits in an address space. Let’s take an example.

A class C network is subnetted in 4 subnets. Find the number of host bits used in Subnetting and their location in address space.

To create 4 subnets we need to 2 (22 = 4) Subnetting eligible host bits.

Since in class C network space Subnetting eligible bits starts from 25 and Subnetting always goes from left to right without skipping any bit, the bits used in this network are 25 and 26.

![](csg09-07-subneting-drection.png)

It’s a compact representation of Subnet mask. In this notation a slash (/) sign and total number of the on bits in subnet mask are written with IP address instead of full Subnet mask.

Following table lists some examples of IP addresses with Subnet mask in all three notations.

<table><tbody><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="e032e5f3c5f94013854e10e7f987e5c8" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="9e58e835c77c4b68a3d3a3c763cf50fc"><span data-offset-key="9e58e835c77c4b68a3d3a3c763cf50fc:0">In Slash notation</span></span></p></div></td><td><div data-key="a34385ac13644f8991a5890b0ee7a934" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="ad328d3f72dc4a5c86ccc238e15ab650"><span data-offset-key="ad328d3f72dc4a5c86ccc238e15ab650:0">In binary notation</span></span></p></div></td><td><div data-key="2d679cc3e0384ab784926c5a48b3af82" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="ba576cc856984f5980519573e0a6ef49"><span data-offset-key="ba576cc856984f5980519573e0a6ef49:0">In decimal notation</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="ce12a60df9ba4d6d8ca36e7842756ee9" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="2cdc42603f594fe693bf6dcc73263013"><span data-offset-key="2cdc42603f594fe693bf6dcc73263013:0">10.10.10.10/8</span></span></p></div></td><td><div data-key="e3be8d3d48564fa2868bfa6e41206a41" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="cae79e5dffc646699da50f5cafbf9dfc"><span data-offset-key="cae79e5dffc646699da50f5cafbf9dfc:0">00001010.00001010.00001010.00001010 11111111.00000000.00000000.00000000</span></span></p></div></td><td><div data-key="e740753526ff4e458286f67396e08b56" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="d91758c57bfd4a16bba33255ecdd8343"><span data-offset-key="d91758c57bfd4a16bba33255ecdd8343:0">10.10.10.10 255.0.0.0</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="79d188b277414a4fbb8882f0590e7c15" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="3c38685050024de7a0618015a27ee9a4"><span data-offset-key="3c38685050024de7a0618015a27ee9a4:0">172.168.1.1/16</span></span></p></div></td><td><div data-key="34df8c8263b64d768109249e15844691" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="57fa2f4573404b5fb6339c0caf7360b6"><span data-offset-key="57fa2f4573404b5fb6339c0caf7360b6:0">10101100.10101000.00000001.00000001 11111111.11111111.00000000.00000000</span></span></p></div></td><td><div data-key="cf4d0f94f12946509ebe1144615a514b" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="30ed588b625d488c9c7090e1b83dbf4a"><span data-offset-key="30ed588b625d488c9c7090e1b83dbf4a:0">172.168.1.1 255.255.0.</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="aca26c4c8d5449699dd5c53fcd1d612f" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="118ffd38a04245b0b7715b417b22175d"><span data-offset-key="118ffd38a04245b0b7715b417b22175d:0">192.168.1.1/24</span></span></p></div></td><td><div data-key="aa33cb5ecde849809af0f0a247184fdd" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="10b3ec0903d945128ad13313b07b0d13"><span data-offset-key="10b3ec0903d945128ad13313b07b0d13:0">11000000.10101000.00000001.00000001 11111111.11111111.11111111.00000000</span></span></p></div></td><td><div data-key="5dee83d7780549768aa69e1c7134b555" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="4cb2a248ac4446a7af95d9f03931fd2e"><span data-offset-key="4cb2a248ac4446a7af95d9f03931fd2e:0">192.168.1.1 255.255.255.0</span></span></p></div></td></tr><tr data-rnwi-5xr8s6-dse9kg-2fw26j-10utlgm-focus-visible="true" data-rnwi-handle="table-row"><td><div data-key="c16c80a950a545f3b2a04c5aadd75a41" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="7ae4baf9889140438ee18d6cc6c40d57"><span data-offset-key="7ae4baf9889140438ee18d6cc6c40d57:0">192.168.1.1/28</span></span></p></div></td><td><div data-key="8b14dc86d89041dc96a65e3f3eb53c70" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="5448ef0029e64c388298a58eea4885ab"><span data-offset-key="5448ef0029e64c388298a58eea4885ab:0">11000000.10101000.00000001.00000001 11111111.11111111.11111111.11110000</span></span></p></div></td><td><div data-key="af667569ba1547ff9425a8d8221ad3d4" data-fragment="true" data-slate-editor="true" data-document-key="4"><p><span data-key="d7a145851a53450b9dc10273fce46f9d"><span data-offset-key="d7a145851a53450b9dc10273fce46f9d:0">192.168.1.1 255.255.255.240</span></span></p></div></td></tr></tbody></table>

There are two types of Subnetting FLSM and VLSM. In FLSM, all subnets have equal number of host addresses and use same Subnet mask. In VLSM, subnets have flexible number of host addresses and use different subnet mask.

Following figure shows an example of FLSM and VLSM.

![](csg09-08-flsm-vlsm.png)

FLSM is easy in implementation and simple in operation but wastes a lot of IP addresses. VLSM is hard in implementation and complex in operation but utilizes maximum IP addresses.

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