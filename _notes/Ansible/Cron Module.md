[[Index]] 

~~~~
  - name: Run daily DB backup script at 00:00

    ansible.builtin.cron:

      name: "Run daily DB backup script at 00:00"

      minute: "0"

      hour: "0"

      job: "/usr/local/bin/db_backup_script.sh > /var/log/db_backup_script.sh.log 2>&1"
  


~~~~