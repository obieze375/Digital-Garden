
~~~~
  
  - name: Add a block of configuration options at the end of the file if it doesnt exist

    ansible.builtin.blockinfile:

      path: /etc/example_dictory/example.conf

      block: |

        feature1_enabled: true

        feature2_enabled: false

        feature2_enabled: true

      insertafter: EOF
~~~~