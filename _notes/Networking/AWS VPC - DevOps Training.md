Here is best description in this Video about VPC and we are going through this step by step here

These are my written notes on the lesson, so this may be a bit difficult to dissect at parts, but I certainly recommend exploring the video further for more in depth lessons on the subject matter. I left “bookmark” links below each of the snapshots to encourage further exploration.

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

## 

Virtual Private Cloud[](https://tkssharma-devops.gitbook.io/devops-training/basic-networking/computer-networking-for-beginners#360b)



![](https://miro.medium.com/max/1400/1*XH_I2aSK_NXjB_iZQYGLtQ.png)

![](https://miro.medium.com/max/1400/1*SA27e_l2WVvm9HLxxFEeKw.png)

![](https://miro.medium.com/max/1400/1*uKHUWnPxc5603i_pU1fOAA.png)

The default VPC contains over 65,000 private IPs… so why not use it? If you instead create a custom VPC, it is more secure and you can customize (define your own IP address range, create your own public and private subnets, tighten down security settings).

“By default, instances you launch into a VPC can’t communicate with your own network.” So you can connect your VPC to your own data center using [**Hardware VPN Access**](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_VPN.html). “So that you can effectively extend your data center into the cloud and create a hybrid environment”

![](https://miro.medium.com/max/1400/1*UzTju-34AMhJ4_evm8DcNw.png)

To do this, you need a [**Virtual Private Gateway**](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_VPN.html). On the left side (labelled ‘virtual private gateway’) is the [**VPN concentrator**](http://searchnetworking.techtarget.com/answer/How-does-the-VPN-concentrator-work) on the Amazon side. Then on your side, you need a **customer gateway**, which is either a physical device or a software applicate that sits on your side of the VPN connection. A VPN Tunnel comes up when traffic is generated from your side of the connection.

![](https://miro.medium.com/max/1400/1*_pYD4T0Ev59CwAMAtB_VcQ.png)

Can be between your VPCs or other VPCs. VPC A wouldn’t be able to communicate with VPC B or C without a peering connection. Transitive peering does not work, meaning that VPCs need to be directly peered in order to be connected.

Also, VPCs with overlapping [**CIDRS**](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) cannot be peered. These are fine because they have different domain ranges, but if they didn’t there would be a problem.

If you delete the default VPC, you have to contact AWS support to get it back again!

[**Private IP Addresses**](http://whatismyipaddress.com/private-ip) are IP Addresses not reachable over the internet. They are used for communications between instances in the same network.

> “When you launch a new instance it’s given a private IP address and an internal DNS Hostname that resolves to the private IP address of the instance. But if you want to connect to this over the internet, it’s not going to work. So then you’d need a public IP address which is reachable from the internet. You can use public IP addresses for communication between your instances and the internet. Each instance that receives a public IP address is also given an external DNS hostname.
> 
> [Public IP addresses](http://blog.adiglobal.us/private-and-public-ip-address-ranges/) are associated with your instances from the Amazon pool of public IP addresses. When you stop or terminate your instance, the public IP address is released, and a new one is associated when the instance starts. So if you want your instance to retain this public IP address, you need to use something called an [**Elastic IP Address**](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html).”

An elastic IP address is a static or persistent IP address that’s allocated to your account and can be associated to and from your instances as required.

![](https://miro.medium.com/max/1400/1*eXgDhk23BOdjaSJzhu6ULA.png)

[Default Net Mask](https://www.net.princeton.edu/iprouters.html) in 20 for Subnets. These preserve up to 4096 IP addresses per subnet. Subnets are always mapped to a single availability zone (see below)

![](https://miro.medium.com/max/1400/1*MY0Uvh7t3SOSfXomMsD6Wg.png)

It is good to spread VPCs over availability zones for [redundancy](https://en.wikipedia.org/wiki/Redundancy_(engineering)) and [failover](https://en.wikipedia.org/wiki/Failover) purposes. You use Public Subnets for things that must be connected to the internet, such as web servers. Private Subnets either don’t need the internet, or are things you want to protect from the internet, such as database instances.

![](https://miro.medium.com/max/1400/1*ZUxNk1z-dT7cpbZy7e7KgQ.png)

![](https://miro.medium.com/max/1400/1*k02qXwO860kzDmokpTYi-w.png)

To attach your VPC to the internet, you need to attach an [Internet Gateway](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Internet_Gateway.html), and you can only attach one internet gateway per VPC.

![](https://miro.medium.com/max/1400/1*oPWQ7VxnwF6pCL0aFEKzMg.png)

Can now see the VPC has internet attached:

![](https://miro.medium.com/max/1400/1*ic5vEEci4DGThxDiRG1W-g.png)

Before our instances can have access to the internet, we need to make sure that our subnet route tables point to the internet gateway.

![](https://miro.medium.com/max/1400/1*XhC6O2SxOpQPXqju_tMJ9Q.png)

Every VPC has a default route table. It’s good practice to create a new one to practice with customization.

![](https://miro.medium.com/max/1400/1*GrOSIisVN3s0xWc4nn4Phg.png)

Above, the main route table is for the locally connected private subnet, which is the default (not connected to the internet). Above, the custom route table is used for the public subnet, connected to the internet gateway, and therefore the internet.

This is where you edit/create a route table and connect it to an internet gateway:

![](https://miro.medium.com/max/1400/1*vxgzr4Yb4JKUeje--EfQ0A.png)

Then, visit “subnet associations” and associate the Public subnet with the route table you just created.

![](https://miro.medium.com/max/1400/1*7X9mn_-znmkhIIAWvU5-hw.png)

[**NAT devices**](https://en.wikipedia.org/wiki/Network_address_translation) **\[network address translation devices\]** allow you to give a private subnet to the internet, without allowing the internet to access that subnet.

A NAT device forwards traffic from your private subnet to the internet, or other AWS services, and then sends the response back to the instances. When traffic goes to the internet, the source IP address of your instance is replaced with the NAT device and when the internet traffic comes back again, then that device translates the address to your instance’s private IP address.

A [NAT Gateway](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-nat-gateway.html) is recommended by AWS because it is a provided service that gives more bandwidth than [NAT Instances](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_NAT_Instance.html). Each NAT Gateway is created in a specific availability zone and is implemented with redundancy.

A NAT Instance is launched from a NAT AMI \[Amazon Machine Image\] and runs as an instance in your VPC, so it’s something else you have to look after. Whereas, in a NAT Gateway, a fully managed service, you can basically install it and forget about it.

NAT Gateway must be launched into a public subnet because it needs internet connectivity.

![](https://miro.medium.com/max/1400/1*xH2WH5XlvAETY9SwD75WPg.png)

Our diagram with security groups:

![](https://miro.medium.com/max/1400/1*23eTH3-DFsfSMKnIYtgwjg.png)

![](https://miro.medium.com/max/1400/1*RHTNZuClTgGamTWvmY4RSQ.png)

Now, for Network ACLs

![](https://miro.medium.com/max/1400/1*BpRUURD-R4T2dcs0cYLe4A.png)

Our diagram with Network ACLs:



![](https://miro.medium.com/max/1400/1*sjXLe2dJC9cYb_z17_6JWA.png)

![](https://miro.medium.com/max/1400/1*XhYT3sEQTAZOWlZVfb3y2g.png)

![](https://miro.medium.com/max/1400/1*fa9zwt4F5bgTIKCGZYZxvQ.png)

![](https://miro.medium.com/max/1400/1*t2qfzweZQo_ULg0d8GeICQ.png)

![](https://miro.medium.com/max/1400/1*dhjXLSmkSBBjCgSvtA83eA.png)

As always, thank you for reading! If you’d like to connect, I’ll leave my information below. I thrive in my work only by meeting and learning from new people.

<iframe src="https://cdn.iframe.ly/HstXc30" style="top: 0; left: 0; width: 100%; height: 100%; position: absolute; border: 0;" allowfullscreen="" scrolling="no" allow="accelerometer *; clipboard-write *; encrypted-media *; gyroscope *; picture-in-picture *;"></iframe>

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

