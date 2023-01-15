
[[Index]] 

## Sample Ansible yum-playbook.yml

~~~~

---



-

  name: Install package(s) using yum

  hosts: centos

  become: yes

  tasks:

    - name: Install the latest version of Apache

      yum:

        name: httpd

        state: latest

  

    - name: Install apache >= 2.4

      yum:

        name: httpd>=2.4

        state: present

    - name: Install a list of packages (suitable replacement for 2.11 loop deprecation warning)

      yum:

        name: Install apache and postgresql

          - httpd

          - postgresql

          - postgresql-server

        state: present

~~~~