~~~~
  - name: Copy and template the Nginx configuration file to the host

    ansible.builtin.template:

      src: templates/nginx.conf.j2

      dest: /etc/nginx/sites-available/default
~~~~     