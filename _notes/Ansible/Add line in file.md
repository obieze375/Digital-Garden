~~~~
  - name: Add a line to a file if it doesnt exist

    ansible.builtin.lineinfile:

      path: /tmp/example_file

      line: "This line must exist in the file"

      state: present
~~~~