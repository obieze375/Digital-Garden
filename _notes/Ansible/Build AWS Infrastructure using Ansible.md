[https://github.com/kenhitchcock/ansible-role-cornerstone](https://github.com/kenhitchcock/ansible-role-cornerstone)



## Playbook example 2

---------------------

  

```yaml

---

  

- name: Build Instance  

  hosts: localhost

  vars_files:

    - roles/ansible-role-cornerstone/vars/main.yml

  

  tasks:

    - include_role:

        name: roles/ansible-role-cornerstone

```

  

## vars file example in the var folder for 2nd Playbook example

  

```yaml
---
# vars file for cornerstone
ansible_python_interpreter: /usr/bin/python3
cornerstone_prefix: cs
cornerstone_ssh_admin_username: rhadmin
cornerstone_ssh_admin_pubkey:
cornerstone_aws_ssh_key_name: ssh-test
cornerstone_aws_profile: default
cornerstone_ssh_user: ec2-user
cornerstone_ssh_key_path: "/Users/oezeakachi/Desktop/key/ssh-test.pem"

cornerstone_platform: aws
cornerstone_location: eu-west-1

cornerstone_sg:
  - name: "obitestworkshop-sg"
    description: Security group for aws
    region: "{{ cornerstone_location }}"
    rules:
      - proto: tcp
        from_port: 22
        to_port: 22
        group_name: ""
        cidr_ip: 0.0.0.0/0
        rule_desc: "allowSSHin_all"
      - proto: tcp
        from_port: 443
        to_port: 443
        group_name: ""
        cidr_ip: 0.0.0.0/0
        rule_desc: "allowHttpsin_all"
      - proto: all
        from_port: ""
        to_port: ""
        group_name: "obitestworkshop-sg"
        cidr_ip: 0.0.0.0/0
        rule_desc: "allowAllfromSelf"

vm_state: present

guests:
  testsystem1:
      cornerstone_vm_state: "{{vm_state}}"
      cornerstone_platform: aws
      cornerstone_tag_purpose: "Testing"
      cornerstone_tag_role: "testsystem"
      cornerstone_vm_name: testsystem1
      cornerstone_location: eu-west-1
      cornerstone_vm_aws_az: eu-west-1a
      cornerstone_vm_flavour: t3.2xlarge
      cornerstone_vm_aws_ami: ami-0b04ce5d876a9ba29
      cornerstone_vm_aws_sg: obitestworkshop-sg
      cornerstone_virtual_network_name: "{{ cornerstone_prefix }}vnet"
      cornerstone_virtual_network_cidr: "10.1.0.0/16"
      cornerstone_subnet_name: "{{ cornerstone_prefix }}subnet"
      cornerstone_public_private_ip: public
      cornerstone_vm_private_ip:
      cornerstone_vm_assign_public_ip: yes
      cornerstone_vm_public_ip: 34.248.68.57
      cornerstone_publicip_allocation_method: Dynamic
      cornerstone_publicip_domain_name: null
      cornerstone_vm_os_disk_size: 10
      cornerstone_vm_data_disk: false
      cornerstone_vm_data_disk_device_name: "/dev/xvdb"
      cornerstone_aws_vm_data_disk_managed: "gp2"
      cornerstone_vm_data_disk_size: "50" 
  testsystem2:
      cornerstone_vm_state: "{{vm_state}}"
      cornerstone_platform: aws
      cornerstone_tag_purpose: "Testing"
      cornerstone_tag_role: "testsystem"
      cornerstone_vm_name: testsystem2
      cornerstone_location: eu-west-1
      cornerstone_vm_aws_az: eu-west-1a
      cornerstone_vm_flavour: t3.2xlarge
      cornerstone_vm_aws_ami: ami-0b04ce5d876a9ba29
      cornerstone_vm_aws_sg: obitestworkshop-sg
      cornerstone_virtual_network_name: "{{ cornerstone_prefix }}vnet"
      cornerstone_virtual_network_cidr: "10.1.0.0/16"
      cornerstone_subnet_name: "{{ cornerstone_prefix }}subnet"
      cornerstone_public_private_ip: public
      cornerstone_vm_private_ip:
      cornerstone_vm_assign_public_ip: yes
      cornerstone_vm_public_ip: 52.18.234.20
      cornerstone_publicip_allocation_method: Dynamic
      cornerstone_publicip_domain_name: null
      cornerstone_vm_os_disk_size: 10
      cornerstone_vm_data_disk: false
      cornerstone_vm_data_disk_device_name: "/dev/xvdb"
      cornerstone_aws_vm_data_disk_managed: "gp2"
      cornerstone_vm_data_disk_size: "50"
  testsystem3:
      cornerstone_vm_state: "{{vm_state}}"
      cornerstone_platform: aws
      cornerstone_tag_purpose: "Testing"
      cornerstone_tag_role: "testsystem"
      cornerstone_vm_name: testsystem3
      cornerstone_location: eu-west-1
      cornerstone_vm_aws_az: eu-west-1a
      cornerstone_vm_flavour: t3.2xlarge
      cornerstone_vm_aws_ami: ami-0b04ce5d876a9ba29
      cornerstone_vm_aws_sg: obitestworkshop-sg
      cornerstone_virtual_network_name: "{{ cornerstone_prefix }}vnet"
      cornerstone_virtual_network_cidr: "10.1.0.0/16"
      cornerstone_subnet_name: "{{ cornerstone_prefix }}subnet"
      cornerstone_public_private_ip: public
      cornerstone_vm_private_ip:
      cornerstone_vm_assign_public_ip: yes
      cornerstone_vm_public_ip: 52.214.229.143
      cornerstone_publicip_allocation_method: Dynamic
      cornerstone_publicip_domain_name: null
      cornerstone_vm_os_disk_size: 10
      cornerstone_vm_data_disk: false
      cornerstone_vm_data_disk_device_name: "/dev/xvdb"
      cornerstone_aws_vm_data_disk_managed: "gp2"
      cornerstone_vm_data_disk_size: "50"

```

## duplicate the testsystem config if you want to create more instances i.e testsystem3 and its settings and so forth

  

## For Azure you cannot use the guest layout yet. The task will only create one instance at a time.

  

## For aws please configure the aws cli with the access key and secret access key creds prior to running playbook and role. Also elastic ips must be created in AWS before and added into file in vars folder


Playbook calls role which then calls the main.yml (tasks folder) file to populate the file with values from the dictionary of the vars folder file. Can also be called main.yml. 

Then other ymls in the taskd folder containing aws in their names are run to build the vms



