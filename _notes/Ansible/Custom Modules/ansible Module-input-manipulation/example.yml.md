[[Index]] 
```

---
- hosts: localhost
  gather_facts: False
  tasks:
  - name: "Get the area"
    foobar:
      length: 10
      breath: 8
      height: 9
      action: 'area'
    register: area_out

  - name: "Print the area "
    debug:
      msg: "{{ area_out.stdout }}"

  - name: "Get the volume"
    foobar:
      length: 10
      breath: 8
      height: 9
      action: 'volume'
    register: vol_out

  - name: "Print the volume"
    debug:
      msg: "{{ vol_out.stdout }}"
```