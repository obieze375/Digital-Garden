
[[Index]] 

## Rule of thumb: Mirror playbook structure to other playbooks in repo i.e to solve and issue take a look and see if other playbooks have are using something like a module that could help. Also use modules as much as possible for cleaner code creation

~~~~

---

- name: Ansible debug module in action

  hosts: all

  tasks:

          - name: Print system uptime

            shell: uptime -p

            register: system_uptime

          - name: Print uptime of managed node

            debug:

              msg: "{{ system_uptime }}"

  

---

- name: Ansible debug module in action

  hosts: all

  vars:

          greetings: Hello World!

          site: Linuxtechi

  tasks:

          - name: Print the value of a variable

            debug:

              msg: "{{ greetings }}, Welcome to {{ site }}."

  
  

---

- name: Ansible debug module in action

  hosts: all

  tasks:

          - name: Print a simple statement

            debug:

              msg: "Hello World! Welcome to Linuxtechi"

  
  
  
  

~~~~