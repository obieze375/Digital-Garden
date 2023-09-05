
created: 2023-09-01T07:43:56 (UTC +01:00)

tags: []

source: https://medium.com/@ekirson/openshift-4-8-single-node-aws-ea5108cf24c1

author: Erez Kirson

---

  

# OpenShift 4.8 Single Node @ AWS. Full Openshift installation using ONE… | by Erez Kirson | Medium

  

> ## Excerpt

> Red Hat Openshift is a hybrid , enterprise Kubernetes application platform. Everything needed to run & develop containers in production. Main benefits are hundreds of open source project integrated…

  

---

## Prerequisites:

  

-   AWS IAM temporary admin Access & Secret key permissions

-   Existing VPC: , For Each AZ:  

    Public Subnet ID(IGW)  

    Private Subnet ID (NAT)
    
** Raise an VPC using terraform test script and insert the az info into the yml file

-   R53 DNS domain name

-   Openshift Installer files. [Click Here](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/latest/openshift-install-linux.tar.gz)

  

## Preparation

  

1.  Create configuration files , answer the guided questions.

  

```

openshift-install create install-config --dir=demo 

./openshift-install create install-config --dir=demo

```

  

2\. Modify **install-config.yaml** to meet your exciting VPC needs by specifying the exact subnets settings of your environment

  

```
apiVersion: v1
baseDomain: kirson-openshift.com #R53 DNS Domain name
controlPlane:
  hyperthreading: Enabled
  name: demo
  platform:
    aws:
      rootVolume:
        size: 120
      type: m5.xlarge
  replicas: 1 # This actually the Single Node setting!
compute:
- hyperthreading: Enabled
  name: worker
  platform:
    aws:
      rootVolume:
        size: 120
      type: m5.xlarge
  replicas: 0 # This actually the Single Node setting!
metadata:
  name: demo-vpc
networking:
  clusterNetwork:
  - cidr: 10.128.0.0/14
    hostPrefix: 23
  machineNetwork:
  - cidr: 10.0.0.0/16 # Change to your AWS CIDR
  networkType: OpenShiftSDN
  serviceNetwork:
  - 172.30.0.0/16
platform:
  aws:
    region: eu-central-1
    subnets:
     - subnet-xxxxxx # Public-AZ1
     - subnet-xxxxxx # Private-AZ3
publish: External # Can change to Internal, disables internet facing
pullSecret: # Pull Secret from cloud.redhat.com

```

  

## Installation

  

2\. Run the installer

  

```

openshift-install create cluster --dir=demo

```

  

**Note:** track installation process please open a new tab

  

```

tail -f demo/.openshift_install.log

```

  

During the installation The following AWS Resources are created

  

a. AWS Security Groups for EC2 & ELB  

b. AWS IAM Roles for our Single EC2 Instance  

c. AWS TAG all related resources kubernetes.io/cluster/demo-vpc-\[strings\]  

d. AWS ELB with Target groups  

e. AWS R53 Private Sub-Domains  

f. AWS S3 Bucket with Ignition files

  

After installation, openshift user authentication info is printed in STDOUT & placed in .**openshift\_install.log.**

  

Next Update environment vars:

  


```

echo "export KUBECONFIG=/home/ec2-user/demo/auth/kubeconfig" >> ~ec2-user/.bashrcsource ~ec2-user/.bashrc

```

  

Can now login and start using the cluster :

  

```

oc login ; oc get nodes

```

  

## Termination

  

This option destroys all AWS resources , in the background the script finds all relevant installation TAGS and deletes them.

  

```

openshift destroy cluster --dir=demo

./openshift-install destroy cluster --dir=demo

```

  

Hope you enjoyed !! My Cafe is ready….


## Extra Notes  

```
Obinna Ezeakachi

, 

Aug 22, 4:21 PM

INFO To access the cluster as the system:admin user when using 'oc', run 'export KUBECONFIG=/home/oezeakac/labs/OCP Env/demo/auth/kubeconfig'  
INFO Access the OpenShift web-console here: [https://console-openshift-console.apps.ll-test-vpc.obilab.net](https://console-openshift-console.apps.ll-test-vpc.obilab.net/)  
INFO Login to the console with user: "kubeadmin", and password: "Nqzva-2ofCf-TtyrK-eRAKZ"  
INFO Time elapsed: 25m18s


[oezeakac@oezeakac-thinkpadt14gen3 OCP Env]$ oc login -u kubeadmin -p 2fpSV-A4rF2-ZPVKB-qbFrr --server=[https://console-openshift-console.apps.ll-test-vpc.obilab.net](https://console-openshift-console.apps.ll-test-vpc.obilab.net/) --insecure-skip-tls-verify -> swap the server name for the api address in the web console front page when you log in

"kubeadmin", and password: "2fpSV-A4rF2-ZPVKB-qbFrr"



```



## Install Config
 
```yml 

apiVersion: v1

baseDomain: obi-openshift.com #R53 DNS Domain name

controlPlane:

  hyperthreading: Enabled

  name: demo

  platform:

    aws:

      rootVolume:

        size: 120

      type: m5.xlarge ## Upgrade specs 3x any lower will cause installation to crash as it's insuffiecient hardware

  replicas: 1 #<-- This actually the Single Node setting !

compute:

- hyperthreading: Enabled

  name: worker

  platform:

    aws:

      rootVolume:

        size: 120

      type: m5.xlarge

  replicas: 0 #<-- This actually the Single Node setting !

metadata:

  name: ll-test-vpc

networking:

  clusterNetwork:

  - cidr: 10.128.0.0/14

    hostPrefix: 23

  machineNetwork:

  - cidr: 10.0.0.0/16 # Change to your AWS CIDR

  networkType: OpenShiftSDN

  serviceNetwork:

  - 172.30.0.0/16

platform:

  aws:

    region: eu-west-1

    subnets:

     - subnet-0880d35028f6d7699 #Public-AZ1

     - subnet-036a85f33fa001246 #Private-AZ3

publish: External # Can change to Internal, disables internet facing

pullSecret: #Pull Secret from cloud.redhat.com
```
