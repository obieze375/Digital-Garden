[[Index]] 


~~~~

  

tasks:

- name: ansible create multiple directory example

ansible.builtin.file:

     path: " {{ directory }} / {{ item }}"

     state: directory

     recurse: yes

with_items:

      - '/tmp/devops_system1'

      - '/tmp/devops_system2'

      - '/tmp/devops_system3'

when: "hostname in group_names" # Searches for hostname group in inventory file specified under group vars dir

~~~~